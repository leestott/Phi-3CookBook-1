# ปรับแต่ง Phi3 ด้วย Olive

ในตัวอย่างนี้ คุณจะใช้ Olive เพื่อ:

1. ปรับแต่ง LoRA adapter เพื่อจำแนกวลีเป็น Sad, Joy, Fear, Surprise  
1. รวมค่า weights ของ adapter เข้ากับโมเดลพื้นฐาน  
1. ปรับแต่งและทำ Quantize โมเดลให้เป็น `int4`  

เรายังจะแสดงให้คุณเห็นวิธีการใช้ ONNX Runtime (ORT) Generate API เพื่อทำการ inference โมเดลที่ปรับแต่งแล้ว

> **⚠️ สำหรับการปรับแต่ง คุณจำเป็นต้องมี GPU ที่เหมาะสม เช่น A10, V100, A100**

## 💾 การติดตั้ง

สร้างสภาพแวดล้อม Python ใหม่ (ตัวอย่างเช่น โดยใช้ `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

ถัดไป ติดตั้ง Olive และ dependencies ที่จำเป็นสำหรับ workflow การปรับแต่ง:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 ปรับแต่ง Phi3 ด้วย Olive

[ไฟล์การตั้งค่า Olive](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json) ประกอบด้วย *workflow* ที่มี *passes* ดังนี้:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

ในภาพรวม workflow นี้จะ:

1. ปรับแต่ง Phi3 (เป็นเวลา 150 steps ซึ่งคุณสามารถปรับเปลี่ยนได้) โดยใช้ข้อมูลจาก [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json)  
1. รวมค่า weights ของ LoRA adapter เข้ากับโมเดลพื้นฐาน ซึ่งจะให้ผลลัพธ์เป็นไฟล์โมเดล ONNX เพียงไฟล์เดียว  
1. Model Builder จะปรับแต่งโมเดลให้เหมาะสมสำหรับ ONNX runtime *และ* ทำการ quantize โมเดลให้เป็น `int4`  

เพื่อเรียกใช้ workflow ให้รัน:

```bash
olive run --config phrase-classification.json
```

เมื่อ Olive เสร็จสิ้น คุณจะได้โมเดล Phi3 ที่ปรับแต่งและปรับแต่งเป็น `int4` ซึ่งอยู่ที่: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`

## 🧑‍💻 รวม Phi3 ที่ปรับแต่งแล้วเข้ากับแอปพลิเคชันของคุณ

เพื่อเรียกใช้งานแอป:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

ผลลัพธ์ที่ได้ควรเป็นคำตอบแบบคำเดียวที่จำแนกวลี (Sad/Joy/Fear/Surprise)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติที่ขับเคลื่อนด้วย AI แม้ว่าเราจะพยายามอย่างเต็มที่เพื่อความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางควรถูกพิจารณาให้เป็นแหล่งข้อมูลที่เชื่อถือได้ หากเป็นข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลภาษาจากผู้เชี่ยวชาญมืออาชีพ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดพลาดที่อาจเกิดขึ้นจากการใช้การแปลนี้