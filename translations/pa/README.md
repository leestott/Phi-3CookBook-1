# ਫਾਈ ਕੁਕਬੁੱਕ: ਮਾਈਕਰੋਸਾਫਟ ਦੇ ਫਾਈ ਮਾਡਲਾਂ ਨਾਲ ਹਥਾਂ-ਵਿਚ ਕਸਰਤ

Phi ਮਾਈਕਰੋਸਾਫਟ ਦੁਆਰਾ ਵਿਕਸਤ ਖੁੱਲੇ ਸਰੋਤ ਵਾਲੇ AI ਮਾਡਲਾਂ ਦੀ ਇੱਕ ਸਿਰੀਜ਼ ਹੈ।  

Phi ਇਸ ਵੇਲੇ ਸਭ ਤੋਂ ਸ਼ਕਤੀਸ਼ਾਲੀ ਅਤੇ ਲਾਗਤ-ਪ੍ਰਭਾਵੀ ਛੋਟਾ ਭਾਸ਼ਾ ਮਾਡਲ (SLM) ਹੈ, ਜੋ ਬਹੁ-ਭਾਸ਼ਾ, ਤਰਕ, ਪਾਠ/ਗੱਲਬਾਤ ਪੈਦਾ ਕਰਨ, ਕੋਡਿੰਗ, ਚਿੱਤਰਾਂ, ਆਡੀਓ ਅਤੇ ਹੋਰ ਸਥਿਤੀਆਂ ਵਿੱਚ ਬਹੁਤ ਵਧੀਆ ਬੈਂਚਮਾਰਕ ਪ੍ਰਦਰਸ਼ਨ ਕਰਦਾ ਹੈ।  

ਤੁਸੀਂ Phi ਨੂੰ ਕਲਾਉਡ ਜਾਂ ਐਜ ਡਿਵਾਈਸਾਂ 'ਤੇ ਡਿਪਲੌਇ ਕਰ ਸਕਦੇ ਹੋ, ਅਤੇ ਤੁਸੀਂ ਘੱਟ ਕੰਪਿਊਟਿੰਗ ਪਾਵਰ ਨਾਲ ਜਨਰੇਟਿਵ AI ਐਪਲੀਕੇਸ਼ਨ ਆਸਾਨੀ ਨਾਲ ਬਣਾਉਣ ਲਈ ਇਸਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹੋ।  

