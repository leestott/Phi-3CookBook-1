# Phi3-ийг Olive ашиглан тохируулах

Энэ жишээн дээр Olive-ийг ашиглан дараах ажлуудыг гүйцэтгэнэ:

1. LoRA адаптерийг тохируулж өгүүлбэрүүдийг Sad, Joy, Fear, Surprise гэсэн ангилалд хуваах.
1. Адаптерийн жинг үндсэн загварт нэгтгэх.
1. Загварыг `int4` болгон оновчтой болгож, тоон хэлбэрт шилжүүлэх.

Мөн ONNX Runtime (ORT) Generate API ашиглан тохируулсан загвараар хэрхэн таамаглал хийхийг үзүүлэх болно.

> **⚠️ Тохируулахад тохиромжтой GPU шаардлагатай - жишээ нь, A10, V100, A100 гэх мэт.**

## 💾 Суурилуулалт

Шинэ Python виртуал орчин үүсгээрэй (жишээ нь, `conda` ашиглан):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

Дараа нь Olive болон тохируулах ажлын урсгалын хамаарлуудыг суулгаарай:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Phi3-ийг Olive ашиглан тохируулах
[Olive тохиргооны файл](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json)-д дараах *дамжуулгуудтай* *ажлын урсгал* агуулагдана:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

Өндөр түвшинд энэ ажлын урсгал дараах байдлаар ажиллана:

1. [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json) өгөгдлийг ашиглан Phi3-ийг (150 алхам, өөрчлөх боломжтой) тохируулна.
1. LoRA адаптерийн жинг үндсэн загварт нэгтгэнэ. Үүний үр дүнд ONNX форматтай нэг загварын файлыг үүсгэнэ.
1. Model Builder нь загварыг ONNX runtime-д оновчтой болгож, мөн `int4` болгон тоон хэлбэрт шилжүүлнэ.

Ажлын урсгалыг гүйцэтгэхийн тулд дараах командыг ажиллуулна:

```bash
olive run --config phrase-classification.json
```

Olive дууссаны дараа, оновчтой `int4` тохируулсан Phi3 загвар дараах байршилд хадгалагдана: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 Тохируулсан Phi3-ийг програмдаа нэгтгэх 

Програмыг ажиллуулахын тулд:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

Энэ нь өгүүлбэрийг нэг үгээр ангилах хариу өгөх болно (Sad/Joy/Fear/Surprise).

It seems you may have meant "mo," but could you please clarify which language you are referring to? For example, "mo" could refer to Māori, Mon (a language spoken in Myanmar and Thailand), or something else. Let me know so I can assist you accurately!