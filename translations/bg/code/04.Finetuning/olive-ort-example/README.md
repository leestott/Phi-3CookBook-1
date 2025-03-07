# Фина настройка на Phi3 с помощта на Olive

В този пример ще използвате Olive, за да:

1. Фино настроите LoRA адаптер за класифициране на фрази в категории: Тъга, Радост, Страх, Изненада.
1. Сливате теглата на адаптера с базовия модел.
1. Оптимизирате и квантувате модела в `int4`.

Също така ще ви покажем как да правите предсказания с фино настроения модел, използвайки ONNX Runtime (ORT) Generate API.

> **⚠️ За фина настройка ще ви е необходим подходящ GPU - например, A10, V100, A100.**

## 💾 Инсталация

Създайте нова виртуална среда за Python (например, използвайки `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

След това инсталирайте Olive и зависимостите за работен процес на фина настройка:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Фина настройка на Phi3 с помощта на Olive

[Конфигурационният файл на Olive](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) съдържа *работен процес* със следните *стъпки*:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

На високо ниво този работен процес ще:

1. Фино настрои Phi3 (за 150 стъпки, които можете да промените) с помощта на данните от [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json).
1. Слее теглата на LoRA адаптера с базовия модел. Това ще ви даде един артефакт на модел във формат ONNX.
1. Model Builder ще оптимизира модела за ONNX runtime *и* ще го квантува в `int4`.

За да изпълните работния процес, стартирайте:

```bash
olive run --config phrase-classification.json
```

Когато Olive завърши, вашият оптимизиран `int4` фино настроен модел Phi3 ще бъде наличен тук: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 Интегриране на фино настроения Phi3 във вашето приложение

За да стартирате приложението:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

Отговорът трябва да бъде еднословна класификация на фразата (Тъга/Радост/Страх/Изненада).

**Отказ от отговорност**:  
Този документ е преведен с помощта на машинни AI услуги за превод. Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи може да съдържат грешки или неточности. Оригиналният документ на неговия оригинален език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален превод от човек. Не носим отговорност за никакви недоразумения или погрешни интерпретации, произтичащи от използването на този превод.