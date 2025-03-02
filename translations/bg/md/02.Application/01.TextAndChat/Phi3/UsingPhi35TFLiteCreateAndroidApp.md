# **Използване на Microsoft Phi-3.5 tflite за създаване на Android приложение**

Това е пример за Android приложение, което използва моделите Microsoft Phi-3.5 tflite.

## **📚 Знания**

Android LLM Inference API ви позволява да стартирате големи езикови модели (LLMs) изцяло на устройството за Android приложения. Можете да ги използвате за изпълнение на широк спектър от задачи, като генериране на текст, извличане на информация в естествен езиков формат и обобщаване на документи. API предоставя вградена поддръжка за множество текст-към-текст големи езикови модели, което ви позволява да прилагате най-новите генеративни AI модели на устройството във вашите Android приложения.

Googld AI Edge Torch е Python библиотека, която поддържа конвертиране на PyTorch модели във формат .tflite, който след това може да се стартира с TensorFlow Lite и MediaPipe. Това позволява създаването на приложения за Android, iOS и IoT, които могат да изпълняват модели изцяло на устройството. AI Edge Torch предлага широка поддръжка за CPU, с начална поддръжка за GPU и NPU. AI Edge Torch се стреми към тясна интеграция с PyTorch, като се основава на torch.export() и осигурява добра съвместимост с основните ATen оператори.

## **🪬 Насоки**

### **🔥 Конвертиране на Microsoft Phi-3.5 към tflite**

0. Този пример е за Android 14+

1. Инсталирайте Python 3.10.12

***Препоръка:*** използвайте conda за инсталиране на вашата Python среда

2. Ubuntu 20.04 / 22.04 (моля, обърнете внимание на [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch))

***Препоръка:*** Използвайте Azure Linux VM или облачен VM от трета страна за създаване на вашата среда

3. Отворете вашия Linux bash и инсталирайте Python библиотеката 

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Изтеглете Microsoft-3.5-Instruct от Hugging face


```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. Конвертирайте Microsoft Phi-3.5 към tflite


```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```


### **🔥 Конвертиране на Microsoft Phi-3.5 към Android Mediapipe Bundle**

Първо инсталирайте mediapipe

```bash

pip install mediapipe

```

Стартирайте този код в [вашия notebook](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb)



```python

import mediapipe as mp
from mediapipe.tasks.python.genai import bundler

config = bundler.BundleConfig(
    tflite_model='Your Phi-3.5 tflite model path',
    tokenizer_model='Your Phi-3.5 tokenizer model path',
    start_token='start_token',
    stop_tokens=[STOP_TOKENS],
    output_filename='Your Phi-3.5 task model path',
    enable_bytes_to_unicode_mapping=True or Flase,
)
bundler.create_bundle(config)

```


### **🔥 Използване на adb push за качване на модела на вашето Android устройство**


```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 Стартиране на вашия Android код**

![демо](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.bg.png)

**Отказ от отговорност**:  
Този документ е преведен с помощта на автоматизирани AI услуги за превод. Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи може да съдържат грешки или неточности. Оригиналният документ на неговия оригинален език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Не носим отговорност за каквито и да било недоразумения или погрешни интерпретации, произтичащи от използването на този превод.