# تنظیم Phi3 با استفاده از Olive

در این مثال، شما با استفاده از Olive:

1. یک آداپتور LoRA را برای دسته‌بندی عبارات به غم، شادی، ترس و شگفتی تنظیم می‌کنید.
1. وزن‌های آداپتور را با مدل پایه ادغام می‌کنید.
1. مدل را به `int4` بهینه و کوانتایز می‌کنید.

همچنین به شما نشان خواهیم داد که چگونه می‌توانید با استفاده از API تولید ONNX Runtime (ORT)، از مدل تنظیم‌شده استفاده کنید.

> **⚠️ برای تنظیم مدل، نیاز به یک GPU مناسب دارید - برای مثال، A10، V100، A100.**

## 💾 نصب

یک محیط مجازی پایتون جدید ایجاد کنید (برای مثال، با استفاده از `conda`):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

سپس، Olive و وابستگی‌های مورد نیاز برای فرآیند تنظیم را نصب کنید:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 تنظیم Phi3 با استفاده از Olive

[فایل پیکربندی Olive](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json) شامل یک *workflow* با *passes* زیر است:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

در یک نگاه کلی، این workflow:

1. Phi3 را (برای 150 مرحله که می‌توانید تغییر دهید) با استفاده از داده‌های [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json) تنظیم می‌کند.
1. وزن‌های آداپتور LoRA را با مدل پایه ادغام می‌کند. این کار یک خروجی مدل در قالب ONNX به شما می‌دهد.
1. Model Builder مدل را برای ONNX runtime بهینه کرده و آن را به `int4` کوانتایز می‌کند.

برای اجرای workflow، دستور زیر را اجرا کنید:

```bash
olive run --config phrase-classification.json
```

پس از اتمام فرآیند توسط Olive، مدل Phi3 تنظیم‌شده و بهینه‌شده `int4` شما در مسیر زیر موجود است:  
`code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 ادغام Phi3 تنظیم‌شده در برنامه شما

برای اجرای برنامه:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

پاسخ باید یک کلمه باشد که دسته‌بندی عبارت را مشخص کند (غم/شادی/ترس/شگفتی).

**سلب مسئولیت**:  
این سند با استفاده از خدمات ترجمه مبتنی بر هوش مصنوعی ترجمه شده است. در حالی که ما تلاش می‌کنیم تا دقت را رعایت کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل اشتباهات یا نادرستی‌هایی باشد. سند اصلی به زبان اصلی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما هیچ مسئولیتی در قبال سوءتفاهم‌ها یا تفسیرهای نادرست ناشی از استفاده از این ترجمه نداریم.