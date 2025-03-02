# **Intel OpenVINO ਦੀ ਵਰਤੋਂ ਨਾਲ Phi-3.5 ਦਾ ਕਵਾਂਟਾਈਜ਼ ਕਰਨਾ**

Intel ਸਭ ਤੋਂ ਪੁਰਾਣਾ CPU ਨਿਰਮਾਤਾ ਹੈ ਜਿਸਦੇ ਬਹੁਤ ਸਾਰੇ ਉਪਭੋਗਤਾ ਹਨ। ਮਸ਼ੀਨ ਲਰਨਿੰਗ ਅਤੇ ਡੀਪ ਲਰਨਿੰਗ ਦੇ ਉਭਾਰ ਨਾਲ, Intel ਨੇ ਵੀ AI ਤੇਜ਼ੀ ਲਈ ਮੁਕਾਬਲੇ ਵਿੱਚ ਹਿੱਸਾ ਲਿਆ ਹੈ। ਮਾਡਲ ਇਨਫਰੈਂਸ ਲਈ, Intel ਸਿਰਫ਼ GPUs ਅਤੇ CPUs ਹੀ ਨਹੀਂ, ਸਗੋਂ NPUs ਦੀ ਵੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ।

ਅਸੀਂ ਚਾਹੁੰਦੇ ਹਾਂ ਕਿ Phi-3.x ਪਰਿਵਾਰ ਨੂੰ ਐਂਡ ਸਾਈਡ ਤੇ ਡਿਪਲੌਇ ਕੀਤਾ ਜਾਵੇ, ਤਾਂ ਜੋ ਇਹ AI PC ਅਤੇ Copilot PC ਦਾ ਸਭ ਤੋਂ ਮਹੱਤਵਪੂਰਨ ਹਿੱਸਾ ਬਣ ਸਕੇ। ਐਂਡ ਸਾਈਡ ਤੇ ਮਾਡਲ ਨੂੰ ਲੋਡ ਕਰਨ ਲਈ ਵੱਖ-ਵੱਖ ਹਾਰਡਵੇਅਰ ਨਿਰਮਾਤਾਵਾਂ ਦੇ ਸਹਿਯੋਗ 'ਤੇ ਨਿਰਭਰ ਕਰਨਾ ਪੈਂਦਾ ਹੈ। ਇਹ ਅਧਿਆਇ ਮੁੱਖ ਤੌਰ 'ਤੇ Intel OpenVINO ਦੇ ਇੱਕ ਕਵਾਂਟਾਈਟਿਵ ਮਾਡਲ ਦੇ ਐਪਲੀਕੇਸ਼ਨ ਸਿਨਾਰਿਓ 'ਤੇ ਧਿਆਨ ਕੇਂਦਰਤ ਕਰਦਾ ਹੈ।  

## **OpenVINO ਕੀ ਹੈ**

OpenVINO ਇੱਕ ਓਪਨ-ਸੋਰਸ ਟੂਲਕਿਟ ਹੈ ਜੋ ਕਲਾਉਡ ਤੋਂ ਐਜ ਤੱਕ ਡੀਪ ਲਰਨਿੰਗ ਮਾਡਲਾਂ ਨੂੰ ਓਪਟੀਮਾਈਜ਼ ਅਤੇ ਡਿਪਲੌਇ ਕਰਨ ਲਈ ਵਰਤਿਆ ਜਾਂਦਾ ਹੈ। ਇਹ ਡੀਪ ਲਰਨਿੰਗ ਇਨਫਰੈਂਸ ਨੂੰ ਵੱਖ-ਵੱਖ ਉਪਯੋਗ ਕੇਸਾਂ ਵਿੱਚ ਤੇਜ਼ ਕਰਦਾ ਹੈ, ਜਿਵੇਂ ਕਿ ਜਨਰੇਟਿਵ AI, ਵੀਡੀਓ, ਆਡੀਓ, ਅਤੇ ਭਾਸ਼ਾ, ਅਤੇ ਇਹ PyTorch, TensorFlow, ONNX ਅਤੇ ਹੋਰ ਮਸ਼ਹੂਰ ਫਰੇਮਵਰਕਾਂ ਦੇ ਮਾਡਲਾਂ ਨੂੰ ਸਪੋਰਟ ਕਰਦਾ ਹੈ। ਮਾਡਲਾਂ ਨੂੰ ਕਨਵਰਟ ਅਤੇ ਓਪਟੀਮਾਈਜ਼ ਕਰੋ ਅਤੇ ਵੱਖ-ਵੱਖ Intel® ਹਾਰਡਵੇਅਰ ਅਤੇ ਮਾਹੌਲਾਂ ਵਿੱਚ ਡਿਪਲੌਇ ਕਰੋ, ਚਾਹੇ ਉਹ ਓਨ-ਪ੍ਰੇਮਿਸ ਹੋਵੇ ਜਾਂ ਓਨ-ਡਿਵਾਈਸ, ਬ੍ਰਾਊਜ਼ਰ ਵਿੱਚ ਜਾਂ ਕਲਾਉਡ ਵਿੱਚ।

