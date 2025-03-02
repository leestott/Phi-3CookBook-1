# **Phi-3.5 কে Intel OpenVINO ব্যবহার করে কোয়ান্টাইজ করা**

Intel হলো সবচেয়ে ঐতিহ্যবাহী CPU নির্মাতা, যার অনেক ব্যবহারকারী রয়েছে। মেশিন লার্নিং এবং ডিপ লার্নিংয়ের উত্থানের সঙ্গে, Intel AI অ্যাক্সিলারেশনের প্রতিযোগিতায় যোগ দিয়েছে। মডেল ইনফারেন্সের জন্য, Intel শুধুমাত্র GPU এবং CPU ব্যবহার করে না, বরং NPU-ও ব্যবহার করে।

আমরা চাই Phi-3.x Family-কে এন্ড-সাইডে ডেপ্লয় করতে, যাতে এটি AI PC এবং Copilot PC-এর সবচেয়ে গুরুত্বপূর্ণ অংশ হয়ে ওঠে। এন্ড-সাইডে মডেল লোড করার জন্য বিভিন্ন হার্ডওয়্যার নির্মাতার সহযোগিতা প্রয়োজন। এই অধ্যায়টি মূলত Intel OpenVINO-এর একটি কোয়ান্টিটেটিভ মডেল হিসাবে প্রয়োগের ক্ষেত্রে মনোযোগ দেয়।  


## **OpenVINO কী?**

OpenVINO হলো একটি ওপেন-সোর্স টুলকিট, যা ক্লাউড থেকে এজ পর্যন্ত ডিপ লার্নিং মডেল অপ্টিমাইজ এবং ডেপ্লয় করার জন্য ব্যবহৃত হয়। এটি জেনারেটিভ AI, ভিডিও, অডিও এবং ভাষার মতো বিভিন্ন ক্ষেত্রে ডিপ লার্নিং ইনফারেন্সকে ত্বরান্বিত করে। PyTorch, TensorFlow, ONNX এবং আরও অনেক জনপ্রিয় ফ্রেমওয়ার্কের মডেলগুলোর জন্য এটি ব্যবহার করা যায়। মডেল রূপান্তর এবং অপ্টিমাইজ করুন, এবং Intel® হার্ডওয়্যার এবং পরিবেশের মিশ্রণে, অন-প্রিমাইস এবং অন-ডিভাইস, ব্রাউজারে বা ক্লাউডে ডেপ্লয় করুন।

এখন OpenVINO-এর সাহায্যে, আপনি Intel হার্ডওয়্যারে GenAI মডেল দ্রুত কোয়ান্টাইজ করতে পারবেন এবং মডেল রেফারেন্স ত্বরান্বিত করতে পারবেন।

বর্তমানে OpenVINO Phi-3.5-Vision এবং Phi-3.5 Instruct-এর কোয়ান্টাইজেশন কনভার্সন সাপোর্ট করে।  


### **পরিবেশ সেটআপ**

অনুগ্রহ করে নিশ্চিত করুন যে নিম্নলিখিত পরিবেশ নির্ভরতাগুলি ইনস্টল করা আছে, এটি হলো requirement.txt  

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```  


### **OpenVINO ব্যবহার করে Phi-3.5-Instruct কোয়ান্টাইজ করা**

টার্মিনালে, অনুগ্রহ করে এই স্ক্রিপ্টটি চালান  

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```  


### **OpenVINO ব্যবহার করে Phi-3.5-Vision কোয়ান্টাইজ করা**

Python বা Jupyter ল্যাবে এই স্ক্রিপ্টটি চালান  

```python

import requests
from pathlib import Path
from ov_phi3_vision import convert_phi3_model
import nncf

if not Path("ov_phi3_vision.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/notebooks/phi-3-vision/ov_phi3_vision.py")
    open("ov_phi3_vision.py", "w").write(r.text)


if not Path("gradio_helper.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/notebooks/phi-3-vision/gradio_helper.py")
    open("gradio_helper.py", "w").write(r.text)

if not Path("notebook_utils.py").exists():
    r = requests.get(url="https://raw.githubusercontent.com/openvinotoolkit/openvino_notebooks/latest/utils/notebook_utils.py")
    open("notebook_utils.py", "w").write(r.text)



model_id = "microsoft/Phi-3.5-vision-instruct"
out_dir = Path("../model/phi-3.5-vision-128k-instruct-ov")
compression_configuration = {
    "mode": nncf.CompressWeightsMode.INT4_SYM,
    "group_size": 64,
    "ratio": 0.6,
}
if not out_dir.exists():
    convert_phi3_model(model_id, out_dir, compression_configuration)

```  


### **🤖 Intel OpenVINO সহ Phi-3.5-এর জন্য নমুনা**

| ল্যাব    | পরিচিতি | যান |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | আপনার AI PC-তে Phi-3.5 Instruct কীভাবে ব্যবহার করবেন তা শিখুন    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | আপনার AI PC-তে Phi-3.5 Vision ব্যবহার করে কীভাবে ইমেজ বিশ্লেষণ করবেন তা শিখুন      |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (video)   | আপনার AI PC-তে Phi-3.5 Vision ব্যবহার করে কীভাবে ভিডিও বিশ্লেষণ করবেন তা শিখুন    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |  


## **রিসোর্স**

1. Intel OpenVINO সম্পর্কে আরও জানুন [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub রিপোজিটরি [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**অস্বীকৃতি**:  
এই নথি মেশিন-ভিত্তিক এআই অনুবাদ সেবার মাধ্যমে অনূদিত হয়েছে। আমরা যথাসম্ভব নির্ভুলতার জন্য চেষ্টা করি, তবে দয়া করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ভুল বা অসঙ্গতি থাকতে পারে। নথির মূল ভাষায় লেখা আসল সংস্করণটিকে প্রামাণ্য উৎস হিসেবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদের সুপারিশ করা হয়। এই অনুবাদ ব্যবহার থেকে উদ্ভূত যে কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী নই।