# ضبط Phi3 باستخدام Olive

في هذا المثال ستستخدم Olive للقيام بما يلي:

1. ضبط محول LoRA لتصنيف العبارات إلى حزن، فرح، خوف، مفاجأة.
2. دمج أوزان المحول في النموذج الأساسي.
3. تحسين النموذج وتكميمه إلى `int4`.

سنوضح لك أيضًا كيفية استخدام نموذج ضبط الأداء للتنبؤ باستخدام واجهة برمجة التطبيقات Generate الخاصة بـ ONNX Runtime (ORT).

> **⚠️ لضبط الأداء، ستحتاج إلى وجود وحدة معالجة رسومات (GPU) مناسبة - مثل A10، V100، A100.**

## 💾 التثبيت

قم بإنشاء بيئة افتراضية جديدة لـ Python (على سبيل المثال، باستخدام `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

بعد ذلك، قم بتثبيت Olive ومتطلبات سير العمل لضبط الأداء:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 ضبط Phi3 باستخدام Olive

يحتوي [ملف إعداد Olive](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json) على *سير عمل* مع *خطوات* تشمل ما يلي:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

بصورة عامة، يقوم هذا سير العمل بما يلي:

1. ضبط Phi3 (لمدة 150 خطوة، يمكنك تعديل ذلك) باستخدام بيانات [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json).
2. دمج أوزان محول LoRA في النموذج الأساسي. ستحصل على ملف نموذج واحد بصيغة ONNX.
3. يقوم Model Builder بتحسين النموذج لـ ONNX Runtime *وأيضًا* تكميم النموذج إلى `int4`.

لتنفيذ سير العمل، قم بتشغيل:

```bash
olive run --config phrase-classification.json
```

عند انتهاء Olive، سيكون لديك نموذج Phi3 مضبوط ومحسن بـ `int4` في المسار: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 دمج Phi3 المضبوط في تطبيقك

لتشغيل التطبيق:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

يجب أن تكون الاستجابة كلمة واحدة تصنف العبارة (حزن/فرح/خوف/مفاجأة).

**إخلاء المسؤولية**:  
تم ترجمة هذا المستند باستخدام خدمات ترجمة آلية تعتمد على الذكاء الاصطناعي. بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو معلومات غير دقيقة. يجب اعتبار المستند الأصلي بلغته الأصلية هو المصدر الموثوق. للحصول على معلومات حساسة أو مهمة، يُوصى بالاستعانة بترجمة بشرية احترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ينشأ عن استخدام هذه الترجمة.