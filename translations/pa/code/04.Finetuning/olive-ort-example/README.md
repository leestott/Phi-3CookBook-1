# Olive ਦੀ ਵਰਤੋਂ ਨਾਲ Phi3 ਨੂੰ Fine-tune ਕਰੋ

ਇਸ ਉਦਾਹਰਣ ਵਿੱਚ ਤੁਸੀਂ Olive ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋ:

1. ਇੱਕ LoRA ਅਡਾਪਟਰ ਨੂੰ Fine-tune ਕਰਨ ਲਈ, ਜੋ ਵਾਕਾਂ ਨੂੰ Sad, Joy, Fear, Surprise ਵਿੱਚ ਵਰਗਬੱਧ ਕਰਦਾ ਹੈ।
1. ਅਡਾਪਟਰ ਦੇ ਭਾਰਾਂ ਨੂੰ ਮੂਲ ਮਾਡਲ ਵਿੱਚ ਮਿਲਾਓ।
1. ਮਾਡਲ ਨੂੰ `int4` ਵਿੱਚ Optimize ਅਤੇ Quantize ਕਰੋ।

ਅਸੀਂ ਤੁਹਾਨੂੰ ਇਹ ਵੀ ਦਿਖਾਵਾਂਗੇ ਕਿ ONNX Runtime (ORT) Generate API ਦੀ ਵਰਤੋਂ ਕਰਕੇ Fine-tuned ਮਾਡਲ ਨੂੰ ਕਿਵੇਂ inference ਕਰਨਾ ਹੈ।

> **⚠️ Fine-tuning ਲਈ, ਤੁਹਾਡੇ ਕੋਲ ਇੱਕ ਉਚਿਤ GPU ਉਪਲਬਧ ਹੋਣਾ ਚਾਹੀਦਾ ਹੈ - ਉਦਾਹਰਣ ਲਈ, A10, V100, A100।**

## 💾 ਇੰਸਟਾਲ ਕਰੋ

ਨਵਾਂ Python ਵਰਚੁਅਲ ਇਨਵਾਇਰਨਮੈਂਟ ਬਣਾਓ (ਉਦਾਹਰਣ ਲਈ, `conda` ਦੀ ਵਰਤੋਂ ਕਰਕੇ):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

ਫਿਰ, Olive ਅਤੇ Fine-tuning workflow ਲਈ dependencies ਇੰਸਟਾਲ ਕਰੋ:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Olive ਦੀ ਵਰਤੋਂ ਨਾਲ Phi3 ਨੂੰ Fine-tune ਕਰੋ
[Olive configuration file](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) ਵਿੱਚ ਇੱਕ *workflow* ਹੈ ਜਿਸ ਵਿੱਚ ਹੇਠਲੇ *passes* ਸ਼ਾਮਲ ਹਨ:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

ਇਸ workflow ਦਾ ਉੱਚ-ਪੱਧਰੀ ਵੇਰਵਾ:

1. Phi3 ਨੂੰ Fine-tune ਕਰੋ (150 steps ਲਈ, ਜਿਨ੍ਹਾਂ ਨੂੰ ਤੁਸੀਂ ਬਦਲ ਸਕਦੇ ਹੋ) [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json) ਡਾਟਾ ਦੀ ਵਰਤੋਂ ਕਰਕੇ।
1. LoRA ਅਡਾਪਟਰ ਦੇ ਭਾਰਾਂ ਨੂੰ ਮੂਲ ਮਾਡਲ ਵਿੱਚ ਮਿਲਾਓ। ਇਸ ਨਾਲ ਤੁਹਾਨੂੰ ONNX ਫਾਰਮੈਟ ਵਿੱਚ ਇੱਕ ਸਿੰਗਲ ਮਾਡਲ artifact ਮਿਲੇਗਾ।
1. Model Builder ਮਾਡਲ ਨੂੰ ONNX runtime ਲਈ Optimize ਅਤੇ `int4` ਵਿੱਚ Quantize ਕਰੇਗਾ।

workflow ਚਲਾਉਣ ਲਈ, ਇਹ ਚਲਾਓ:

```bash
olive run --config phrase-classification.json
```

ਜਦੋਂ Olive ਮੁਕੰਮਲ ਹੋ ਜਾਂਦਾ ਹੈ, ਤਾਂ ਤੁਹਾਡਾ optimized `int4` Fine-tuned Phi3 ਮਾਡਲ ਇਸ ਥਾਂ ਉਪਲਬਧ ਹੁੰਦਾ ਹੈ: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`।

## 🧑‍💻 Fine-tuned Phi3 ਨੂੰ ਆਪਣੇ ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਸ਼ਾਮਲ ਕਰੋ

ਐਪ ਚਲਾਉਣ ਲਈ:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

ਇਸ ਦਾ ਜਵਾਬ ਵਾਕ ਦਾ ਸਿਰਫ ਇੱਕ ਸ਼ਬਦ ਵਿੱਚ ਵਰਗਬੱਧ ਹੋਣਾ ਚਾਹੀਦਾ ਹੈ (Sad/Joy/Fear/Surprise)।

**ਅਸਵੀਕਾਰਨਾ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ-ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਦਾ ਯਤਨ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਚੱਜੇ ਹੋਣ ਦੀ ਸੰਭਾਵਨਾ ਹੋ ਸਕਦੀ ਹੈ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਨੂੰ ਇਸ ਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਅਧਿਕਾਰਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।