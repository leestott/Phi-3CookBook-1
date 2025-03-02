# **การปรับแต่ง Phi-3.5 ด้วย Intel OpenVINO**

Intel เป็นผู้ผลิต CPU ที่มีชื่อเสียงและมีฐานผู้ใช้จำนวนมาก ด้วยการเติบโตของการเรียนรู้ของเครื่อง (Machine Learning) และการเรียนรู้เชิงลึก (Deep Learning) Intel ได้เข้าร่วมแข่งขันในด้านการเร่งความเร็ว AI โดยสำหรับการประมวลผลโมเดล Intel ไม่ได้ใช้แค่ GPUs และ CPUs เท่านั้น แต่ยังใช้ NPUs ด้วย

เราหวังที่จะนำ Phi-3.x Family ไปใช้งานในอุปกรณ์ปลายทาง โดยมุ่งหวังให้เป็นส่วนสำคัญของ AI PC และ Copilot PC การโหลดโมเดลในอุปกรณ์ปลายทางขึ้นอยู่กับความร่วมมือของผู้ผลิตฮาร์ดแวร์ที่แตกต่างกัน บทนี้จะเน้นไปที่การใช้งาน Intel OpenVINO ในฐานะโมเดลเชิงปริมาณ (Quantized Model)

## **OpenVINO คืออะไร**

OpenVINO เป็นเครื่องมือโอเพ่นซอร์สสำหรับการปรับแต่งและการนำโมเดลการเรียนรู้เชิงลึกไปใช้งาน ตั้งแต่คลาวด์ไปจนถึงอุปกรณ์ปลายทาง มันช่วยเร่งการประมวลผลโมเดลการเรียนรู้เชิงลึกในหลายกรณี เช่น AI สร้างสรรค์ (Generative AI), วิดีโอ, เสียง และภาษา โดยใช้โมเดลจากเฟรมเวิร์คยอดนิยมอย่าง PyTorch, TensorFlow, ONNX และอื่น ๆ คุณสามารถแปลงและปรับแต่งโมเดล รวมถึงนำไปใช้งานในฮาร์ดแวร์และสภาพแวดล้อมของ Intel ได้ทั้งแบบ on-premises และ on-device, ในเบราว์เซอร์ หรือในคลาวด์

ด้วย OpenVINO คุณสามารถปรับแต่งโมเดล GenAI บนฮาร์ดแวร์ของ Intel ได้อย่างรวดเร็ว และเร่งการประมวลผลโมเดล

ปัจจุบัน OpenVINO รองรับการปรับแต่งเชิงปริมาณสำหรับ Phi-3.5-Vision และ Phi-3.5 Instruct

### **การตั้งค่าสภาพแวดล้อม**

โปรดตรวจสอบให้แน่ใจว่าได้ติดตั้ง dependencies ต่อไปนี้แล้ว นี่คือไฟล์ requirement.txt

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **การปรับแต่ง Phi-3.5-Instruct ด้วย OpenVINO**

ใน Terminal ให้รันสคริปต์นี้

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **การปรับแต่ง Phi-3.5-Vision ด้วย OpenVINO**

โปรดรันสคริปต์นี้ใน Python หรือ Jupyter Lab

```python

import requests
from pathlib import Path
from ov_phi3_vision import convert_phi3_model
import nncf

if not Path("ov_phi3_vision.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/notebooks/phi-3-vision/ov_phi3_vision.py")
    open("ov_phi3_vision.py", "w").write(r.text)


if not Path("gradio_helper.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/notebooks/phi-3-vision/gradio_helper.py")
    open("gradio_helper.py", "w").write(r.text)

if not Path("notebook_utils.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/utils/notebook_utils.py")
    open("notebook_utils.py", "w").write(r.text)



model_id = "microsoft/Phi-3.5-vision-instruct"
out_dir = Path("../model/phi-3.5-vision-128k-instruct-ov")
compression_configuration = {
    "mode": nncf.CompressWeightsMode.INT4_SYM,
    "group_size": 64,
    "ratio": 0.6,
}
if not out_dir.exists():
    convert_phi3_model(model_id, out_dir, compression_configuration)

```

### **🤖 ตัวอย่างการใช้งาน Phi-3.5 กับ Intel OpenVINO**

| Labs    | แนะนำ | ไปที่ |
| -------- | ------- |  ------- |
| 🚀 Lab-แนะนำ Phi-3.5 Instruct  | เรียนรู้วิธีการใช้ Phi-3.5 Instruct ใน AI PC ของคุณ    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-แนะนำ Phi-3.5 Vision (ภาพ) | เรียนรู้วิธีการใช้ Phi-3.5 Vision เพื่อวิเคราะห์ภาพใน AI PC ของคุณ      |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-แนะนำ Phi-3.5 Vision (วิดีโอ)   | เรียนรู้วิธีการใช้ Phi-3.5 Vision เพื่อวิเคราะห์วิดีโอใน AI PC ของคุณ    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |

## **แหล่งข้อมูล**

1. เรียนรู้เพิ่มเติมเกี่ยวกับ Intel OpenVINO [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub Repo [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติด้วย AI แม้ว่าเราจะพยายามให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นทางควรถือเป็นแหล่งข้อมูลที่ถูกต้องและเชื่อถือได้ที่สุด สำหรับข้อมูลที่สำคัญ ขอแนะนำให้ใช้บริการแปลภาษาจากผู้เชี่ยวชาญที่เป็นมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดที่เกิดจากการใช้การแปลนี้