# **Microsoft Phi-3.5 tflite ব্যবহার করে Android অ্যাপ তৈরি করা**

এটি Microsoft Phi-3.5 tflite মডেল ব্যবহার করে একটি Android নমুনা।

## **📚 জ্ঞান**

Android LLM Inference API আপনাকে Android অ্যাপ্লিকেশনের জন্য সম্পূর্ণ অন-ডিভাইস বড় ভাষা মডেল (LLMs) চালানোর অনুমতি দেয়, যা ব্যবহার করে আপনি বিভিন্ন কাজ করতে পারেন, যেমন টেক্সট তৈরি করা, প্রাকৃতিক ভাষার আকারে তথ্য পুনরুদ্ধার করা এবং ডকুমেন্ট সারাংশ তৈরি করা। এই টাস্কে একাধিক টেক্সট-টু-টেক্সট বড় ভাষা মডেলের জন্য বিল্ট-ইন সাপোর্ট রয়েছে, যা আপনাকে আপনার Android অ্যাপে সর্বশেষ অন-ডিভাইস জেনারেটিভ AI মডেল প্রয়োগ করতে দেয়।

Google AI Edge Torch একটি পাইথন লাইব্রেরি যা PyTorch মডেলগুলিকে .tflite ফরম্যাটে রূপান্তর করতে সহায়তা করে, যা TensorFlow Lite এবং MediaPipe দিয়ে চালানো যেতে পারে। এটি এমন অ্যাপ্লিকেশনগুলিকে সক্ষম করে যা Android, iOS এবং IoT-এ সম্পূর্ণ অন-ডিভাইস মডেল চালাতে পারে। AI Edge Torch বিস্তৃত CPU কভারেজ প্রদান করে, প্রাথমিক GPU এবং NPU সাপোর্ট সহ। AI Edge Torch PyTorch-এর সাথে ঘনিষ্ঠভাবে একত্রিত হতে চায়, torch.export() এর উপর ভিত্তি করে এবং Core ATen অপারেটরগুলির ভালো কভারেজ প্রদান করে।

## **🪬 নির্দেশিকা**

### **🔥 Microsoft Phi-3.5 কে tflite সাপোর্টে রূপান্তর করা**

0. এই নমুনাটি Android 14+ এর জন্য।

1. Python 3.10.12 ইনস্টল করুন।

***পরামর্শ:*** আপনার Python পরিবেশ ইনস্টল করতে conda ব্যবহার করুন।

2. Ubuntu 20.04 / 22.04 (দয়া করে [google ai-edge-torch](https://github.com/google-ai-edge/ai-edge-torch)-এ ফোকাস করুন।)

***পরামর্শ:*** Azure Linux VM বা তৃতীয় পক্ষের ক্লাউড VM ব্যবহার করে আপনার পরিবেশ তৈরি করুন।

3. আপনার Linux bash-এ যান, এবং Python লাইব্রেরি ইনস্টল করুন।

```bash

git clone https://github.com/google-ai-edge/ai-edge-torch.git

cd ai-edge-torch

pip install -r requirements.txt -U 

pip install tensorflow-cpu -U

pip install -e .

```

4. Hugging Face থেকে Microsoft-3.5-Instruct ডাউনলোড করুন।

```bash

git lfs install

git clone  https://huggingface.co/microsoft/Phi-3.5-mini-instruct

```

5. Microsoft Phi-3.5 কে tflite-এ রূপান্তর করুন।

```bash

python ai-edge-torch/ai_edge_torch/generative/examples/phi/convert_phi3_to_tflite.py --checkpoint_path  Your Microsoft Phi-3.5-mini-instruct path --tflite_path Your Microsoft Phi-3.5-mini-instruct tflite path  --prefill_seq_len 1024 --kv_cache_max_len 1280 --quantize True

```

### **🔥 Microsoft Phi-3.5 কে Android Mediapipe Bundle-এ রূপান্তর করা**

প্রথমে Mediapipe ইনস্টল করুন।

```bash

pip install mediapipe

```

এই কোডটি [আপনার নোটবুকে](../../../../../../code/09.UpdateSamples/Aug/Android/convert/convert_phi.ipynb) চালান।

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

### **🔥 আপনার Android ডিভাইসের পাথে adb push টাস্ক মডেল ব্যবহার করা**

```bash

adb shell rm -r /data/local/tmp/llm/ # Remove any previously loaded models

adb shell mkdir -p /data/local/tmp/llm/

adb push 'Your Phi-3.5 task model path' /data/local/tmp/llm/phi3.task

```

### **🔥 আপনার Android কোড চালানো**

![ডেমো](../../../../../../translated_images/demo.8981711efb5a9cee5dcd835f66b3b31b94b4f3e527300e15a98a0d48863b9fbd.bn.png)

**অস্বীকৃতি**:  
এই নথিটি মেশিন-ভিত্তিক কৃত্রিম বুদ্ধিমত্তা অনুবাদ পরিষেবা ব্যবহার করে অনুবাদ করা হয়েছে। আমরা যথাসম্ভব সঠিক অনুবাদের চেষ্টা করি, তবে অনুগ্রহ করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসংগতি থাকতে পারে। এর মূল ভাষায় থাকা নথিটিকেই প্রামাণিক উৎস হিসাবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের ক্ষেত্রে, পেশাদার মানব অনুবাদ সুপারিশ করা হয়। এই অনুবাদ ব্যবহারের ফলে সৃষ্ট কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী নই।