ਹੁਣ OpenVINO ਨਾਲ, ਤੁਸੀਂ Intel ਹਾਰਡਵੇਅਰ ਵਿੱਚ ਜਨਰੇਟਿਵ AI ਮਾਡਲ ਨੂੰ ਤੇਜ਼ੀ ਨਾਲ ਕਵਾਂਟਾਈਜ਼ ਕਰ ਸਕਦੇ ਹੋ ਅਤੇ ਮਾਡਲ ਰਿਫਰੈਂਸ ਨੂੰ ਤੇਜ਼ ਕਰ ਸਕਦੇ ਹੋ।  

ਹੁਣ OpenVINO Phi-3.5-Vision ਅਤੇ Phi-3.5 Instruct ਦੀ ਕਵਾਂਟਾਈਜ਼ੇਸ਼ਨ ਕਨਵਰਜ਼ਨ ਸਪੋਰਟ ਕਰਦਾ ਹੈ।  

### **ਮਾਹੌਲ ਸੈਟਅੱਪ**

ਕਿਰਪਾ ਕਰਕੇ ਇਹ ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਹੇਠਾਂ ਦਿੱਤੀਆਂ ਮਾਹੌਲ ਡਿਪੈਂਡੈਂਸੀਜ਼ ਇੰਸਟਾਲ ਕੀਤੀਆਂ ਗਈਆਂ ਹਨ, ਇਹ ਹੈ `requirement.txt`  

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **OpenVINO ਦੀ ਵਰਤੋਂ ਨਾਲ Phi-3.5-Instruct ਨੂੰ ਕਵਾਂਟਾਈਜ਼ ਕਰਨਾ**

ਟਰਮੀਨਲ ਵਿੱਚ, ਕਿਰਪਾ ਕਰਕੇ ਇਹ ਸਕ੍ਰਿਪਟ ਚਲਾਓ  

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **OpenVINO ਦੀ ਵਰਤੋਂ ਨਾਲ Phi-3.5-Vision ਨੂੰ ਕਵਾਂਟਾਈਜ਼ ਕਰਨਾ**

ਕਿਰਪਾ ਕਰਕੇ ਇਸ ਸਕ੍ਰਿਪਟ ਨੂੰ Python ਜਾਂ Jupyter ਲੈਬ ਵਿੱਚ ਚਲਾਓ  

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

### **🤖 Intel OpenVINO ਨਾਲ Phi-3.5 ਲਈ ਨਮੂਨੇ**

| ਲੈਬਸ    | ਜਾਣ ਪਛਾਣ | ਜਾਓ |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | ਜਾਣੋ ਕਿ ਆਪਣੀ AI PC ਵਿੱਚ Phi-3.5 Instruct ਨੂੰ ਕਿਵੇਂ ਵਰਤਣਾ ਹੈ    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | ਜਾਣੋ ਕਿ ਆਪਣੀ AI PC ਵਿੱਚ ਤਸਵੀਰਾਂ ਦਾ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰਨ ਲਈ Phi-3.5 Vision ਨੂੰ ਕਿਵੇਂ ਵਰਤਣਾ ਹੈ      |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (video)   | ਜਾਣੋ ਕਿ ਆਪਣੀ AI PC ਵਿੱਚ ਵੀਡੀਓ ਦਾ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰਨ ਲਈ Phi-3.5 Vision ਨੂੰ ਕਿਵੇਂ ਵਰਤਣਾ ਹੈ    |  [Go](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |

## **ਸਰੋਤ**

1. Intel OpenVINO ਬਾਰੇ ਹੋਰ ਜਾਣੋ [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub Repo [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)  

**ਪ੍ਰਤੀਖਿਆ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ-ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਪਨ ਲਈ ਪ੍ਰਯਾਸ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਆਟੋਮੇਟਿਕ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਵਿਧਾਵਾਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਇਸ ਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਮੌਜੂਦ ਮੂਲ ਦਸਤਾਵੇਜ਼ ਨੂੰ ਅਧਿਕਾਰਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਅਸੀਂ ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਈਆਂ ਕਿਸੇ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।