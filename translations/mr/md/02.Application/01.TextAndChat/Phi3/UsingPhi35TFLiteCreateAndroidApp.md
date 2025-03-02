# **मायक्रोसॉफ्ट Phi-3.5 tflite वापरून Android अॅप तयार करणे**

हे मायक्रोसॉफ्ट Phi-3.5 tflite मॉडेल्स वापरणारे Android चे एक नमुना आहे.

## **📚 ज्ञान**

Android LLM Inference API तुम्हाला Android अॅप्ससाठी मोठ्या भाषिक मॉडेल्स (LLMs) पूर्णपणे डिव्हाइसवर चालवण्याची परवानगी देते. याचा उपयोग तुम्ही विविध कामांसाठी करू शकता, जसे की मजकूर तयार करणे, नैसर्गिक भाषेत माहिती मिळवणे आणि दस्तऐवजांचे सारांश तयार करणे. या कार्यामध्ये अनेक टेक्स्ट-टू-टेक्स्ट मोठ्या भाषिक मॉडेल्ससाठी अंगभूत समर्थन आहे, ज्यामुळे तुम्ही तुमच्या Android अॅप्समध्ये नवीनतम ऑन-डिव्हाइस जनरेटिव्ह AI मॉडेल्स लागू करू शकता.

Google AI Edge Torch ही एक पायथन लायब्ररी आहे जी PyTorch मॉडेल्सना .tflite स्वरूपात रूपांतरित करण्यासाठी समर्थन देते, ज्यामुळे ते TensorFlow Lite आणि MediaPipe सह चालवले जाऊ शकतात. यामुळे Android, iOS आणि IoT अॅप्ससाठी संधी निर्माण होते, ज्यामध्ये मॉडेल्स पूर्णपणे डिव्हाइसवर चालवता येतात. AI Edge Torch विस्तृत CPU कव्हरेज देते, तसेच प्रारंभी GPU आणि NPU समर्थन देखील प्रदान करते. AI Edge Torch, PyTorch सह जवळून एकत्रीकरण साधण्याचा प्रयत्न करते, torch.export() वर आधारित राहून Core ATen ऑपरेटर्सचे चांगले कव्हरेज देते.

## **🪬 मार्गदर्शक**

### **🔥 मायक्रोसॉफ्ट Phi-3.5 ला tflite मध्ये रूपांतरित करा**

0. हा नमुना Android 14+ साठी आहे.

1. Python 3.10.12 इंस्टॉल करा.

***सूचना:*** तुमच्या Python वातावरणासाठी conda वापरण्याचा विचार करा.

2. Ubuntu 20.04 / 22.04 (कृपया [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch) वर लक्ष केंद्रित करा)

***सूचना:*** Azure Linux VM किंवा तृतीय पक्षाचे क्लाउड VM वापरून तुमचे वातावरण तयार करा.

3. तुमच्या Linux bash मध्ये जा, आणि Python लायब्ररी इंस्टॉल करा.

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Hugging Face वरून Microsoft-3.5-Instruct डाउनलोड करा.

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. मायक्रोसॉफ्ट Phi-3.5 ला tflite मध्ये रूपांतरित करा.

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 मायक्रोसॉफ्ट Phi-3.5 ला Android Mediapipe बंडलमध्ये रूपांतरित करा**

कृपया प्रथम mediapipe इंस्टॉल करा.

```bash

pip install mediapipe

```

[तुमच्या नोटबुकमध्ये](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb) हा कोड चालवा.

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

### **🔥 adb push वापरून मॉडेल तुमच्या Android डिव्हाइसच्या पथावर पाठवा**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 तुमचा Android कोड चालवा**

![demo](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.mr.png)

**अस्वीकृती**:  
हे दस्तऐवज मशीन-आधारित AI भाषांतर सेवांचा वापर करून भाषांतरित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित भाषांतरे त्रुटी किंवा अचूकतेच्या अभावासह असू शकतात. मूळ भाषेतील मूळ दस्तऐवज अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी, व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या भाषांतराचा वापर करून झालेल्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार राहणार नाही.