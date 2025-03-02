# **Phi-3.5 लाई Intel OpenVINO प्रयोग गरी क्वान्टाइज गर्ने**

Intel सबैभन्दा परम्परागत CPU निर्माता हो जसका धेरै प्रयोगकर्ता छन्। मेसिन लर्निङ र डीप लर्निङको बढ्दो लोकप्रियतासँगै, Intel ले पनि AI एक्सेलेरेसनको प्रतिस्पर्धामा सामेल भएको छ। मोडेल इन्फरेन्सका लागि, Intel ले GPU र CPU मात्र नभई NPU पनि प्रयोग गर्दछ।

हामी Phi-3.x परिवारलाई एन्ड साइडमा तैनाथ गर्न चाहन्छौं, जसले AI PC र Copilot PC को सबैभन्दा महत्त्वपूर्ण भाग बन्न सकोस् भन्ने हाम्रो आशा छ। एन्ड साइडमा मोडेल लोड गर्नका लागि विभिन्न हार्डवेयर निर्माताको सहकार्य आवश्यक पर्छ। यो अध्याय मुख्यत: Intel OpenVINO लाई क्वान्टिटेटिभ मोडेलको रूपमा प्रयोग गर्ने अनुप्रयोग परिदृश्यमा केन्द्रित छ।  

## **OpenVINO के हो**

OpenVINO क्लाउडदेखि एजसम्म डीप लर्निङ मोडेलहरूलाई अप्टिमाइज र डिप्लोय गर्नका लागि खुला स्रोत टूलकिट हो। यसले जेनेरेटिभ AI, भिडियो, अडियो, र भाषा जस्ता विभिन्न उपयोग केसहरूमा लोकप्रिय फ्रेमवर्कहरू जस्तै PyTorch, TensorFlow, ONNX, र अन्यबाट मोडेलहरूको इन्फरेन्सलाई तीव्र बनाउँछ। मोडेलहरूलाई रूपान्तरण र अप्टिमाइज गर्नुहोस्, र Intel® हार्डवेयर र वातावरणहरूको संयोजनमा, अन-प्रिमाइस र अन-डिभाइस, ब्राउजर वा क्लाउडमा तैनाथ गर्नुहोस्।

अब OpenVINO को साथमा, तपाईं Intel हार्डवेयरमा GenAI मोडेललाई छिटो क्वान्टाइज गर्न सक्नुहुन्छ र मोडेल इन्फरेन्सलाई तीव्र बनाउन सक्नुहुन्छ।

हाल OpenVINO ले Phi-3.5-Vision र Phi-3.5 Instruct को क्वान्टाइजेसन रूपान्तरणलाई समर्थन गर्दछ।

### **पर्यावरण सेटअप**

कृपया तलका वातावरण निर्भरताहरू इन्स्टल भएको सुनिश्चित गर्नुहोस्, यो requirement.txt हो

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **Phi-3.5-Instruct लाई OpenVINO प्रयोग गरी क्वान्टाइज गर्ने**

Terminal मा यो स्क्रिप्ट चलाउनुहोस्

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **Phi-3.5-Vision लाई OpenVINO प्रयोग गरी क्वान्टाइज गर्ने**

Python वा Jupyter Lab मा यो स्क्रिप्ट चलाउनुहोस्

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

### **🤖 Intel OpenVINO संग Phi-3.5 का नमूनाहरू**

| प्रयोगशालाहरू    | परिचय | जानुहोस् |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | तपाईंको AI PC मा Phi-3.5 Instruct कसरी प्रयोग गर्ने भन्ने कुरा सिक्नुहोस्    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | तपाईंको AI PC मा Phi-3.5 Vision प्रयोग गरी छविलाई विश्लेषण कसरी गर्ने भन्ने कुरा सिक्नुहोस्      |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (video)   | तपाईंको AI PC मा Phi-3.5 Vision प्रयोग गरी भिडियो विश्लेषण कसरी गर्ने भन्ने कुरा सिक्नुहोस्    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |

## **स्रोतहरू**

1. Intel OpenVINO को बारेमा थप जान्नुहोस् [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub Repo [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**अस्वीकरण**:  
यो दस्तावेज मेसिन-आधारित एआई अनुवाद सेवाहरू प्रयोग गरी अनुवाद गरिएको छ। हामी यथासम्भव सही अनुवाद प्रदान गर्न प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटिहरू वा अशुद्धताहरू हुन सक्छ। मूल भाषामा रहेको मूल दस्तावेजलाई नै आधिकारिक स्रोत मानिनुपर्छ। महत्त्वपूर्ण जानकारीको लागि, व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यो अनुवाद प्रयोग गर्दा उत्पन्न हुने कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी जिम्मेवार हुने छैनौं।