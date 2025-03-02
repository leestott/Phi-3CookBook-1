# Olive प्रयोग गरेर Phi3 लाई Fine-tune गर्नुहोस्

यस उदाहरणमा तपाईं Olive प्रयोग गरेर निम्न कार्यहरू गर्नुहुनेछ:

1. LoRA adapter लाई Fine-tune गरेर वाक्यांशहरूलाई Sad, Joy, Fear, Surprise मा वर्गीकृत गर्नुहोस्।
1. Adapter का वजनहरूलाई आधारभूत मोडेलमा मर्ज गर्नुहोस्।
1. मोडेललाई `int4` मा Optimize र Quantize गर्नुहोस्।

हामी तपाईंलाई ONNX Runtime (ORT) Generate API प्रयोग गरेर Fine-tuned मोडेललाई कसरी inference गर्ने भनेर पनि देखाउनेछौं।

> **⚠️ Fine-tuning को लागि, तपाईंलाई उपयुक्त GPU उपलब्ध हुन आवश्यक छ - उदाहरणका लागि, A10, V100, A100।**

## 💾 स्थापना गर्नुहोस्

नयाँ Python भर्चुअल वातावरण सिर्जना गर्नुहोस् (उदाहरणका लागि, `conda` प्रयोग गरेर):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

पछाडि, Olive र Fine-tuning workflow का लागि आवश्यक dependencies स्थापना गर्नुहोस्:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Olive प्रयोग गरेर Phi3 लाई Fine-tune गर्नुहोस्
[Olive configuration file](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) मा *workflow* निम्न *passes* समावेश गर्दछ:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

उच्च-स्तरमा, यो workflow ले निम्न कार्यहरू गर्दछ:

1. [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json) डेटा प्रयोग गरेर Phi3 लाई (150 steps को लागि, जुन तपाईं परिमार्जन गर्न सक्नुहुन्छ) Fine-tune गर्नुहोस्।
1. LoRA adapter का वजनहरूलाई आधारभूत मोडेलमा मर्ज गर्नुहोस्। यसले तपाईंलाई ONNX ढाँचामा एकल मोडेल आर्टिफ्याक्ट दिनेछ।
1. Model Builder ले मोडेललाई ONNX runtime का लागि Optimize गर्नेछ *र* मोडेललाई `int4` मा Quantize गर्नेछ।

workflow चलाउन, निम्न कमाण्ड चलाउनुहोस्:

```bash
olive run --config phrase-classification.json
```

Olive ले काम पूरा गरेपछि, तपाईंको Optimized `int4` Fine-tuned Phi3 मोडेल यहाँ उपलब्ध हुनेछ: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`।

## 🧑‍💻 Fine-tuned Phi3 लाई तपाईंको एप्लिकेसनमा समावेश गर्नुहोस् 

एप्लिकेसन चलाउन:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

यो प्रतिक्रिया वाक्यांशको एक शब्दको वर्गीकरण (Sad/Joy/Fear/Surprise) हुनेछ।

**अस्वीकरण**:  
यो दस्तावेज मेसिन-आधारित एआई अनुवाद सेवाहरू प्रयोग गरी अनुवाद गरिएको हो। हामी शुद्धताको लागि प्रयास गर्दछौं, तर कृपया जानकार हुनुहोस् कि स्वचालित अनुवादहरूले त्रुटिहरू वा अशुद्धताहरू समावेश गर्न सक्छ। यसको मौलिक भाषामा रहेको मूल दस्तावेजलाई प्राधिकृत स्रोत मानिनुपर्छ। महत्त्वपूर्ण जानकारीका लागि, व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न हुने कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी उत्तरदायी हुने छैनौं।