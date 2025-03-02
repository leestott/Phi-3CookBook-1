# **ایپل MLX فریم ورک کا استعمال کرتے ہوئے Phi-3.5 کو کوانٹائز کرنا**

MLX ایپل سلیکون پر مشین لرننگ ریسرچ کے لیے ایک ایریے فریم ورک ہے، جو ایپل مشین لرننگ ریسرچ کی طرف سے پیش کیا گیا ہے۔

MLX مشین لرننگ ریسرچرز کے لیے مشین لرننگ ریسرچرز کے ذریعے ڈیزائن کیا گیا ہے۔ یہ فریم ورک صارف دوست ہونے کے ساتھ ساتھ ماڈلز کو ٹرین اور ڈیپلائے کرنے کے لیے مؤثر بھی ہے۔ فریم ورک کا ڈیزائن خود بھی تصوراتی طور پر سادہ ہے۔ ہمارا مقصد یہ ہے کہ محققین کے لیے MLX کو بہتر اور توسیع دینا آسان ہو، تاکہ نئے خیالات کو تیزی سے دریافت کیا جا سکے۔

Apple Silicon ڈیوائسز میں LLMs کو MLX کے ذریعے تیز کیا جا سکتا ہے، اور ماڈلز کو مقامی طور پر بہت آسانی سے چلایا جا سکتا ہے۔

اب Apple MLX Framework Phi-3.5-Instruct(**Apple MLX Framework support**)، Phi-3.5-Vision(**MLX-VLM Framework support**) اور Phi-3.5-MoE(**Apple MLX Framework support**) کے کوانٹائزیشن کنورژن کو سپورٹ کرتا ہے۔ آئیے اسے آزمائیں:

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

### **🤖 Apple MLX کے ساتھ Phi-3.5 کے نمونے**

| لیبز    | تعارف | جاؤ |
| -------- | ------- |  ------- |
| 🚀 لیب - Phi-3.5 Instruct کا تعارف  | سیکھیں کہ Apple MLX فریم ورک کے ساتھ Phi-3.5 Instruct کو کیسے استعمال کریں   |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 لیب - Phi-3.5 Vision (تصویر) کا تعارف | سیکھیں کہ Apple MLX فریم ورک کے ساتھ تصویر کا تجزیہ کرنے کے لیے Phi-3.5 Vision کو کیسے استعمال کریں     |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 لیب - Phi-3.5 Vision (moE) کا تعارف   | سیکھیں کہ Apple MLX فریم ورک کے ساتھ Phi-3.5 MoE کو کیسے استعمال کریں  |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **وسائل**

1. Apple MLX Framework کے بارے میں جانیں [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub ریپوزیٹری [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub ریپوزیٹری [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**ڈسکلیمر**:  
یہ دستاویز مشین پر مبنی AI ترجمہ خدمات کا استعمال کرتے ہوئے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کی پوری کوشش کرتے ہیں، براہ کرم نوٹ کریں کہ خودکار ترجمے میں غلطیاں یا خامیاں ہو سکتی ہیں۔ اصل دستاویز کو اس کی اصل زبان میں مستند ذریعہ سمجھا جانا چاہیے۔ اہم معلومات کے لیے، پیشہ ور انسانی ترجمے کی سفارش کی جاتی ہے۔ اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے لیے ہم ذمہ دار نہیں ہیں۔