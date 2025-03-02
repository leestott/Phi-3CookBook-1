# **تكميم Phi-3.5 باستخدام إطار عمل Apple MLX**

MLX هو إطار عمل مخصص للبحث في تعلم الآلة على أجهزة Apple Silicon، مقدم من فريق أبحاث تعلم الآلة في Apple.

تم تصميم MLX من قبل باحثين في تعلم الآلة ليكون مخصصًا لباحثي تعلم الآلة. الإطار مصمم ليكون سهل الاستخدام وفي نفس الوقت فعالًا في تدريب النماذج ونشرها. تصميم الإطار نفسه بسيط من الناحية المفاهيمية، مما يهدف إلى تسهيل توسيع وتحسين MLX من قبل الباحثين لاستكشاف أفكار جديدة بسرعة.

يمكن تسريع النماذج اللغوية الكبيرة (LLMs) على أجهزة Apple Silicon باستخدام MLX، ويمكن تشغيل النماذج محليًا بكل سهولة.

يدعم الآن إطار عمل Apple MLX تحويل التكميم لنماذج Phi-3.5-Instruct (**بدعم من إطار عمل Apple MLX**)، Phi-3.5-Vision (**بدعم من إطار عمل MLX-VLM**)، وPhi-3.5-MoE (**بدعم من إطار عمل Apple MLX**). دعونا نجرب ذلك:

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

### **🤖 أمثلة على Phi-3.5 باستخدام Apple MLX**

| المعامل    | الوصف | الانتقال |
| -------- | ------- |  ------- |
| 🚀 معمل - مقدمة عن Phi-3.5 Instruct  | تعلم كيفية استخدام Phi-3.5 Instruct مع إطار عمل Apple MLX   |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 معمل - مقدمة عن Phi-3.5 Vision (صور) | تعلم كيفية استخدام Phi-3.5 Vision لتحليل الصور باستخدام إطار عمل Apple MLX     |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 معمل - مقدمة عن Phi-3.5 Vision (MoE)   | تعلم كيفية استخدام Phi-3.5 MoE مع إطار عمل Apple MLX  |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **المصادر**

1. تعرف على إطار عمل Apple MLX [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. مستودع GitHub الخاص بـ Apple MLX [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. مستودع GitHub الخاص بـ MLX-VLM [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**إخلاء المسؤولية**:  
تم ترجمة هذا المستند باستخدام خدمات الترجمة الآلية المعتمدة على الذكاء الاصطناعي. بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو معلومات غير دقيقة. يجب اعتبار المستند الأصلي بلغته الأصلية هو المصدر الرسمي والموثوق. للحصول على معلومات حساسة أو هامة، يُوصى بالاستعانة بترجمة بشرية احترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسيرات خاطئة تنشأ عن استخدام هذه الترجمة.