ਇਹ ਸਰੋਤ ਵਰਤਣ ਦੀ ਸ਼ੁਰੂਆਤ ਕਰਨ ਲਈ ਹੇਠ ਲਿਖੇ ਕਦਮਾਂ ਦੀ ਪਾਲਣਾ ਕਰੋ:  
1. **ਰੇਪੋਜ਼ਟਰੀ ਫੋਰਕ ਕਰੋ**: ਕਲਿੱਕ ਕਰੋ [![GitHub forks](https://img.shields.io/github/forks/microsoft/phicookbook.svg?style=social&label=Fork)](https://GitHub.com/microsoft/phicookbook/network/?WT.mc_id=aiml-137032-kinfeylo)  
2. **ਰੇਪੋਜ਼ਟਰੀ ਕਲੋਨ ਕਰੋ**:   `git clone https://github.com/microsoft/PhiCookBook.git`  
3. [**ਮਾਈਕਰੋਸਾਫਟ AI ਡਿਸਕੋਰਡ ਕਮਿਊਨਿਟੀ ਵਿੱਚ ਸ਼ਾਮਲ ਹੋਵੋ ਅਤੇ ਮਾਹਿਰਾਂ ਅਤੇ ਹੋਰ ਡਿਵੈਲਪਰਾਂ ਨਾਲ ਮਿਲੋ**](https://discord.com/invite/ByRwuEEgH4?WT.mc_id=aiml-137032-kinfeylo)  

![cover](../../translated_images/cover.2595d43b382944c601aebf88583314636768eece3d94e8e4448e03a4e5bedef4.pa.png)

## ਸਮੱਗਰੀ ਦੀ ਸੂਚੀ

- ਪਰਚਿਆਵ  
  - [ਫਾਈ ਪਰਿਵਾਰ ਵਿੱਚ ਤੁਹਾਡਾ ਸਵਾਗਤ ਹੈ](./md/01.Introduction/01/01.PhiFamily.md)  
  - [ਆਪਣੇ ਮਾਹੌਲ ਦੀ ਸੈਟਿੰਗ](./md/01.Introduction/01/01.EnvironmentSetup.md)  
  - [ਮੁੱਖ ਤਕਨਾਲੋਜੀਆਂ ਨੂੰ ਸਮਝਣਾ](./md/01.Introduction/01/01.Understandingtech.md)  
  - [ਫਾਈ ਮਾਡਲਾਂ ਲਈ AI ਸੁਰੱਖਿਆ](./md/01.Introduction/01/01.AISafety.md)  
  - [ਫਾਈ ਹਾਰਡਵੇਅਰ ਸਹਾਇਤਾ](./md/01.Introduction/01/01.Hardwaresupport.md)  
  - [ਫਾਈ ਮਾਡਲ ਅਤੇ ਪਲੇਟਫਾਰਮਾਂ 'ਤੇ ਉਪਲਬਧਤਾ](./md/01.Introduction/01/01.Edgeandcloud.md)  
  - [Guidance-ai ਅਤੇ Phi ਦੀ ਵਰਤੋਂ](./md/01.Introduction/01/01.Guidance.md)  
  - [GitHub ਮਾਰਕੀਟਪਲੇਸ ਮਾਡਲ](https://github.com/marketplace/models)  
  - [Azure AI ਮਾਡਲ ਕੈਟਾਲਾਗ](https://ai.azure.com)  

- ਵੱਖਰੇ ਮਾਹੌਲ ਵਿੱਚ ਫਾਈ ਦਾ ਇੰਫਰੈਂਸ  
    -  [Hugging face](./md/01.Introduction/02/01.HF.md)  
    -  [GitHub ਮਾਡਲ](./md/01.Introduction/02/02.GitHubModel.md)  
    -  [Azure AI Foundry ਮਾਡਲ ਕੈਟਾਲਾਗ](./md/01.Introduction/02/03.AzureAIFoundry.md)  
    -  [Ollama](./md/01.Introduction/02/04.Ollama.md)  
    -  [AI Toolkit VSCode (AITK)](./md/01.Introduction/02/05.AITK.md)  
    -  [NVIDIA NIM](./md/01.Introduction/02/06.NVIDIA.md)  

- ਫਾਈ ਪਰਿਵਾਰ ਦਾ ਇੰਫਰੈਂਸ  
    - [iOS ਵਿੱਚ ਫਾਈ ਦਾ ਇੰਫਰੈਂਸ](./md/01.Introduction/03/iOS_Inference.md)  
    - [ਐਂਡਰਾਇਡ ਵਿੱਚ ਫਾਈ ਦਾ ਇੰਫਰੈਂਸ](./md/01.Introduction/03/Android_Inference.md)  
- [ਜੈਟਸਨ ਵਿੱਚ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Jetson_Inference.md)
    - [AI PC ਵਿੱਚ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/AIPC_Inference.md)
    - [ਐਪਲ MLX ਫਰੇਮਵਰਕ ਨਾਲ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/MLX_Inference.md)
    - [ਲੋਕਲ ਸਰਵਰ ਵਿੱਚ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Local_Server_Inference.md)
    - [AI ਟੂਲਕਿਟ ਵਰਤ ਕੇ ਰਿਮੋਟ ਸਰਵਰ ਵਿੱਚ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Remote_Interence.md)
    - [ਰਸਟ ਨਾਲ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Rust_Inference.md)
    - [ਲੋਕਲ ਵਿੱਚ ਫਾਈ-ਵਿਜ਼ਨ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Vision_Inference.md)
    - [ਕਾਈਟੋ AKS, ਐਜ਼ੂਰ ਕੰਟੇਨਰਜ਼ (ਆਧਿਕਾਰਿਕ ਸਹਾਇਤਾ) ਨਾਲ ਫਾਈ ਦਾ ਇਨਫਰੈਂਸ](./md/01.Introduction/03/Kaito_Inference.md)
- [ਫਾਈ ਪਰਿਵਾਰ ਦੀ ਮਾਤਰਾ ਨਿਰਧਾਰਤ ਕਰਨਾ](./md/01.Introduction/04/QuantifyingPhi.md)
    - [llama.cpp ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਫਾਈ-3.5 / 4 ਦੀ ਮਾਤਰਾ ਨਿਰਧਾਰਤ ਕਰਨਾ](./md/01.Introduction/04/UsingLlamacppQuantifyingPhi.md)
    - [onnxruntime ਲਈ ਜਨਰੇਟਿਵ AI ਐਕਸਟੈਂਸ਼ਨ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਫਾਈ-3.5 / 4 ਦੀ ਮਾਤਰਾ ਨਿਰਧਾਰਤ ਕਰਨਾ](./md/01.Introduction/04/UsingORTGenAIQuantifyingPhi.md)
    - [ਇੰਟੈਲ OpenVINO ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਫਾਈ-3.5 / 4 ਦੀ ਮਾਤਰਾ ਨਿਰਧਾਰਤ ਕਰਨਾ](./md/01.Introduction/04/UsingIntelOpenVINOQuantifyingPhi.md)
    - [ਐਪਲ MLX ਫਰੇਮਵਰਕ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਫਾਈ-3.5 / 4 ਦੀ ਮਾਤਰਾ ਨਿਰਧਾਰਤ ਕਰਨਾ](./md/01.Introduction/04/UsingAppleMLXQuantifyingPhi.md)

- ਫਾਈ ਦਾ ਮੁਲਾਂਕਣ
    - [ਜਵਾਬਦੇਹ AI](./md/01.Introduction/05/ResponsibleAI.md)
    - [ਮੁਲਾਂਕਣ ਲਈ ਐਜ਼ੂਰ AI ਫਾਉਂਡਰੀ](./md/01.Introduction/05/AIFoundry.md)
    - [ਮੁਲਾਂਕਣ ਲਈ ਪ੍ਰੌਮਪਟਫਲੋ ਦੀ ਵਰਤੋਂ](./md/01.Introduction/05/Promptflow.md)

- RAG ਐਜ਼ੂਰ AI ਸਰਚ ਨਾਲ
    - [ਐਜ਼ੂਰ AI ਸਰਚ ਨਾਲ ਫਾਈ-4-ਮਿਨੀ ਅਤੇ ਫਾਈ-4-ਮਲਟੀਮੋਡਲ (RAG) ਦੀ ਵਰਤੋਂ ਕਿਵੇਂ ਕਰਨੀ ਹੈ](https://github.com/microsoft/PhiCookBook/blob/main/code/06.E2E/E2E_Phi-4-RAG-Azure-AI-Search.ipynb)

- ਫਾਈ ਐਪਲੀਕੇਸ਼ਨ ਡਿਵੈਲਪਮੈਂਟ ਸੈਂਪਲ
  - ਟੈਕਸਟ ਅਤੇ ਚੈਟ ਐਪਲੀਕੇਸ਼ਨਜ਼
    - ਫਾਈ-4 ਸੈਂਪਲ 🆕
      - [📓] [ਫਾਈ-4-ਮਿਨੀ ONNX ਮਾਡਲ ਨਾਲ ਚੈਟ ਕਰੋ](./md/02.Application/01.TextAndChat/Phi4/ChatWithPhi4ONNX/README.md)
      - [ਫਾਈ-4 ਲੋਕਲ ONNX ਮਾਡਲ .NET ਨਾਲ ਚੈਟ ਕਰੋ](../../md/04.HOL/dotnet/src/LabsPhi4-Chat-01OnnxRuntime)
      - [ਸੈਮੈਂਟਿਕ ਕਰਨਲ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਫਾਈ-4 ONNX ਨਾਲ .NET ਕੰਸੋਲ ਐਪ ਵਿੱਚ ਚੈਟ ਕਰੋ](../../md/04.HOL/dotnet/src/LabsPhi4-Chat-02SK)
    - ਫਾਈ-3 / 3.5 ਸੈਂਪਲ
      - [ਬ੍ਰਾਊਜ਼ਰ ਵਿੱਚ ਫਾਈ3, ONNX ਰਨਟਾਈਮ ਵੈਬ ਅਤੇ ਵੈਬGPU ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਲੋਕਲ ਚੈਟਬੋਟ](https://github.com/microsoft/onnxruntime-inference-examples/tree/main/js/chat)
      - [OpenVINO ਚੈਟ](./md/02.Application/01.TextAndChat/Phi3/E2E_OpenVino_Chat.md)
      - [ਮਲਟੀ ਮਾਡਲ - ਇੰਟਰਐਕਟਿਵ ਫਾਈ-3-ਮਿਨੀ ਅਤੇ OpenAI ਵਿਸਪਰ](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-mini_with_whisper.md)
      - [MLFlow - ਇੱਕ ਰੈਪਰ ਬਣਾਉਣਾ ਅਤੇ MLFlow ਨਾਲ ਫਾਈ-3 ਦੀ ਵਰਤੋਂ](./md//02.Application/01.TextAndChat/Phi3/E2E_Phi-3-MLflow.md)
      - [ਮਾਡਲ ਅਪਟਿਮਾਈਜ਼ੇਸ਼ਨ - Olive ਦੀ ਵਰਤੋਂ ਕਰਕੇ ONNX ਰਨਟਾਈਮ ਵੈਬ ਲਈ ਫਾਈ-3-ਮਿਨ ਮਾਡਲ ਨੂੰ ਕਿਵੇਂ ਅਪਟਿਮਾਈਜ਼ ਕਰਨਾ ਹੈ](https://github.com/microsoft/Olive/tree/main/examples/phi3)
      - [ਫਾਈ-3 ਮਿਨੀ-4k-ਇਨਸਟਰੱਕਟ-ONNX ਨਾਲ WinUI3 ਐਪ](https://github.com/microsoft/Phi3-Chat-WinUI3-Sample/)
      - [WinUI3 ਮਲਟੀ ਮਾਡਲ AI ਪਾਵਰਡ ਨੋਟਸ ਐਪ ਸੈਂਪਲ](https://github.com/microsoft/ai-powered-notes-winui3-sample)
      - [ਕਸਟਮ ਫਾਈ-3 ਮਾਡਲਾਂ ਨੂੰ ਫਾਈਨ-ਟਿਊਨ ਅਤੇ ਪ੍ਰੌਮਪਟਫਲੋ ਨਾਲ ਇੰਟੀਗ੍ਰੇਟ ਕਰੋ](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-FineTuning_PromptFlow_Integration.md)
      - [ਐਜ਼ੂਰ AI ਫਾਉਂਡਰੀ ਵਿੱਚ ਕਸਟਮ ਫਾਈ-3 ਮਾਡਲਾਂ ਨੂੰ ਫਾਈਨ-ਟਿਊਨ ਅਤੇ ਪ੍ਰੌਮਪਟਫਲੋ ਨਾਲ ਇੰਟੀਗ੍ਰੇਟ ਕਰੋ](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-FineTuning_PromptFlow_Integration_AIFoundry.md)
      - [ਮਾਈਕਰੋਸਾਫਟ ਦੇ ਜਵਾਬਦੇਹ AI ਸਿਧਾਂਤਾਂ ਨੂੰ ਧਿਆਨ ਵਿੱਚ ਰੱਖਦਿਆਂ ਐਜ਼ੂਰ AI ਫਾਉਂਡਰੀ ਵਿੱਚ ਫਾਈਨ-ਟਿਊਨ ਕੀਤੇ ਫਾਈ-3 / ਫਾਈ-3.5 ਮਾਡਲ ਦਾ ਮੁਲਾਂਕਣ ਕਰੋ](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-Evaluation_AIFoundry.md)
- [📓] [Phi-3.5-mini-instruct ਭਾਸ਼ਾ ਅਨੁਮਾਨ ਨਮੂਨਾ (ਚੀਨੀ/ਅੰਗ੍ਰੇਜ਼ੀ)](../../md/02.Application/01.TextAndChat/Phi3/phi3-instruct-demo.ipynb)
      - [Phi-3.5-Instruct WebGPU RAG Chatbot](./md/02.Application/01.TextAndChat/Phi3/WebGPUWithPhi35Readme.md)
      - [Windows GPU ਦੀ ਵਰਤੋਂ ਕਰਕੇ Phi-3.5-Instruct ONNX ਨਾਲ Prompt Flow ਹੱਲ ਬਣਾਉਣਾ](./md/02.Application/01.TextAndChat/Phi3/UsingPromptFlowWithONNX.md)
      - [Microsoft Phi-3.5 tflite ਦੀ ਵਰਤੋਂ ਕਰਕੇ Android ਐਪ ਬਣਾਉਣਾ](./md/02.Application/01.TextAndChat/Phi3/UsingPhi35TFLiteCreateAndroidApp.md)
      - [ਸਥਾਨਕ ONNX Phi-3 ਮਾਡਲ ਦੀ ਵਰਤੋਂ ਕਰਕੇ Microsoft.ML.OnnxRuntime ਨਾਲ Q&A .NET ਉਦਾਹਰਨ](../../md/04.HOL/dotnet/src/LabsPhi301)
      - [Semantic Kernel ਅਤੇ Phi-3 ਨਾਲ Console Chat .NET ਐਪ](../../md/04.HOL/dotnet/src/LabsPhi302)

  - Azure AI Inference SDK ਕੋਡ ਅਧਾਰਿਤ ਨਮੂਨੇ 
    - Phi-4 ਨਮੂਨੇ 🆕
      - [📓] [Phi-4-multimodal ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਪ੍ਰੋਜੈਕਟ ਕੋਡ ਬਣਾਉਣਾ](./md/02.Application/02.Code/Phi4/GenProjectCode/README.md)
    - Phi-3 / 3.5 ਨਮੂਨੇ
      - [Microsoft Phi-3 ਪਰਿਵਾਰ ਨਾਲ ਆਪਣਾ Visual Studio Code GitHub Copilot Chat ਬਣਾਓ](./md/02.Application/02.Code/Phi3/VSCodeExt/README.md)
      - [GitHub ਮਾਡਲਾਂ ਦੁਆਰਾ Phi-3.5 ਨਾਲ ਆਪਣਾ Visual Studio Code Chat Copilot Agent ਬਣਾਓ](/md/02.Application/02.Code/Phi3/CreateVSCodeChatAgentWithGitHubModels.md)

  - ਉੱਚ ਸਤਰ ਦੀ ਦਲੀਲ ਦੇ ਨਮੂਨੇ
    - Phi-4 ਨਮੂਨੇ 🆕
      - [📓] [Phi-4-mini Reasoning ਨਮੂਨੇ](./md/02.Application/03.AdvancedReasoning/Phi4/AdvancedResoningPhi4mini/README.md)
  
  - ਡੈਮੋ
      - [Phi-4-mini ਡੈਮੋ Hugging Face Spaces 'ਤੇ ਹੋਸਟ ਕੀਤੇ ਗਏ](https://huggingface.co/spaces/microsoft/phi-4-mini?WT.mc_id=aiml-137032-kinfeylo)
      - [Phi-4-multimodal ਡੈਮੋ Hugging Face Spaces 'ਤੇ ਹੋਸਟ ਕੀਤੇ ਗਏ](https://huggingface.co/spaces/microsoft/phi-4-multimodal?WT.mc_id=aiml-137032-kinfeylo)
  - ਵਿਜ਼ਨ ਨਮੂਨੇ
    - Phi-4 ਨਮੂਨੇ 🆕
      - [📓] [Phi-4-multimodal ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਚਿੱਤਰ ਪੜ੍ਹੋ ਅਤੇ ਕੋਡ ਬਣਾਓ](./md/02.Application/04.Vision/Phi4/CreateFrontend/README.md) 
    - Phi-3 / 3.5 ਨਮੂਨੇ
      -  [📓][Phi-3-vision-ਚਿੱਤਰ ਟੈਕਸਟ ਤੋਂ ਟੈਕਸਟ](../../md/02.Application/04.Vision/Phi3/E2E_Phi-3-vision-image-text-to-text-online-endpoint.ipynb)
      - [Phi-3-vision-ONNX](https://onnxruntime.ai/docs/genai/tutorials/phi3-v.html)
      - [📓][Phi-3-vision CLIP Embedding](../../md/02.Application/04.Vision/Phi3/E2E_Phi-3-vision-image-text-to-text-online-endpoint.ipynb)
      - [ਡੈਮੋ: Phi-3 ਰੀਸਾਇਕਲਿੰਗ](https://github.com/jennifermarsman/PhiRecycling/)
      - [Phi-3-vision - ਵਿਜੁਅਲ ਭਾਸ਼ਾ ਸਹਾਇਕ - Phi3-Vision ਅਤੇ OpenVINO ਨਾਲ](https://docs.openvino.ai/nightly/notebooks/phi-3-vision-with-output.html)
      - [Phi-3 Vision Nvidia NIM](./md/02.Application/04.Vision/Phi3/E2E_Nvidia_NIM_Vision.md)
      - [Phi-3 Vision OpenVino](./md/02.Application/04.Vision/Phi3/E2E_OpenVino_Phi3Vision.md)
      - [📓][Phi-3.5 Vision ਬਹੁ-ਫ੍ਰੇਮ ਜਾਂ ਬਹੁ-ਚਿੱਤਰ ਨਮੂਨਾ](../../md/02.Application/04.Vision/Phi3/phi3-vision-demo.ipynb)
      - [Microsoft.ML.OnnxRuntime .NET ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਸਥਾਨਕ ONNX ਮਾਡਲ ਨਾਲ Phi-3 Vision](../../md/04.HOL/dotnet/src/LabsPhi303)
      - [Microsoft.ML.OnnxRuntime .NET ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਮੈਨੂ ਅਧਾਰਿਤ Phi-3 Vision ਸਥਾਨਕ ONNX ਮਾਡਲ](../../md/04.HOL/dotnet/src/LabsPhi304)

  - ਆਡੀਓ ਨਮੂਨੇ
    - Phi-4 ਨਮੂਨੇ 🆕
      - [📓] [Phi-4-multimodal ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਆਡੀਓ ਟ੍ਰਾਂਸਕ੍ਰਿਪਟ ਕੱਢਣਾ](./md/02.Application/05.Audio/Phi4/Transciption/README.md)
      - [📓] [Phi-4-multimodal ਆਡੀਓ ਨਮੂਨਾ](../../md/02.Application/05.Audio/Phi4/Siri/demo.ipynb)
      - [📓] [Phi-4-multimodal ਸਪੀਚ ਅਨੁਵਾਦ ਨਮੂਨਾ](../../md/02.Application/05.Audio/Phi4/Translate/demo.ipynb)
      - [.NET console ਐਪਲੀਕੇਸ਼ਨ Phi-4-multimodal ਆਡੀਓ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਆਡੀਓ ਫਾਈਲ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰਨ ਅਤੇ ਟ੍ਰਾਂਸਕ੍ਰਿਪਟ ਬਣਾਉਣ ਲਈ](../../md/04.HOL/dotnet/src/LabsPhi4-MultiModal-02Audio)

  - MOE ਨਮੂਨੇ
    - Phi-3 / 3.5 ਨਮੂਨੇ
      - [📓] [Phi-3.5 Mixture of Experts Models (MoEs) ਸੋਸ਼ਲ ਮੀਡੀਆ ਨਮੂਨਾ](../../md/02.Application/06.MoE/Phi3/phi3_moe_demo.ipynb)
      - [📓] [NVIDIA NIM Phi-3 MOE, Azure AI Search, ਅਤੇ LlamaIndex ਨਾਲ Retrieval-Augmented Generation (RAG) ਪਾਈਪਲਾਈਨ ਬਣਾਉਣਾ](../../md/02.Application/06.MoE/Phi3/azure-ai-search-nvidia-rag.ipynb)
  - ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਨਮੂਨੇ
    - Phi-4 ਨਮੂਨੇ 🆕
      -  [📓] [Phi-4-mini ਨਾਲ Function Calling ਦੀ ਵਰਤੋਂ](./md/02.Application/07.FunctionCalling/Phi4/FunctionCallingBasic/README.md)
  - Multimodal Mixing ਨਮੂਨੇ
    - Phi-4 ਨਮੂਨੇ 🆕
- [📓] [ਫਾਈ-4-ਮਲਟੀਮੋਡਲ ਨੂੰ ਤਕਨਾਲੋਜੀ ਪੱਤਰਕਾਰ ਵਜੋਂ ਵਰਤਣਾ](../../md/02.Application/08.Multimodel/Phi4/TechJournalist/phi_4_mm_audio_text_publish_news.ipynb)  
  - [.NET ਕਨਸੋਲ ਐਪਲੀਕੇਸ਼ਨ ਫਾਈ-4-ਮਲਟੀਮੋਡਲ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਚਿੱਤਰਾਂ ਦਾ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰਦੀ ਹੈ](../../md/04.HOL/dotnet/src/LabsPhi4-MultiModal-01Images)

- ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ ਸੈਂਪਲਜ਼  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਸਿਥੀ](./md/03.FineTuning/FineTuning_Scenarios.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਵਿਰੁੱਧ RAG](./md/03.FineTuning/FineTuning_vs_RAG.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ: ਫਾਈ-3 ਨੂੰ ਉਦਯੋਗ ਦਾ ਮਾਹਿਰ ਬਣਾਉਣਾ](./md/03.FineTuning/LetPhi3gotoIndustriy.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: VS Code ਲਈ AI ਟੂਲਕਿਟ ਦੀ ਵਰਤੋਂ](./md/03.FineTuning/Finetuning_VSCodeaitoolkit.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: Azure Machine Learning Service ਨਾਲ](./md/03.FineTuning/Introduce_AzureML.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: Lora ਦੀ ਵਰਤੋਂ ਨਾਲ](./md/03.FineTuning/FineTuning_Lora.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: QLora ਨਾਲ](./md/03.FineTuning/FineTuning_Qlora.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: Azure AI Foundry ਨਾਲ](./md/03.FineTuning/FineTuning_AIFoundry.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: Azure ML CLI/SDK ਨਾਲ](./md/03.FineTuning/FineTuning_MLSDK.md)  
  - [ਮਾਈਕਰੋਸਾਫਟ ਓਲਿਵ ਨਾਲ ਫਾਈਨ-ਟਿਊਨਿੰਗ](./md/03.FineTuning/FineTuning_MicrosoftOlive.md)  
  - [ਮਾਈਕਰੋਸਾਫਟ ਓਲਿਵ ਹੈਂਡਸ-ਆਨ ਲੈਬ ਨਾਲ ਫਾਈਨ-ਟਿਊਨਿੰਗ](./md/03.FineTuning/olive-lab/readme.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3-ਵਿਜ਼ਨ: Weights ਅਤੇ Bias ਨਾਲ](./md/03.FineTuning/FineTuning_Phi-3-visionWandB.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3: Apple MLX Framework ਨਾਲ](./md/03.FineTuning/FineTuning_MLX.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3-ਵਿਜ਼ਨ (ਆਧਿਕਾਰਿਕ ਸਹਿਯੋਗ)](./md/03.FineTuning/FineTuning_Vision.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3 ਅਤੇ Kaito AKS, Azure Containers (ਆਧਿਕਾਰਿਕ ਸਹਿਯੋਗ)](./md/03.FineTuning/FineTuning_Kaito.md)  
  - [ਫਾਈਨ-ਟਿਊਨਿੰਗ ਫਾਈ-3 ਅਤੇ 3.5 ਵਿਜ਼ਨ](https://github.com/2U1/Phi3-Vision-Finetune)

- ਹੈਂਡਸ-ਆਨ ਲੈਬ  
  - [ਨਵੇਂ ਮਾਡਲਾਂ ਦੀ ਖੋਜ: LLMs, SLMs, ਸਥਾਨਕ ਵਿਕਾਸ ਅਤੇ ਹੋਰ](https://github.com/microsoft/aitour-exploring-cutting-edge-models)  
  - [NLP ਦੀ ਸਮਰਥਾ ਖੋਲ੍ਹਣਾ: ਮਾਈਕਰੋਸਾਫਟ ਓਲਿਵ ਨਾਲ ਫਾਈਨ-ਟਿਊਨਿੰਗ](https://github.com/azure/Ignite_FineTuning_workshop)

- ਅਕਾਦਮਿਕ ਖੋਜ ਪੇਪਰ ਅਤੇ ਪ੍ਰਕਾਸ਼ਨ  
  - [Textbooks Are All You Need II: ਫਾਈ-1.5 ਤਕਨੀਕੀ ਰਿਪੋਰਟ](https://arxiv.org/abs/2309.05463)  
  - [ਫਾਈ-3 ਤਕਨੀਕੀ ਰਿਪੋਰਟ: ਤੁਹਾਡੇ ਫ਼ੋਨ ਤੇ ਸਥਾਨਕ ਤੌਰ ਤੇ ਇਕ ਬਹੁਤ ਸਮਰੱਥ ਭਾਸ਼ਾ ਮਾਡਲ](https://arxiv.org/abs/2404.14219)  
  - [ਫਾਈ-4 ਤਕਨੀਕੀ ਰਿਪੋਰਟ](https://arxiv.org/abs/2412.08905)  
  - [ਛੋਟੇ ਭਾਸ਼ਾ ਮਾਡਲਾਂ ਨੂੰ ਵਾਹਨ-ਅੰਦਰ ਫੰਕਸ਼ਨ-ਕਾਲਿੰਗ ਲਈ ਅਨੁਕੂਲਿਤ ਕਰਨਾ](https://arxiv.org/abs/2501.02342)  
  - [(WhyPHI) ਫਾਈ-3 ਨੂੰ Multiple-Choice ਪ੍ਰਸ਼ਨ ਜਵਾਬ ਲਈ ਫਾਈਨ-ਟਿਊਨ ਕਰਨਾ: ਢੰਗ, ਨਤੀਜੇ, ਅਤੇ ਚੁਣੌਤੀਆਂ](https://arxiv.org/abs/2501.01588)

## ਫਾਈ ਮਾਡਲਾਂ ਦੀ ਵਰਤੋਂ

### Azure AI Foundry 'ਤੇ ਫਾਈ

ਤੁਸੀਂ ਮਾਈਕਰੋਸਾਫਟ ਫਾਈ ਦੀ ਵਰਤੋਂ ਅਤੇ ਵੱਖ-ਵੱਖ ਹਾਰਡਵੇਅਰ ਡਿਵਾਈਸਾਂ ਲਈ E2E ਹੱਲ ਬਣਾਉਣ ਬਾਰੇ ਸਿੱਖ ਸਕਦੇ ਹੋ। ਫਾਈ ਨੂੰ ਖੁਦ ਅਨੁਭਵ ਕਰਨ ਲਈ, ਮਾਡਲਾਂ ਨਾਲ ਖੇਡਣਾ ਸ਼ੁਰੂ ਕਰੋ ਅਤੇ ਆਪਣੀਆਂ ਜ਼ਰੂਰਤਾਂ ਲਈ ਫਾਈ ਨੂੰ ਕਸਟਮਾਈਜ਼ ਕਰੋ। [Azure AI Foundry Azure AI Model Catalog](https://aka.ms/phi3-azure-ai) ਵਿੱਚ ਜਾਓ। ਹੋਰ ਜਾਣਕਾਰੀ ਲਈ, [Azure AI Foundry ਸ਼ੁਰੂਆਤ](./md/02.QuickStart/AzureAIFoundry_QuickStart.md) ਦੇਖੋ।

**ਪਲੇਗ੍ਰਾਊਂਡ**  
ਹਰ ਮਾਡਲ ਲਈ ਇੱਕ ਖਾਸ ਪਲੇਗ੍ਰਾਊਂਡ ਹੈ ਜਿਸ ਵਿੱਚ ਤੁਸੀਂ ਟੈਸਟ ਕਰ ਸਕਦੇ ਹੋ: [Azure AI Playground](https://aka.ms/try-phi3)।

### GitHub ਮਾਡਲਾਂ 'ਤੇ ਫਾਈ

ਤੁਸੀਂ ਮਾਈਕਰੋਸਾਫਟ ਫਾਈ ਦੀ ਵਰਤੋਂ ਅਤੇ ਵੱਖ-ਵੱਖ ਹਾਰਡਵੇਅਰ ਡਿਵਾਈਸਾਂ ਲਈ E2E ਹੱਲ ਬਣਾਉਣ ਬਾਰੇ ਸਿੱਖ ਸਕਦੇ ਹੋ। ਫਾਈ ਨੂੰ ਖੁਦ ਅਨੁਭਵ ਕਰਨ ਲਈ, ਮਾਡਲ ਨਾਲ ਖੇਡਣਾ ਸ਼ੁਰੂ ਕਰੋ ਅਤੇ ਆਪਣੀਆਂ ਜ਼ਰੂਰਤਾਂ ਲਈ ਫਾਈ ਨੂੰ ਕਸਟਮਾਈਜ਼ ਕਰੋ। [GitHub Model Catalog](https://github.com/marketplace/models?WT.mc_id=aiml-137032-kinfeylo) ਵਿੱਚ ਜਾਓ। ਹੋਰ ਜਾਣਕਾਰੀ ਲਈ, [GitHub Model Catalog ਸ਼ੁਰੂਆਤ](./md/02.QuickStart/GitHubModel_QuickStart.md) ਦੇਖੋ।

**ਪਲੇਗ੍ਰਾਊਂਡ**  
ਹਰ ਮਾਡਲ ਲਈ ਇੱਕ ਖਾਸ [ਮਾਡਲ ਟੈਸਟ ਕਰਨ ਲਈ ਖੇਡ ਦਾ ਮੈਦਾਨ](/md/02.QuickStart/GitHubModel_QuickStart.md) ਉਪਲਬਧ ਹੈ।

### Hugging Face 'ਤੇ Phi

ਤੁਸੀਂ ਮਾਡਲ ਨੂੰ [Hugging Face](https://huggingface.co/microsoft) 'ਤੇ ਵੀ ਲੱਭ ਸਕਦੇ ਹੋ।

**ਖੇਡ ਦਾ ਮੈਦਾਨ**  
[Hugging Chat ਖੇਡ ਦਾ ਮੈਦਾਨ](https://huggingface.co/chat/models/microsoft/Phi-3-mini-4k-instruct)

## ਜ਼ਿੰਮੇਵਾਰ AI

Microsoft ਆਪਣੇ ਗਾਹਕਾਂ ਦੀ ਮਦਦ ਕਰਨ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਢੰਗ ਨਾਲ AI ਉਤਪਾਦ ਵਰਤਣ ਵਿੱਚ ਵਚਨਬੱਧ ਹੈ। ਅਸੀਂ ਆਪਣੇ ਸਿੱਖਣਾਂ ਨੂੰ ਸਾਂਝਾ ਕਰਦੇ ਹਾਂ ਅਤੇ ਭਰੋਸੇਮੰਦ ਸਾਥਾਂ ਦੀ ਰਚਨਾ ਕਰਨ ਲਈ Transparency Notes ਅਤੇ Impact Assessments ਵਰਗੇ ਟੂਲਾਂ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹਾਂ। ਇਹ ਸਾਧਨ ਬਹੁਤ ਸਾਰੇ [https://aka.ms/RAI](https://aka.ms/RAI) 'ਤੇ ਲੱਭੇ ਜਾ ਸਕਦੇ ਹਨ।  
Microsoft ਦਾ ਜ਼ਿੰਮੇਵਾਰ AI ਲਈ ਰਵੱਈਆ ਸਾਡੇ AI ਦੇ ਸਿਧਾਂਤਾਂ 'ਤੇ ਅਧਾਰਿਤ ਹੈ: ਨਿਆਂਸੰਗਤਾ, ਭਰੋਸੇਯੋਗਤਾ ਅਤੇ ਸੁਰੱਖਿਆ, ਗੋਪਨੀਯਤਾ ਅਤੇ ਸੁਰੱਖਿਆ, ਸ਼ਾਮਿਲਤਾ, ਪਾਰਦਰਸ਼ਤਾ, ਅਤੇ ਜਵਾਬਦੇਹੀ।

ਵੱਡੇ ਪੈਮਾਨੇ ਦੇ ਕੁਦਰਤੀ ਭਾਸ਼ਾ, ਚਿੱਤਰ, ਅਤੇ ਬੋਲਣ ਵਾਲੇ ਮਾਡਲ - ਜਿਵੇਂ ਕਿ ਇਸ ਨਮੂਨੇ ਵਿੱਚ ਵਰਤੇ ਗਏ ਹਨ - ਕਈ ਵਾਰ ਅਨਿਆਇਕ, ਅਭਰੋਸੇਯੋਗ ਜਾਂ ਨੁਕਸਾਨਦਾਇਕ ਢੰਗ ਨਾਲ ਵਤੀਰਾ ਕਰ ਸਕਦੇ ਹਨ। ਇਸ ਨਾਲ ਨੁਕਸਾਨ ਹੋ ਸਕਦਾ ਹੈ। ਕਿਰਪਾ ਕਰਕੇ [Azure OpenAI ਸੇਵਾ Transparency note](https://learn.microsoft.com/legal/cognitive-services/openai/transparency-note?tabs=text) ਨੂੰ ਵੇਖੋ ਤਾਂ ਜੋ ਜੋਖਮਾਂ ਅਤੇ ਸੀਮਾਵਾਂ ਬਾਰੇ ਜਾਣਕਾਰੀ ਮਿਲੇ।

ਇਹ ਜੋਖਮ ਘਟਾਉਣ ਲਈ ਸਿਫਾਰਸ਼ੀ ਤਰੀਕਾ ਇਹ ਹੈ ਕਿ ਆਪਣੇ ਆਰਕੀਟੈਕਚਰ ਵਿੱਚ ਇੱਕ ਸੁਰੱਖਿਆ ਪ੍ਰਣਾਲੀ ਸ਼ਾਮਿਲ ਕਰੋ ਜੋ ਨੁਕਸਾਨਦਾਇਕ ਵਤੀਰੇ ਦੀ ਪਛਾਣ ਕਰ ਸਕੇ ਅਤੇ ਰੋਕ ਸਕੇ। [Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) ਇੱਕ ਸਵਤੰਤਰ ਸੁਰੱਖਿਆ ਲੇਅਰ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ ਜੋ ਐਪਲੀਕੇਸ਼ਨਾਂ ਅਤੇ ਸੇਵਾਵਾਂ ਵਿੱਚ ਉਪਭੋਗਤਾ ਜਾਂ AI ਦੁਆਰਾ ਬਣਾਈ ਗਈ ਨੁਕਸਾਨਦਾਇਕ ਸਮੱਗਰੀ ਦੀ ਪਛਾਣ ਕਰ ਸਕਦਾ ਹੈ। Azure AI Content Safety ਵਿੱਚ ਟੈਕਸਟ ਅਤੇ ਚਿੱਤਰ APIs ਸ਼ਾਮਿਲ ਹਨ ਜੋ ਤੁਹਾਨੂੰ ਨੁਕਸਾਨਦਾਇਕ ਸਮੱਗਰੀ ਦੀ ਪਛਾਣ ਕਰਨ ਦੀ ਇਜਾਜ਼ਤ ਦਿੰਦੇ ਹਨ। Azure AI Foundry ਦੇ ਅੰਦਰ, Content Safety ਸੇਵਾ ਤੁਹਾਨੂੰ ਵੱਖ-ਵੱਖ ਮੋਡੈਲਿਟੀਜ਼ ਵਿੱਚ ਨੁਕਸਾਨਦਾਇਕ ਸਮੱਗਰੀ ਦਾ ਪਤਾ ਲਗਾਉਣ ਲਈ ਨਮੂਨਾ ਕੋਡ ਦੇਖਣ, ਖੋਜਣ ਅਤੇ ਅਜ਼ਮਾਉਣ ਦੀ ਸਹੂਲਤ ਦਿੰਦੀ ਹੈ। ਹੇਠਾਂ ਦਿੱਤੀ [quickstart documentation](https://learn.microsoft.com/azure/ai-services/content-safety/quickstart-text?tabs=visual-studio%2Clinux&pivots=programming-language-rest) ਤੁਹਾਨੂੰ ਸੇਵਾ ਲਈ ਬੇਨਤੀ ਭੇਜਣ ਦਾ ਤਰੀਕਾ ਦਿਖਾਉਂਦੀ ਹੈ।

ਇੱਕ ਹੋਰ ਪਹਲੂ ਜੋ ਧਿਆਨ ਵਿੱਚ ਰੱਖਣ ਯੋਗ ਹੈ ਉਹ ਹੈ ਸਮੁੱਚੀ ਐਪਲੀਕੇਸ਼ਨ ਪ੍ਰਦਰਸ਼ਨ। ਮਲਟੀ-ਮੋਡਲ ਅਤੇ ਮਲਟੀ-ਮਾਡਲ ਐਪਲੀਕੇਸ਼ਨਾਂ ਦੇ ਨਾਲ, ਅਸੀਂ ਪ੍ਰਦਰਸ਼ਨ ਦਾ ਅਰਥ ਇਹ ਲੈਂਦੇ ਹਾਂ ਕਿ ਪ੍ਰਣਾਲੀ ਤੁਹਾਡੇ ਅਤੇ ਤੁਹਾਡੇ ਉਪਭੋਗਤਾਵਾਂ ਦੀ ਉਮੀਦਾਂ ਦੇ ਅਨੁਸਾਰ ਕੰਮ ਕਰਦੀ ਹੈ, ਜਿਸ ਵਿੱਚ ਨੁਕਸਾਨਦਾਇਕ ਨਤੀਜੇ ਪੈਦਾ ਨਾ ਕਰਨਾ ਸ਼ਾਮਿਲ ਹੈ। ਆਪਣੇ ਸਮੁੱਚੇ ਐਪਲੀਕੇਸ਼ਨ ਦੇ ਪ੍ਰਦਰਸ਼ਨ ਦਾ ਮੁਲਾਂਕਨ ਕਰਨ ਲਈ ਇਹ ਮਹੱਤਵਪੂਰਨ ਹੈ ਕਿ [Performance and Quality and Risk and Safety evaluators](https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-metrics-built-in) ਦੀ ਵਰਤੋਂ ਕੀਤੀ ਜਾਵੇ। ਤੁਸੀਂ [custom evaluators](https://learn.microsoft.com/azure/ai-studio/how-to/develop/evaluate-sdk#custom-evaluators) ਬਣਾਉਣ ਅਤੇ ਅੰਕਣ ਕਰਨ ਦੀ ਸਮਰੱਥਾ ਵੀ ਰੱਖਦੇ ਹੋ।

ਤੁਸੀਂ ਆਪਣੇ ਵਿਕਾਸ ਵਾਲੇ ਮਾਹੌਲ ਵਿੱਚ [Azure AI Evaluation SDK](https://microsoft.github.io/promptflow/index.html) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਆਪਣੀ AI ਐਪਲੀਕੇਸ਼ਨ ਦਾ ਮੁਲਾਂਕਨ ਕਰ ਸਕਦੇ ਹੋ। ਇੱਕ ਟੈਸਟ ਡਾਟਾਸੈਟ ਜਾਂ ਟਾਰਗਟ ਦੇ ਨਾਲ, ਤੁਹਾਡੀ ਜਨਰੇਟਿਵ AI ਐਪਲੀਕੇਸ਼ਨ ਦੇ ਨਤੀਜੇ ਬਿਲਟ-ਇਨ ਜਾਂ ਤੁਹਾਡੇ ਚੋਣ ਦੇ custom evaluators ਨਾਲ ਮਾਪੇ ਜਾਂਦੇ ਹਨ। ਆਪਣੇ ਸਿਸਟਮ ਦਾ ਮੁਲਾਂਕਨ ਕਰਨ ਲਈ Azure AI Evaluation SDK ਨਾਲ ਸ਼ੁਰੂਆਤ ਕਰਨ ਲਈ, ਤੁਸੀਂ [quickstart guide](https://learn.microsoft.com/azure/ai-studio/how-to/develop/flow-evaluate-sdk) ਨੂੰ ਫੋਲੋ ਕਰ ਸਕਦੇ ਹੋ। ਜਦੋਂ ਤੁਸੀਂ ਇੱਕ ਅੰਕਣ ਚਲਾਉਂਦੇ ਹੋ, ਤਾਂ ਤੁਸੀਂ [Azure AI Foundry ਵਿੱਚ ਨਤੀਜੇ ਵੇਖ ਸਕਦੇ ਹੋ](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-flow-results)।

## ਟ੍ਰੇਡਮਾਰਕਸ

ਇਹ ਪ੍ਰੋਜੈਕਟ ਪ੍ਰੋਜੈਕਟਾਂ, ਉਤਪਾਦਾਂ ਜਾਂ ਸੇਵਾਵਾਂ ਲਈ ਟ੍ਰੇਡਮਾਰਕ ਜਾਂ ਲੋਗੋ ਸ਼ਾਮਿਲ ਕਰ ਸਕਦਾ ਹੈ। Microsoft ਟ੍ਰੇਡਮਾਰਕਸ ਜਾਂ ਲੋਗੋਜ਼ ਦੀ ਅਧਿਕ੍ਰਿਤ ਵਰਤੋਂ [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general) ਦੇ ਅਨੁਸਾਰ ਹੋਣੀ ਚਾਹੀਦੀ ਹੈ।  
ਇਸ ਪ੍ਰੋਜੈਕਟ ਦੇ ਸੋਧੇ ਹੋਏ ਸੰਸਕਰਣਾਂ ਵਿੱਚ Microsoft ਟ੍ਰੇਡਮਾਰਕਸ ਜਾਂ ਲੋਗੋਜ਼ ਦੀ ਵਰਤੋਂ ਗਲਤਫਹਮੀ ਪੈਦਾ ਨਹੀਂ ਕਰਨੀ ਚਾਹੀਦੀ ਜਾਂ Microsoft ਦੇ ਸਪਾਂਸਰਸ਼ਿਪ ਦਾ ਸੰਕੇਤ ਨਹੀਂ ਦੇਣਾ ਚਾਹੀਦਾ। ਕਿਸੇ ਵੀ ਤੀਜੀ ਪੱਖ ਦੇ ਟ੍ਰੇਡਮਾਰਕਸ ਜਾਂ ਲੋਗੋਜ਼ ਦੀ ਵਰਤੋਂ ਉਹਨਾਂ ਤੀਜੀ ਪੱਖ ਦੀਆਂ ਨੀਤੀਆਂ ਦੇ ਅਧੀਨ ਹੈ।

**ਅਸਵੀਕਾਰਨਾ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ-ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦਿਤ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਲਈ ਯਤਨਸ਼ੀਲ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਜਾਗਰੂਕ ਰਹੋ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਚੱਜੇ ਪੱਖ ਹੋ ਸਕਦੇ ਹਨ। ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਮੂਲ ਦਸਤਾਵੇਜ਼ ਨੂੰ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਨਾਲ ਪੈਦਾ ਹੋਣ ਵਾਲੇ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।