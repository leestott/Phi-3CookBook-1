# ปรับแต่ง Phi3 ด้วย Olive

ในตัวอย่างนี้ คุณจะใช้ Olive เพื่อ:

1. ปรับแต่ง LoRA adapter เพื่อจัดประเภทวลีเป็น Sad, Joy, Fear, Surprise
2. รวมค่าถ่วงน้ำหนักของ adapter เข้ากับโมเดลพื้นฐาน
3. ปรับแต่งและลดขนาดโมเดลเป็น `int4`

เรายังจะแสดงให้คุณเห็นวิธีการใช้งานโมเดลที่ปรับแต่งแล้วด้วย ONNX Runtime (ORT) Generate API

> **⚠️ สำหรับการปรับแต่ง คุณจำเป็นต้องมี GPU ที่เหมาะสม เช่น A10, V100, A100**

## 💾 ติดตั้ง

สร้างสภาพแวดล้อมเสมือนของ Python ใหม่ (เช่น โดยใช้ `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

จากนั้นติดตั้ง Olive และ dependencies สำหรับ workflow การปรับแต่ง:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 ปรับแต่ง Phi3 ด้วย Olive
[ไฟล์การตั้งค่า Olive](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) มี *workflow* ที่มี *passes* ดังนี้:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

ในภาพรวม workflow นี้จะ:

1. ปรับแต่ง Phi3 (เป็นเวลา 150 ขั้นตอน ซึ่งคุณสามารถปรับเปลี่ยนได้) โดยใช้ข้อมูลจาก [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json)
2. รวมค่าถ่วงน้ำหนักของ LoRA adapter เข้ากับโมเดลพื้นฐาน ซึ่งจะได้อาร์ติแฟกต์โมเดลในรูปแบบ ONNX
3. Model Builder จะปรับแต่งโมเดลสำหรับ ONNX runtime *และ* ลดขนาดโมเดลเป็น `int4`

เพื่อรัน workflow ให้ใช้คำสั่ง:

```bash
olive run --config phrase-classification.json
```

เมื่อ Olive ทำงานเสร็จ คุณจะได้โมเดล Phi3 ที่ปรับแต่งและลดขนาดแล้วในรูปแบบ `int4` ซึ่งจะอยู่ใน: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`

## 🧑‍💻 ผสาน Phi3 ที่ปรับแต่งแล้วเข้ากับแอปพลิเคชันของคุณ

เพื่อรันแอป:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

ผลลัพธ์ควรเป็นการจัดประเภทวลีเพียงคำเดียว (Sad/Joy/Fear/Surprise)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติด้วย AI แม้ว่าเราจะพยายามอย่างเต็มที่เพื่อความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นฉบับควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลภาษามนุษย์ที่เป็นมืออาชีพ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดซึ่งเกิดจากการใช้การแปลนี้