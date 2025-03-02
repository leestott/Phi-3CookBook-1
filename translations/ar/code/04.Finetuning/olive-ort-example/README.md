# ضبط Phi3 باستخدام Olive

في هذا المثال، ستستخدم Olive لـ:

1. ضبط LoRA adapter لتصنيف العبارات إلى حزن، فرح، خوف، مفاجأة.
2. دمج أوزان المحول (adapter) في النموذج الأساسي.
3. تحسين النموذج وضغطه إلى `int4`.

سنوضح لك أيضًا كيفية تنفيذ استدلال باستخدام النموذج المضبوط عبر واجهة Generate API الخاصة بـ ONNX Runtime (ORT).

> **⚠️ لضبط النموذج، ستحتاج إلى توفر GPU مناسب - مثل A10 أو V100 أو A100.**

## 💾 التثبيت

قم بإنشاء بيئة Python افتراضية جديدة (على سبيل المثال، باستخدام `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

بعد ذلك، قم بتثبيت Olive والمتطلبات اللازمة لعملية ضبط النموذج:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 ضبط Phi3 باستخدام Olive

ملف [تكوين Olive](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) يحتوي على *عملية* مع المراحل التالية:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

بشكل عام، هذه العملية ستقوم بـ:

1. ضبط Phi3 (لمدة 150 خطوة، ويمكنك تعديلها) باستخدام بيانات [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json).
2. دمج أوزان LoRA adapter في النموذج الأساسي. سيمنحك هذا ملف نموذج واحد بصيغة ONNX.
3. يقوم Model Builder بتحسين النموذج لتشغيله باستخدام ONNX runtime *وأيضًا* ضغط النموذج إلى `int4`.

لتنفيذ العملية، قم بتشغيل:

```bash
olive run --config phrase-classification.json
```

عند اكتمال Olive، سيكون نموذج Phi3 المضبوط والمحسن بصيغة `int4` متاحًا في: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 دمج Phi3 المضبوط في تطبيقك

لتشغيل التطبيق:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

يجب أن تكون الاستجابة تصنيفًا بكلمة واحدة للعبارة (حزن/فرح/خوف/مفاجأة).

**إخلاء المسؤولية**:  
تم ترجمة هذا المستند باستخدام خدمات ترجمة آلية تعتمد على الذكاء الاصطناعي. على الرغم من أننا نسعى لتحقيق الدقة، يرجى العلم بأن الترجمات الآلية قد تحتوي على أخطاء أو معلومات غير دقيقة. يجب اعتبار المستند الأصلي بلغته الأصلية هو المصدر الرسمي. للحصول على معلومات حاسمة، يُوصى باللجوء إلى ترجمة بشرية احترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسيرات خاطئة ناتجة عن استخدام هذه الترجمة.