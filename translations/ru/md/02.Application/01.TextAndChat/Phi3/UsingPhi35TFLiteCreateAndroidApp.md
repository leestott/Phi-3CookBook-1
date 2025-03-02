# **Использование Microsoft Phi-3.5 tflite для создания Android-приложения**

Это пример Android-приложения, использующего модели Microsoft Phi-3.5 tflite.

## **📚 Знания**

API для выполнения LLM на Android позволяет запускать большие языковые модели (LLM) полностью на устройстве для Android-приложений. С его помощью можно выполнять широкий спектр задач, таких как генерация текста, поиск информации в форме естественного языка и создание кратких резюме документов. Этот инструмент предоставляет встроенную поддержку для нескольких моделей "текст-текст", что позволяет использовать самые современные генеративные AI-модели на Android.

Googld AI Edge Torch — это библиотека на Python, которая поддерживает преобразование моделей PyTorch в формат .tflite. Эти модели можно запускать с помощью TensorFlow Lite и MediaPipe, что позволяет создавать приложения для Android, iOS и IoT, которые работают полностью на устройстве. AI Edge Torch предлагает широкую поддержку процессоров (CPU), а также начальную поддержку GPU и NPU. Библиотека стремится к тесной интеграции с PyTorch, основываясь на torch.export() и обеспечивая хорошее покрытие Core ATen операторов.

## **🪬 Руководство**

### **🔥 Преобразование Microsoft Phi-3.5 в формат tflite**

0. Этот пример предназначен для Android 14+

1. Установите Python 3.10.12

***Рекомендация:*** используйте conda для установки среды Python

2. Ubuntu 20.04 / 22.04 (обратите внимание на [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch))

***Рекомендация:*** используйте Azure Linux VM или облачный сервер третьей стороны для создания среды

3. Перейдите в ваш Linux bash, чтобы установить библиотеку Python 

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Загрузите Microsoft-3.5-Instruct с Hugging Face

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. Преобразуйте Microsoft Phi-3.5 в формат tflite

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 Преобразование Microsoft Phi-3.5 в Android Mediapipe Bundle**

Сначала установите mediapipe

```bash

pip install mediapipe

```

Запустите этот код в [вашей записной книжке](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb)

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

### **🔥 Использование adb для отправки модели на ваше Android-устройство**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 Запуск вашего Android-кода**

![демо](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.ru.png)

**Отказ от ответственности**:  
Этот документ был переведен с использованием автоматизированных сервисов машинного перевода на основе ИИ. Несмотря на наши усилия обеспечить точность, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется обратиться к профессиональному переводу, выполненному человеком. Мы не несем ответственности за любые недоразумения или неверные интерпретации, возникающие в результате использования данного перевода.