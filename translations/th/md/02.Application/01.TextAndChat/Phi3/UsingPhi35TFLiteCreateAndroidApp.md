# **การใช้ Microsoft Phi-3.5 tflite เพื่อสร้างแอป Android**

นี่คือตัวอย่างการใช้งาน Android ที่ใช้โมเดล Microsoft Phi-3.5 tflite

## **📚 ความรู้พื้นฐาน**

Android LLM Inference API ช่วยให้คุณสามารถรันโมเดลภาษาใหญ่ (LLMs) บนอุปกรณ์ Android ได้โดยสมบูรณ์ ซึ่งสามารถใช้ในการทำงานที่หลากหลาย เช่น การสร้างข้อความ การค้นหาข้อมูลในรูปแบบภาษาธรรมชาติ และการสรุปเอกสาร ฟีเจอร์นี้มีการสนับสนุนโมเดลภาษาใหญ่แบบข้อความต่อข้อความในตัว ทำให้คุณสามารถใช้โมเดล AI แบบสร้างสรรค์ล่าสุดบนอุปกรณ์ Android ของคุณได้

Googld AI Edge Torch เป็นไลบรารี Python ที่รองรับการแปลงโมเดล PyTorch ให้เป็นรูปแบบ .tflite ซึ่งสามารถรันได้ด้วย TensorFlow Lite และ MediaPipe สิ่งนี้ช่วยให้นำไปใช้งานใน Android, iOS และ IoT ที่สามารถรันโมเดลได้โดยสมบูรณ์บนอุปกรณ์ AI Edge Torch รองรับ CPU อย่างกว้างขวาง และมีการสนับสนุน GPU และ NPU ในเบื้องต้น AI Edge Torch มุ่งเน้นการผสานรวมกับ PyTorch โดยสร้างขึ้นบนพื้นฐานของ torch.export() และรองรับ Core ATen operators ได้ดี

## **🪬 แนวทาง**

### **🔥 การแปลง Microsoft Phi-3.5 ให้รองรับ tflite**

0. ตัวอย่างนี้ใช้สำหรับ Android 14+

1. ติดตั้ง Python 3.10.12

***คำแนะนำ:*** ใช้ conda ในการติดตั้งสภาพแวดล้อม Python ของคุณ

2. ใช้ Ubuntu 20.04 / 22.04 (โปรดโฟกัสที่ [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch))

***คำแนะนำ:*** ใช้ Azure Linux VM หรือ VM จากผู้ให้บริการคลาวด์รายอื่นเพื่อสร้างสภาพแวดล้อมของคุณ

3. ไปที่ bash ใน Linux ของคุณ แล้วติดตั้งไลบรารี Python 

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. ดาวน์โหลด Microsoft-3.5-Instruct จาก Hugging face

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. แปลง Microsoft Phi-3.5 ให้เป็น tflite

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 การแปลง Microsoft Phi-3.5 ให้เป็น Android Mediapipe Bundle**

โปรดติดตั้ง mediapipe ก่อน

```bash

pip install mediapipe

```

รันโค้ดนี้ใน [notebook ของคุณ](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb)

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

### **🔥 การใช้ adb push เพื่อส่งโมเดลไปยังเส้นทางในอุปกรณ์ Android ของคุณ**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 การรันโค้ด Android ของคุณ**

![demo](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.th.png)

**คำปฏิเสธความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาโดยปัญญาประดิษฐ์ แม้ว่าเราจะพยายามอย่างเต็มที่เพื่อความถูกต้อง แต่โปรดทราบว่าการแปลโดยระบบอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นทางควรถูกพิจารณาเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลภาษาจากผู้เชี่ยวชาญที่เป็นมนุษย์ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดพลาดที่เกิดขึ้นจากการใช้การแปลนี้