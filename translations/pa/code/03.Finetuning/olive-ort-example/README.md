# Olive ਦੀ ਵਰਤੋਂ ਨਾਲ Phi3 ਨੂੰ Fine-tune ਕਰੋ

ਇਸ ਉਦਾਹਰਨ ਵਿੱਚ ਤੁਸੀਂ Olive ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਇਹ ਕੰਮ ਕਰੋਗੇ:

1. ਇੱਕ LoRA ਐਡਾਪਟਰ ਨੂੰ Fine-tune ਕਰੋ, ਜੋ ਵਾਕਾਂਸ਼ਾਂ ਨੂੰ Sad, Joy, Fear, Surprise ਵਿੱਚ ਵਰਗਬੱਧ ਕਰੇ।
1. ਐਡਾਪਟਰ ਵਜ਼ਨ ਨੂੰ ਬੇਸ ਮਾਡਲ ਵਿੱਚ ਮਰਜ ਕਰੋ।
1. ਮਾਡਲ ਨੂੰ `int4` ਵਿੱਚ ਅਪਟਿਮਾਈਜ਼ ਅਤੇ ਕਵਾਂਟਾਈਜ਼ ਕਰੋ।

ਅਸੀਂ ਤੁਹਾਨੂੰ ਇਹ ਵੀ ਦਿਖਾਵਾਂਗੇ ਕਿ ONNX Runtime (ORT) Generate API ਦੀ ਵਰਤੋਂ ਕਰਕੇ Fine-tuned ਮਾਡਲ ਨੂੰ ਕਿਵੇਂ ਇਨਫਰੈਂਸ ਕਰਨਾ ਹੈ।

> **⚠️ Fine-tuning ਲਈ, ਤੁਹਾਡੇ ਕੋਲ ਇੱਕ ਉਚਿਤ GPU ਉਪਲਬਧ ਹੋਣਾ ਚਾਹੀਦਾ ਹੈ - ਉਦਾਹਰਣ ਲਈ, A10, V100, A100।**

## 💾 ਇੰਸਟਾਲ ਕਰੋ

ਇੱਕ ਨਵੀਂ Python ਵਰਚੁਅਲ ਐਨਵਾਇਰਨਮੈਂਟ ਬਣਾਓ (ਉਦਾਹਰਣ ਲਈ, `conda` ਦੀ ਵਰਤੋਂ ਕਰਕੇ):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

ਅਗਲਾ, Olive ਅਤੇ Fine-tuning ਵਰਕਫਲੋ ਲਈ ਲੋੜੀਂਦੀਆਂ Dependencies ਇੰਸਟਾਲ ਕਰੋ:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Olive ਦੀ ਵਰਤੋਂ ਨਾਲ Phi3 ਨੂੰ Fine-tune ਕਰੋ
[Olive ਕਨਫਿਗਰੇਸ਼ਨ ਫਾਈਲ](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json) ਵਿੱਚ ਇੱਕ *ਵਰਕਫਲੋ* ਹੈ, ਜਿਸ ਵਿੱਚ ਇਹ *ਪਾਸੇ* ਸ਼ਾਮਲ ਹਨ:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

ਉੱਚ-ਪੱਧਰੀ ਰੂਪ ਵਿੱਚ, ਇਹ ਵਰਕਫਲੋ ਇਹ ਕੰਮ ਕਰੇਗਾ:

1. Phi3 ਨੂੰ Fine-tune ਕਰੋ (150 ਸਟੈਪ ਲਈ, ਜਿਸਨੂੰ ਤੁਸੀਂ ਬਦਲ ਸਕਦੇ ਹੋ) [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json) ਡਾਟਾ ਦੀ ਵਰਤੋਂ ਕਰਕੇ।
1. LoRA ਐਡਾਪਟਰ ਵਜ਼ਨ ਨੂੰ ਬੇਸ ਮਾਡਲ ਵਿੱਚ ਮਰਜ ਕਰੋ। ਇਸ ਨਾਲ ਤੁਹਾਨੂੰ ONNX ਫਾਰਮੈਟ ਵਿੱਚ ਇੱਕ ਸਿੰਗਲ ਮਾਡਲ ਆਰਟੀਫੈਕਟ ਮਿਲੇਗਾ।
1. Model Builder ਮਾਡਲ ਨੂੰ ONNX runtime ਲਈ ਅਪਟਿਮਾਈਜ਼ ਕਰੇਗਾ *ਅਤੇ* ਮਾਡਲ ਨੂੰ `int4` ਵਿੱਚ ਕਵਾਂਟਾਈਜ਼ ਕਰੇਗਾ।

ਵਰਕਫਲੋ ਚਲਾਉਣ ਲਈ, ਇਹ ਕਮਾਂਡ ਰਨ ਕਰੋ:

```bash
olive run --config phrase-classification.json
```

ਜਦੋਂ Olive ਮੁਕੰਮਲ ਹੋ ਜਾਂਦਾ ਹੈ, ਤਾਂ ਤੁਹਾਡਾ ਅਪਟਿਮਾਈਜ਼ ਕੀਤਾ ਹੋਇਆ `int4` Fine-tuned Phi3 ਮਾਡਲ ਇਹਥੇ ਉਪਲਬਧ ਹੈ: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`।

## 🧑‍💻 Fine-tuned Phi3 ਨੂੰ ਆਪਣੇ ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਇੰਟੀਗ੍ਰੇਟ ਕਰੋ

ਐਪ ਚਲਾਉਣ ਲਈ:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

ਇਹ ਜਵਾਬ ਫਰੇਜ਼ ਦੀ ਇੱਕ ਸਿੰਗਲ ਵਰਗਬੱਧਤਾ ਹੋਣੀ ਚਾਹੀਦੀ ਹੈ (Sad/Joy/Fear/Surprise)।

**ਅਸਵੀਕਰਨ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ-ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦਿਤ ਕੀਤਾ ਗਿਆ ਹੈ। ਅਸੀਂ ਸਹੀ ਹੋਣ ਦਾ ਯਤਨ ਕਰਦੇ ਹਾਂ, ਪਰ ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਆਟੋਮੇਟਿਕ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਚੱਜੇ ਪੱਖ ਹੋ ਸਕਦੇ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼, ਜੋ ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਹੈ, ਨੂੰ ਅਧਿਕਾਰਤ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੇ ਇਸਤੇਮਾਲ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।