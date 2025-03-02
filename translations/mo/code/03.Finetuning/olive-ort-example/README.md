# Phi3-ийг Olive ашиглан нарийвчлан тохируулах

Энэ жишээгээр та Olive ашиглан дараах зүйлсийг хийнэ:

1. LoRA адаптерийг нарийвчлан тохируулж, өгүүлбэрүүдийг Sad, Joy, Fear, Surprise гэсэн ангилалд хуваана.
1. Адаптерийн жинг үндсэн загварт нэгтгэнэ.
1. Загварыг `int4` болгон оновчтой болгож, тоон хэлбэрт шилжүүлнэ.

Мөн нарийвчлан тохируулсан загварыг ONNX Runtime (ORT) Generate API ашиглан хэрхэн ашиглахыг үзүүлнэ.

> **⚠️ Нарийвчлан тохируулахын тулд та A10, V100, A100 зэрэг тохиромжтой GPU-тэй байх шаардлагатай.**

## 💾 Суурилуулалт

Шинэ Python виртуал орчин үүсгээрэй (жишээлбэл, `conda` ашиглан):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

Дараа нь Olive болон нарийвчлан тохируулах ажлын урсгалын хамаарлуудыг суулгаарай:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Phi3-ийг Olive ашиглан нарийвчлан тохируулах
[Olive тохиргооны файл](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json)-д дараах *дамжуулгуудтай* *ажлын урсгал* агуулагдана:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

Энэхүү ажлын урсгал нь ерөнхийдөө дараах үйлдлүүдийг хийнэ:

1. Phi3-ийг [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json) өгөгдөл ашиглан 150 алхам (өөрчлөх боломжтой) нарийвчлан тохируулна.
1. LoRA адаптерийн жинг үндсэн загварт нэгтгэнэ. Үүний үр дүнд ONNX форматтай нэг загварын артефакт үүснэ.
1. Model Builder нь загварыг ONNX runtime-д оновчтой болгож, загварыг `int4` болгон тоон хэлбэрт шилжүүлнэ.

Ажлын урсгалыг ажиллуулахын тулд дараах командыг гүйцэтгэнэ:

```bash
olive run --config phrase-classification.json
```

Olive дууссаны дараа таны оновчтой болсон `int4` нарийвчлан тохируулсан Phi3 загвар дараах байршилд хадгалагдсан байна: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 Нарийвчлан тохируулсан Phi3-ийг өөрийн програмд нэгтгэх

Програмыг ажиллуулахын тулд:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

Энэхүү хариулт нь өгүүлбэрийг нэг үгээр ангилах болно (Sad/Joy/Fear/Surprise).

It seems like you want the text translated into a language, but "mo" is unclear. Could you clarify which language you mean by "mo"? For example, are you referring to Maori, Mongolian, or another language? Let me know so I can assist you accurately!