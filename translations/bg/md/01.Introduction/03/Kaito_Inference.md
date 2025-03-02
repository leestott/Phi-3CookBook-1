## Изводи с Kaito

[Kaito](https://github.com/Azure/kaito) е оператор, който автоматизира внедряването на AI/ML модели за извеждане в Kubernetes клъстер.

Kaito има следните ключови предимства в сравнение с повечето от основните методологии за внедряване на модели, изградени върху инфраструктури с виртуални машини:

- Управлява файловете на моделите чрез контейнерни образи. Предоставя HTTP сървър за извършване на извеждащи заявки с помощта на библиотеката на модела.
- Избягва настройката на параметрите за внедряване спрямо хардуера на GPU, като предоставя предварително зададени конфигурации.
- Автоматично осигурява GPU възли според изискванията на модела.
- Хоства големи образи на модели в публичния Microsoft Container Registry (MCR), ако лицензът го позволява.

С Kaito работният процес по внедряване на големи AI модели за извеждане в Kubernetes е значително опростен.

## Архитектура

Kaito следва класическия дизайн модел на Kubernetes за Custom Resource Definition (CRD)/контролер. Потребителят управлява ресурс `workspace`, който описва изискванията за GPU и спецификацията за извеждане. Контролерите на Kaito автоматизират внедряването, като синхронизират ресурса `workspace`.
<div align="left">
  <img src="https://github.com/kaito-project/kaito/blob/main/docs/img/arch.png" width=80% title="Архитектура на Kaito" alt="Архитектура на Kaito">
</div>

Горната фигура представя общия преглед на архитектурата на Kaito. Основните му компоненти включват:

- **Контролер на работно пространство**: Синхронизира ресурса `workspace`, създава потребителски ресурси `machine` (обяснени по-долу) за задействане на автоматично осигуряване на възли и създава натоварване за извеждане (`deployment` или `statefulset`) въз основа на предварителните конфигурации на модела.
- **Контролер за осигуряване на възли**: Името на контролера е *gpu-provisioner* в [gpu-provisioner helm chart](https://github.com/Azure/gpu-provisioner/tree/main/charts/gpu-provisioner). Той използва CRD `machine`, произхождащ от [Karpenter](https://sigs.k8s.io/karpenter), за да взаимодейства с контролера на работното пространство. Интегрира се с API на Azure Kubernetes Service (AKS), за да добави нови GPU възли към AKS клъстера.
> Забележка: [*gpu-provisioner*](https://github.com/Azure/gpu-provisioner) е компонент с отворен код. Може да бъде заменен с други контролери, ако те поддържат API на [Karpenter-core](https://sigs.k8s.io/karpenter).

## Инсталация

Моля, вижте указанията за инсталация [тук](https://github.com/Azure/kaito/blob/main/docs/installation.md).

## Бърз старт за извеждане Phi-3
[Примерен код за извеждане Phi-3](https://github.com/Azure/kaito/tree/main/examples/inference)

```
apiVersion: kaito.sh/v1alpha1
kind: Workspace
metadata:
  name: workspace-phi-3-mini
resource:
  instanceType: "Standard_NC6s_v3"
  labelSelector:
    matchLabels:
      apps: phi-3
inference:
  preset:
    name: phi-3-mini-4k-instruct
    # Note: This configuration also works with the phi-3-mini-128k-instruct preset
```

```sh
$ cat examples/inference/kaito_workspace_phi_3.yaml

apiVersion: kaito.sh/v1alpha1
kind: Workspace
metadata:
  name: workspace-phi-3-mini
resource:
  instanceType: "Standard_NC6s_v3"
  labelSelector:
    matchLabels:
      app: phi-3-adapter
tuning:
  preset:
    name: phi-3-mini-4k-instruct
  method: qlora
  input:
    urls:
      - "https://huggingface.co/datasets/philschmid/dolly-15k-oai-style/resolve/main/data/train-00000-of-00001-54e3756291ca09c6.parquet?download=true"
  output:
    image: "ACR_REPO_HERE.azurecr.io/IMAGE_NAME_HERE:0.0.1" # Tuning Output ACR Path
    imagePushSecret: ACR_REGISTRY_SECRET_HERE
    

$ kubectl apply -f examples/inference/kaito_workspace_phi_3.yaml
```

Статусът на работното пространство може да бъде проследен чрез изпълнение на следната команда. Когато колоната WORKSPACEREADY стане `True`, моделът е успешно внедрен.

```sh
$ kubectl get workspace kaito_workspace_phi_3.yaml
NAME                  INSTANCE            RESOURCEREADY   INFERENCEREADY   WORKSPACEREADY   AGE
workspace-phi-3-mini   Standard_NC6s_v3   True            True             True             10m
```

След това може да се намери IP адресът на клъстерната услуга за извеждане и да се използва временен `curl` pod, за да се тества крайният точка на услугата в клъстера.

```sh
$ kubectl get svc workspace-phi-3-mini
NAME                  TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)            AGE
workspace-phi-3-mini-adapter  ClusterIP   <CLUSTERIP>  <none>        80/TCP,29500/TCP   10m

export CLUSTERIP=$(kubectl get svc workspace-phi-3-mini-adapter -o jsonpath="{.spec.clusterIPs[0]}") 
$ kubectl run -it --rm --restart=Never curl --image=curlimages/curl -- curl -X POST http://$CLUSTERIP/chat -H "accept: application/json" -H "Content-Type: application/json" -d "{\"prompt\":\"YOUR QUESTION HERE\"}"
```

## Бърз старт за извеждане Phi-3 с адаптери

След като инсталирате Kaito, можете да изпълните следните команди, за да стартирате услуга за извеждане.

[Примерен код за извеждане Phi-3 с адаптери](https://github.com/Azure/kaito/blob/main/examples/inference/kaito_workspace_phi_3_with_adapters.yaml)

```
apiVersion: kaito.sh/v1alpha1
kind: Workspace
metadata:
  name: workspace-phi-3-mini-adapter
resource:
  instanceType: "Standard_NC6s_v3"
  labelSelector:
    matchLabels:
      apps: phi-3-adapter
inference:
  preset:
    name: phi-3-mini-128k-instruct
  adapters:
    - source:
        name: "phi-3-adapter"
        image: "ACR_REPO_HERE.azurecr.io/ADAPTER_HERE:0.0.1"
      strength: "1.0"
```

```sh
$ cat examples/inference/kaito_workspace_phi_3_with_adapters.yaml

apiVersion: kaito.sh/v1alpha1
kind: Workspace
metadata:
  name: workspace-phi-3-mini-adapter
resource:
  instanceType: "Standard_NC6s_v3"
  labelSelector:
    matchLabels:
      app: phi-3-adapter
tuning:
  preset:
    name: phi-3-mini-128k-instruct
  method: qlora
  input:
    urls:
      - "https://huggingface.co/datasets/philschmid/dolly-15k-oai-style/resolve/main/data/train-00000-of-00001-54e3756291ca09c6.parquet?download=true"
  output:
    image: "ACR_REPO_HERE.azurecr.io/IMAGE_NAME_HERE:0.0.1" # Tuning Output ACR Path
    imagePushSecret: ACR_REGISTRY_SECRET_HERE
    

$ kubectl apply -f examples/inference/kaito_workspace_phi_3_with_adapters.yaml
```

Статусът на работното пространство може да бъде проследен чрез изпълнение на следната команда. Когато колоната WORKSPACEREADY стане `True`, моделът е успешно внедрен.

```sh
$ kubectl get workspace kaito_workspace_phi_3_with_adapters.yaml
NAME                  INSTANCE            RESOURCEREADY   INFERENCEREADY   WORKSPACEREADY   AGE
workspace-phi-3-mini-adapter   Standard_NC6s_v3   True            True             True             10m
```

След това може да се намери IP адресът на клъстерната услуга за извеждане и да се използва временен `curl` pod, за да се тества крайният точка на услугата в клъстера.

```sh
$ kubectl get svc workspace-phi-3-mini-adapter
NAME                  TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)            AGE
workspace-phi-3-mini-adapter  ClusterIP   <CLUSTERIP>  <none>        80/TCP,29500/TCP   10m

export CLUSTERIP=$(kubectl get svc workspace-phi-3-mini-adapter -o jsonpath="{.spec.clusterIPs[0]}") 
$ kubectl run -it --rm --restart=Never curl --image=curlimages/curl -- curl -X POST http://$CLUSTERIP/chat -H "accept: application/json" -H "Content-Type: application/json" -d "{\"prompt\":\"YOUR QUESTION HERE\"}"
```

**Отказ от отговорност**:  
Този документ е преведен с помощта на услуги за машинен превод, базирани на изкуствен интелект. Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи може да съдържат грешки или неточности. Оригиналният документ на неговия оригинален език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален превод от човек. Ние не носим отговорност за каквито и да е недоразумения или погрешни интерпретации, произтичащи от използването на този превод.