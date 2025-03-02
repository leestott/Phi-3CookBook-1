# **ਮਾਈਕਰੋਸਾਫਟ Phi-3.5 tflite ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਐਂਡਰਾਇਡ ਐਪ ਬਣਾਉਣਾ**

ਇਹ ਮਾਈਕਰੋਸਾਫਟ Phi-3.5 tflite ਮਾਡਲਾਂ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋਏ ਇੱਕ ਐਂਡਰਾਇਡ ਸੈਂਪਲ ਹੈ।

## **📚 ਗਿਆਨ**

ਐਂਡਰਾਇਡ LLM ਇੰਫਰੈਂਸ API ਤੁਹਾਨੂੰ ਐਂਡਰਾਇਡ ਐਪਲੀਕੇਸ਼ਨ ਲਈ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲ (LLMs) ਨੂੰ ਪੂਰੀ ਤਰ੍ਹਾਂ ਡਿਵਾਈਸ 'ਤੇ ਚਲਾਉਣ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ। ਇਸ ਨਾਲ ਤੁਸੀਂ ਵੱਖ-ਵੱਖ ਕੰਮ ਕਰ ਸਕਦੇ ਹੋ, ਜਿਵੇਂ ਕਿ ਟੈਕਸਟ ਜਨਰੇਟ ਕਰਨਾ, ਕੁਦਰਤੀ ਭਾਸ਼ਾ ਰੂਪ ਵਿੱਚ ਜਾਣਕਾਰੀ ਪ੍ਰਾਪਤ ਕਰਨਾ ਅਤੇ ਦਸਤਾਵੇਜ਼ਾਂ ਦਾ ਸਾਰ ਲਿਖਣਾ। ਇਹ ਟਾਸਕ ਕਈ ਟੈਕਸਟ-ਟੂ-ਟੈਕਸਟ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲਾਂ ਲਈ ਬਿਲਟ-ਇਨ ਸਪੋਰਟ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ, ਤਾਂ ਜੋ ਤੁਸੀਂ ਆਪਣੇ ਐਂਡਰਾਇਡ ਐਪਸ ਲਈ ਤਾਜ਼ਾ ਜਨਰੇਟਿਵ AI ਮਾਡਲਾਂ ਨੂੰ ਲਾਗੂ ਕਰ ਸਕੋ।

ਗੂਗਲ AI Edge Torch ਇੱਕ ਪਾਇਥਨ ਲਾਇਬ੍ਰੇਰੀ ਹੈ ਜੋ PyTorch ਮਾਡਲਾਂ ਨੂੰ .tflite ਫਾਰਮੈਟ ਵਿੱਚ ਕਨਵਰਟ ਕਰਨ ਲਈ ਸਹਾਇਤਾ ਕਰਦੀ ਹੈ। ਇਹ ਮਾਡਲ ਫਿਰ TensorFlow Lite ਅਤੇ MediaPipe ਨਾਲ ਚਲ ਸਕਦੇ ਹਨ। ਇਹ ਐਂਡਰਾਇਡ, iOS ਅਤੇ IoT ਲਈ ਐਪਲੀਕੇਸ਼ਨਾਂ ਨੂੰ ਸਮਰਥਨ ਦਿੰਦਾ ਹੈ ਜੋ ਪੂਰੀ ਤਰ੍ਹਾਂ ਡਿਵਾਈਸ 'ਤੇ ਮਾਡਲ ਚਲਾ ਸਕਦੇ ਹਨ। AI Edge Torch ਵਿਸਤ੍ਰਿਤ CPU ਕਵਰੇਜ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ, ਜਿਸ ਵਿੱਚ ਸ਼ੁਰੂਆਤੀ GPU ਅਤੇ NPU ਸਪੋਰਟ ਸ਼ਾਮਲ ਹੈ। AI Edge Torch PyTorch ਨਾਲ ਨਜ਼ਦੀਕੀ ਇਕੀਕਰਨ ਦਾ ਉਦੇਸ਼ ਰੱਖਦਾ ਹੈ, torch.export() 'ਤੇ ਅਧਾਰਿਤ ਹੈ ਅਤੇ Core ATen ਆਪਰੇਟਰਾਂ ਦੀ ਚੰਗੀ ਕਵਰੇਜ ਦਿੰਦਾ ਹੈ।

## **🪬 ਮਾਰਗਦਰਸ਼ਨ**

### **🔥 ਮਾਈਕਰੋਸਾਫਟ Phi-3.5 ਨੂੰ tflite ਸਪੋਰਟ ਵਿੱਚ ਕਨਵਰਟ ਕਰੋ**

0. ਇਹ ਸੈਂਪਲ ਐਂਡਰਾਇਡ 14+ ਲਈ ਹੈ।

1. Python 3.10.12 ਇੰਸਟਾਲ ਕਰੋ

***ਸੁਝਾਅ:*** ਆਪਣੇ ਪਾਇਥਨ ਐਨਵਾਇਰਨਮੈਂਟ ਲਈ conda ਦੀ ਵਰਤੋਂ ਕਰੋ

2. Ubuntu 20.04 / 22.04 (ਕਿਰਪਾ ਕਰਕੇ [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch) 'ਤੇ ਧਿਆਨ ਦੇਵੋ)

***ਸੁਝਾਅ:*** ਆਪਣੇ ਐਨਵਾਇਰਨਮੈਂਟ ਨੂੰ ਬਣਾਉਣ ਲਈ Azure Linux VM ਜਾਂ 3rd party ਕਲਾਉਡ VM ਦੀ ਵਰਤੋਂ ਕਰੋ

3. ਆਪਣੇ Linux bash 'ਤੇ ਜਾਓ, Python ਲਾਇਬ੍ਰੇਰੀ ਇੰਸਟਾਲ ਕਰਨ ਲਈ

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Hugging Face ਤੋਂ Microsoft-3.5-Instruct ਡਾਊਨਲੋਡ ਕਰੋ

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. ਮਾਈਕਰੋਸਾਫਟ Phi-3.5 ਨੂੰ tflite ਵਿੱਚ ਕਨਵਰਟ ਕਰੋ

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 ਮਾਈਕਰੋਸਾਫਟ Phi-3.5 ਨੂੰ ਐਂਡਰਾਇਡ Mediapipe ਬੰਡਲ ਵਿੱਚ ਕਨਵਰਟ ਕਰੋ**

ਕਿਰਪਾ ਕਰਕੇ ਪਹਿਲਾਂ mediapipe ਇੰਸਟਾਲ ਕਰੋ

```bash

pip install mediapipe

```

ਇਹ ਕੋਡ ਆਪਣੇ [ਨੋਟਬੁੱਕ](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb) ਵਿੱਚ ਚਲਾਓ

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

### **🔥 ਆਪਣੇ ਐਂਡਰਾਇਡ ਡਿਵਾਈਸ ਦੇ ਪਾਥ ਵਿੱਚ ਮਾਡਲ ਨੂੰ adb push ਕਰਨਾ**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 ਆਪਣਾ ਐਂਡਰਾਇਡ ਕੋਡ ਚਲਾਉਣਾ**

![ਡੈਮੋ](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.pa.png)

**ਅਸਵੀਕਰਤੀ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ-ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦਿਤ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਵਿੱਚ ਰੱਖੋ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਚੱਜੇ ਪੱਖ ਹੋ ਸਕਦੇ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਨੂੰ ਉਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੇ ਕਿਸੇ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।