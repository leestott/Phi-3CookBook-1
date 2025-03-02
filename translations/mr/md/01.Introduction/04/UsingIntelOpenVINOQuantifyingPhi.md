# **Intel OpenVINO चा वापर करून Phi-3.5 चे क्वांटायझेशन**

Intel हा पारंपरिक CPU निर्मात्यांपैकी एक आहे ज्याचे बरेच वापरकर्ते आहेत. मशीन लर्निंग आणि डीप लर्निंगच्या वाढीसोबत, Intel ने देखील AI अॅक्सेलेरेशनसाठी स्पर्धेत प्रवेश केला आहे. मॉडेल इनफरन्ससाठी, Intel केवळ GPUs आणि CPUs चाच नव्हे तर NPUs चा देखील वापर करते.

आम्हाला Phi-3.x कुटुंबाला एंड साईडवर तैनात करायचे आहे, ज्यामुळे AI PC आणि Copilot PC चा एक महत्त्वाचा भाग बनण्याची आशा आहे. एंड साईडवर मॉडेल लोडिंग वेगवेगळ्या हार्डवेअर उत्पादकांच्या सहकार्यावर अवलंबून असते. हे प्रकरण मुख्यतः Intel OpenVINO च्या क्वांटायझेशन मॉडेलच्या अनुप्रयोग परिस्थितीवर केंद्रित आहे.

## **OpenVINO म्हणजे काय?**

OpenVINO हे एक ओपन-सोर्स टूलकिट आहे जे क्लाउडपासून एजपर्यंत डीप लर्निंग मॉडेल्स ऑप्टिमाइझ आणि तैनात करण्यासाठी वापरले जाते. हे जनरेटिव्ह AI, व्हिडिओ, ऑडिओ, भाषा यांसारख्या विविध उपयोग प्रकरणांमध्ये डीप लर्निंग इनफरन्सला गती देते, जसे की PyTorch, TensorFlow, ONNX आणि इतर लोकप्रिय फ्रेमवर्कचे मॉडेल्स वापरून. मॉडेल्स रूपांतरित करा, ऑप्टिमाइझ करा, आणि Intel® हार्डवेअर आणि पर्यावरणांवर, ऑन-प्रिमायसेस आणि ऑन-डिव्हाइस, ब्राउझरमध्ये किंवा क्लाउडमध्ये तैनात करा.

आता OpenVINO सह, तुम्ही Intel हार्डवेअरमध्ये GenAI मॉडेल लवकर क्वांटायझ करू शकता आणि मॉडेल संदर्भ गतीमान करू शकता.

आता OpenVINO Phi-3.5-Vision आणि Phi-3.5 Instruct चे क्वांटायझेशन रूपांतरण समर्थन करते.

### **पर्यावरण सेटअप**

कृपया खालील पर्यावरणीय अवलंबित्वे स्थापित केलेली असल्याचे सुनिश्चित करा, ही requirement.txt आहे.

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **OpenVINO वापरून Phi-3.5-Instruct चे क्वांटायझेशन**

टर्मिनलमध्ये, कृपया हा स्क्रिप्ट चालवा

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **OpenVINO वापरून Phi-3.5-Vision चे क्वांटायझेशन**

कृपया हा स्क्रिप्ट Python किंवा Jupyter lab मध्ये चालवा

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

### **🤖 Intel OpenVINO सह Phi-3.5 साठी नमुने**

| लॅब्स    | परिचय | जा |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | तुमच्या AI PC मध्ये Phi-3.5 Instruct कसे वापरायचे ते शिका    |  [जा](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | तुमच्या AI PC मध्ये Phi-3.5 Vision वापरून प्रतिमा कशी विश्लेषित करायची ते शिका      |  [जा](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (video)   | तुमच्या AI PC मध्ये Phi-3.5 Vision वापरून व्हिडिओ कसा विश्लेषित करायचा ते शिका    |  [जा](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |

## **स्रोत**

1. Intel OpenVINO बद्दल अधिक जाणून घ्या [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub रिपॉजिटरी [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**अस्वीकरण**:  
हे दस्तऐवज मशीन-आधारित AI भाषांतर सेवा वापरून अनुवादित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ दस्तऐवज त्याच्या मूळ भाषेत अधिकृत स्रोत मानला जावा. महत्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवादाची शिफारस केली जाते. या भाषांतराच्या वापरामुळे उद्भवलेल्या कोणत्याही गैरसमजुतींसाठी किंवा चुकीच्या अर्थ लावण्यास आम्ही जबाबदार राहणार नाही.