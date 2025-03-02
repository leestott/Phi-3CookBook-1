# **Intel OpenVINO를 사용한 Phi-3.5 양자화**

Intel은 많은 사용자를 보유한 가장 전통적인 CPU 제조업체입니다. 머신 러닝과 딥 러닝의 부상으로 Intel도 AI 가속 경쟁에 합류했습니다. 모델 추론을 위해 Intel은 GPU와 CPU뿐만 아니라 NPU도 사용합니다.

우리는 Phi-3.x 패밀리를 엣지 디바이스에 배포하여 AI PC와 Copilot PC의 가장 중요한 부분이 되기를 희망합니다. 엣지 디바이스에서 모델을 로드하는 것은 다양한 하드웨어 제조업체의 협력에 달려 있습니다. 이 장에서는 Intel OpenVINO를 양자화 모델로 사용하는 응용 시나리오에 대해 중점적으로 다룹니다.

## **OpenVINO란 무엇인가**

OpenVINO는 클라우드에서 엣지까지 딥 러닝 모델을 최적화하고 배포하기 위한 오픈 소스 툴킷입니다. PyTorch, TensorFlow, ONNX 등 인기 있는 프레임워크의 모델을 활용하여 생성 AI, 비디오, 오디오, 언어와 같은 다양한 사용 사례에서 딥 러닝 추론을 가속화합니다. 모델을 변환하고 최적화하며, 온프레미스, 디바이스, 브라우저, 클라우드 등 다양한 Intel® 하드웨어와 환경에 배포할 수 있습니다.

OpenVINO를 사용하면 Intel 하드웨어에서 GenAI 모델을 빠르게 양자화하고 모델 참조를 가속화할 수 있습니다.

현재 OpenVINO는 Phi-3.5-Vision과 Phi-3.5 Instruct의 양자화 변환을 지원합니다.

### **환경 설정**

다음 환경 종속성이 설치되어 있는지 확인하세요. 이는 requirement.txt입니다.

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **OpenVINO를 사용한 Phi-3.5-Instruct 양자화**

터미널에서 이 스크립트를 실행하세요.

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **OpenVINO를 사용한 Phi-3.5-Vision 양자화**

Python 또는 Jupyter Lab에서 이 스크립트를 실행하세요.

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

### **🤖 Intel OpenVINO와 함께하는 Phi-3.5 샘플**

| 실험실   | 소개 | 이동 |
| -------- | ------- |  ------- |
| 🚀 Lab-Phi-3.5 Instruct 소개  | AI PC에서 Phi-3.5 Instruct를 사용하는 방법을 배워보세요.    |  [이동](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Lab-Phi-3.5 Vision (이미지) 소개 | AI PC에서 Phi-3.5 Vision을 사용하여 이미지를 분석하는 방법을 배워보세요.      |  [이동](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Lab-Phi-3.5 Vision (비디오) 소개   | AI PC에서 Phi-3.5 Vision을 사용하여 비디오를 분석하는 방법을 배워보세요.    |  [이동](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |

## **자료**

1. Intel OpenVINO에 대해 더 알아보기 [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Intel OpenVINO GitHub 저장소 [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**면책 조항**:  
이 문서는 기계 기반 AI 번역 서비스를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있지만, 자동 번역에는 오류나 부정확성이 포함될 수 있음을 유의하시기 바랍니다. 원어로 작성된 원본 문서를 신뢰할 수 있는 권위 있는 자료로 간주해야 합니다. 중요한 정보의 경우, 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.