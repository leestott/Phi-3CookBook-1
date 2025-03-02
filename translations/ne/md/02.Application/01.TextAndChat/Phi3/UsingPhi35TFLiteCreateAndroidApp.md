# **Microsoft Phi-3.5 tflite प्रयोग गरेर Android एप बनाउन**

यो एउटा Android नमूना हो जसले Microsoft Phi-3.5 tflite मोडेलहरू प्रयोग गर्छ।

## **📚 ज्ञान**

Android LLM Inference API ले तपाईंलाई Android अनुप्रयोगहरूको लागि ठूला भाषा मोडेलहरू (LLMs) पूर्ण रूपमा उपकरणमै चलाउन अनुमति दिन्छ। यसले तपाईंलाई पाठ उत्पन्न गर्न, प्राकृतिक भाषामा जानकारी पुनःप्राप्त गर्न, र कागजातहरूको संक्षेप गर्न जस्ता विभिन्न कार्यहरू गर्न प्रयोग गर्न सकिन्छ। यस कार्यले धेरै पाठ-देखि-पाठ ठूला भाषा मोडेलहरूको लागि पूर्वनिर्मित समर्थन प्रदान गर्दछ, जसले तपाईंलाई नवीनतम उपकरणमै चल्ने Generative AI मोडेलहरू तपाईंको Android एपहरूमा लागू गर्न मद्दत गर्छ।

Google AI Edge Torch एउटा Python पुस्तकालय हो जसले PyTorch मोडेलहरूलाई .tflite ढाँचामा रूपान्तरण गर्न समर्थन गर्दछ। यी मोडेलहरू त्यसपछि TensorFlow Lite र MediaPipe को साथ चलाउन सकिन्छ। यसले Android, iOS र IoT का लागि अनुप्रयोगहरू सक्षम गर्दछ जसले मोडेलहरू पूर्ण रूपमा उपकरणमै चलाउन सक्छ। AI Edge Torch ले व्यापक CPU कभरेज प्रदान गर्दछ, प्रारम्भिक GPU र NPU समर्थनको साथ। AI Edge Torch ले PyTorch सँग नजिकबाट एकीकृत हुने प्रयास गर्दछ, torch.export() मा आधारित हुँदै र Core ATen अपरेटरहरूको राम्रो कभरेज प्रदान गर्दै।

## **🪬 मार्गदर्शन**

### **🔥 Microsoft Phi-3.5 लाई tflite मा रूपान्तरण गर्ने तरिका**

0. यो नमूना Android 14+ का लागि हो।

1. Python 3.10.12 स्थापना गर्नुहोस्।

***सुझाव:*** conda प्रयोग गरेर तपाईंको Python वातावरण स्थापना गर्नुहोस्।

2. Ubuntu 20.04 / 22.04 (कृपया [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch) मा ध्यान दिनुहोस्।)

***सुझाव:*** Azure Linux VM वा तेस्रो पक्षको क्लाउड VM प्रयोग गरेर तपाईंको वातावरण सिर्जना गर्नुहोस्।

3. तपाईंको Linux bash मा जानुहोस् र Python पुस्तकालय स्थापना गर्नुहोस्। 

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Hugging Face बाट Microsoft-3.5-Instruct डाउनलोड गर्नुहोस्।

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. Microsoft Phi-3.5 लाई tflite मा रूपान्तरण गर्नुहोस्।

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 Microsoft Phi-3.5 लाई Android Mediapipe Bundle मा रूपान्तरण गर्ने तरिका**

पहिले Mediapipe स्थापना गर्नुहोस्।

```bash

pip install mediapipe

```

[तपाईंको नोटबुकमा](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb) यो कोड चलाउनुहोस्।

```python

import mediapipe as mp
from mediapipe.tasks.python.genai import bundler

config = bundler.BundleConfig(
    tflite_model='Your Phi-3.5 tflite model path',
    tokenizer_model='Your Phi-3.5 tokenizer model path',
    start_token='start_token',
    stop_tokens=[STOP_TOKENS],
    output_filename='Your Phi-3.5 task model path',
    enable_bytes_to_unicode_mapping=True or Flase,
)
bundler.create_bundle(config)

```

### **🔥 तपाईंको Android उपकरणको पथमा adb push task model प्रयोग गर्नुहोस्।**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 तपाईंको Android कोड चलाउनुहोस्।**

![demo](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.ne.png)

**अस्वीकरण**:  
यो दस्तावेज़ मेसिन-आधारित एआई अनुवाद सेवाहरू प्रयोग गरेर अनुवाद गरिएको हो। हामी यथासम्भव सही अनुवाद प्रदान गर्न प्रयास गर्दछौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटिहरू वा असत्यताहरू हुन सक्छ। मूल भाषामा रहेको मूल दस्तावेजलाई प्राधिकृत स्रोतको रूपमा मानिनुपर्छ। महत्वपूर्ण जानकारीका लागि, व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यो अनुवाद प्रयोग गर्दा उत्पन्न हुने कुनै पनि गलतफहमी वा गलत व्याख्याका लागि हामी जिम्मेवार हुने छैनौं।  