# **การทำ Quantization Phi-3.5 ด้วย Apple MLX Framework**

MLX เป็นเฟรมเวิร์กสำหรับการวิจัยแมชชีนเลิร์นนิงที่พัฒนาขึ้นสำหรับอุปกรณ์ Apple Silicon โดยทีมวิจัยแมชชีนเลิร์นนิงของ Apple

MLX ถูกออกแบบโดยนักวิจัยแมชชีนเลิร์นนิงเพื่อให้นักวิจัยสามารถใช้งานได้ง่าย แต่ยังคงประสิทธิภาพสูงสำหรับการฝึกและการใช้งานโมเดล นอกจากนี้ การออกแบบของเฟรมเวิร์กยังมีความเรียบง่ายในเชิงแนวคิด เพื่อให้นักวิจัยสามารถขยายและปรับปรุง MLX ได้อย่างสะดวก ด้วยเป้าหมายในการทดลองไอเดียใหม่ ๆ ได้อย่างรวดเร็ว

LLM สามารถเร่งความเร็วได้ในอุปกรณ์ Apple Silicon ผ่าน MLX และยังสามารถรันโมเดลได้ในเครื่องอย่างสะดวกสบาย

ตอนนี้ Apple MLX Framework รองรับการแปลง Quantization ของ Phi-3.5-Instruct (**รองรับ Apple MLX Framework**), Phi-3.5-Vision (**รองรับ MLX-VLM Framework**) และ Phi-3.5-MoE (**รองรับ Apple MLX Framework**) ลองมาดูวิธีการใช้งานกัน:

### **Phi-3.5-Instruct**

```bash

python -m mlx_lm.convert --hf-path microsoft/Phi-3.5-mini-instruct -q

```

### **Phi-3.5-Vision**

```bash

python -m mlxv_lm.convert --hf-path microsoft/Phi-3.5-vision-instruct -q

```

### **Phi-3.5-MoE**

```bash

python -m mlx_lm.convert --hf-path microsoft/Phi-3.5-MoE-instruct  -q

```

### **🤖 ตัวอย่างการใช้งาน Phi-3.5 กับ Apple MLX**

| Labs    | แนะนำ | ลิงก์ |
| -------- | ------- |  ------- |
| 🚀 Lab-แนะนำ Phi-3.5 Instruct  | เรียนรู้วิธีการใช้ Phi-3.5 Instruct กับ Apple MLX Framework   |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 Lab-แนะนำ Phi-3.5 Vision (image) | เรียนรู้วิธีการใช้ Phi-3.5 Vision ในการวิเคราะห์ภาพด้วย Apple MLX Framework     |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 Lab-แนะนำ Phi-3.5 Vision (moE)   | เรียนรู้วิธีการใช้ Phi-3.5 MoE กับ Apple MLX Framework  |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **ทรัพยากร**

1. เรียนรู้เพิ่มเติมเกี่ยวกับ Apple MLX Framework [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub Repo [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub Repo [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาด้วย AI อัตโนมัติ แม้ว่าเราจะพยายามอย่างเต็มที่เพื่อให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้องเกิดขึ้น เอกสารต้นฉบับในภาษาต้นทางควรถูกพิจารณาเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลสำคัญ แนะนำให้ใช้บริการแปลภาษามนุษย์มืออาชีพ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดใด ๆ ที่เกิดจากการใช้การแปลนี้