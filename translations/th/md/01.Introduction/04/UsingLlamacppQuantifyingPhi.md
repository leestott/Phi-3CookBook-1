# **การควอนไทซ์ตระกูล Phi ด้วย llama.cpp**

## **llama.cpp คืออะไร**

llama.cpp เป็นไลบรารีซอฟต์แวร์แบบโอเพ่นซอร์สที่เขียนด้วยภาษา C++ เป็นหลัก ใช้สำหรับการทำอินเฟอเรนซ์บนโมเดลภาษาขนาดใหญ่ (LLMs) ต่าง ๆ เช่น Llama โดยมีเป้าหมายหลักเพื่อให้ได้ประสิทธิภาพระดับสูงสุดสำหรับการทำอินเฟอเรนซ์ LLM บนอุปกรณ์ฮาร์ดแวร์หลากหลายประเภท โดยมีการตั้งค่าเพียงเล็กน้อย นอกจากนี้ยังมี Python bindings สำหรับไลบรารีนี้ ซึ่งช่วยให้ใช้งาน API ระดับสูงสำหรับการเติมข้อความและเซิร์ฟเวอร์เว็บที่เข้ากันได้กับ OpenAI

เป้าหมายหลักของ llama.cpp คือการทำให้การอินเฟอเรนซ์ LLM เป็นเรื่องง่ายและมีประสิทธิภาพสูงสุดบนฮาร์ดแวร์หลากหลายประเภท ทั้งในเครื่องและในคลาวด์

- การพัฒนาด้วยภาษา C/C++ ล้วน ๆ โดยไม่มีการพึ่งพาไลบรารีอื่น
- รองรับ Apple Silicon เป็นอย่างดี โดยปรับแต่งผ่าน ARM NEON, Accelerate และ Metal frameworks
- รองรับ AVX, AVX2 และ AVX512 สำหรับสถาปัตยกรรม x86
- การควอนไทซ์ตัวเลขแบบ 1.5-bit, 2-bit, 3-bit, 4-bit, 5-bit, 6-bit และ 8-bit เพื่อการอินเฟอเรนซ์ที่เร็วขึ้นและการใช้หน่วยความจำที่ลดลง
- รองรับ Custom CUDA kernels สำหรับการรัน LLM บน GPU ของ NVIDIA (และรองรับ GPU ของ AMD ผ่าน HIP)
- รองรับ backend แบบ Vulkan และ SYCL
- การอินเฟอเรนซ์แบบผสม CPU+GPU เพื่อเร่งความเร็วสำหรับโมเดลที่มีขนาดใหญ่กว่าความจุ VRAM รวม

## **การควอนไทซ์ Phi-3.5 ด้วย llama.cpp**

โมเดล Phi-3.5-Instruct สามารถควอนไทซ์ด้วย llama.cpp ได้ แต่ Phi-3.5-Vision และ Phi-3.5-MoE ยังไม่รองรับ รูปแบบที่ llama.cpp แปลงคือ gguf ซึ่งเป็นรูปแบบควอนไทซ์ที่ใช้กันอย่างแพร่หลายที่สุดในปัจจุบัน

มีโมเดลในรูปแบบ GGUF ที่ถูกควอนไทซ์แล้วจำนวนมากบน Hugging Face โดย AI Foundry, Ollama และ LlamaEdge ต่างก็ใช้ llama.cpp ดังนั้นโมเดล GGUF จึงถูกใช้งานบ่อยครั้ง

### **GGUF คืออะไร**

GGUF เป็นรูปแบบไบนารีที่ถูกปรับแต่งให้โหลดและบันทึกโมเดลได้อย่างรวดเร็ว ทำให้มีประสิทธิภาพสูงสำหรับการใช้งานอินเฟอเรนซ์ GGUF ถูกออกแบบมาเพื่อใช้กับ GGML และ executor อื่น ๆ โดย GGUF ถูกพัฒนาโดย @ggerganov ซึ่งเป็นผู้พัฒนา llama.cpp ซึ่งเป็นเฟรมเวิร์กสำหรับการอินเฟอเรนซ์ LLM ที่ได้รับความนิยม โมเดลที่พัฒนาด้วยเฟรมเวิร์กอย่าง PyTorch สามารถแปลงเป็นรูปแบบ GGUF เพื่อใช้งานกับเอนจินเหล่านี้ได้

### **ONNX vs GGUF**

ONNX เป็นรูปแบบที่ใช้ในงานแมชชีนเลิร์นนิง/ดีพเลิร์นนิงแบบดั้งเดิม ซึ่งได้รับการสนับสนุนอย่างดีในเฟรมเวิร์ก AI ต่าง ๆ และเหมาะสำหรับการใช้งานในอุปกรณ์เอดจ์ ในขณะที่ GGUF ถูกพัฒนาขึ้นบนพื้นฐานของ llama.cpp และสามารถกล่าวได้ว่าเป็นผลิตภัณฑ์ในยุค GenAI การใช้งานของทั้งสองมีความคล้ายคลึงกัน หากคุณต้องการประสิทธิภาพที่ดีกว่าในฮาร์ดแวร์แบบฝังตัวและชั้นแอปพลิเคชัน ONNX อาจเป็นตัวเลือกของคุณ แต่หากคุณใช้เฟรมเวิร์กและเทคโนโลยีที่ต่อยอดจาก llama.cpp GGUF อาจเหมาะสมกว่า

### **การควอนไทซ์ Phi-3.5-Instruct ด้วย llama.cpp**

**1. การตั้งค่าสภาพแวดล้อม**

```bash

git clone https://github.com/ggerganov/llama.cpp.git

cd llama.cpp

make -j8

```

**2. การควอนไทซ์**

ใช้ llama.cpp เพื่อแปลง Phi-3.5-Instruct เป็น FP16 GGUF

```bash

./convert_hf_to_gguf.py <Your Phi-3.5-Instruct Location> --outfile phi-3.5-128k-mini_fp16.gguf

```

ควอนไทซ์ Phi-3.5 เป็น INT4

```bash

./llama.cpp/llama-quantize <Your phi-3.5-128k-mini_fp16.gguf location> ./gguf/phi-3.5-128k-mini_Q4_K_M.gguf Q4_K_M

```

**3. การทดสอบ**

ติดตั้ง llama-cpp-python

```bash

pip install llama-cpp-python -U

```

***หมายเหตุ***

หากคุณใช้ Apple Silicon ให้ติดตั้ง llama-cpp-python ด้วยวิธีนี้

```bash

CMAKE_ARGS="-DLLAMA_METAL=on" pip install llama-cpp-python -U

```

การทดสอบ

```bash

llama.cpp/llama-cli --model <Your phi-3.5-128k-mini_Q4_K_M.gguf location> --prompt "<|user|>\nCan you introduce .NET<|end|>\n<|assistant|>\n"  --gpu-layers 10

```

## **ทรัพยากรเพิ่มเติม**

1. เรียนรู้เพิ่มเติมเกี่ยวกับ llama.cpp [https://onnxruntime.ai/docs/genai/](https://onnxruntime.ai/docs/genai/)

2. เรียนรู้เพิ่มเติมเกี่ยวกับ GGUF [https://huggingface.co/docs/hub/en/gguf](https://huggingface.co/docs/hub/en/gguf)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติด้วย AI แม้ว่าเราจะพยายามอย่างเต็มที่เพื่อให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางควรถูกพิจารณาว่าเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่มีความสำคัญ แนะนำให้ใช้บริการแปลภาษาจากผู้เชี่ยวชาญที่เป็นมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดอันเกิดจากการใช้การแปลนี้