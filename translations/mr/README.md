# Phi Cookbook: मायक्रोसॉफ्टच्या Phi मॉडेल्ससह प्रॅक्टिकल उदाहरणे

[![GitHub Codespaces मध्ये नमुने उघडा आणि वापरा](https://github.com/codespaces/badge.svg)](https://codespaces.new/microsoft/phicookbook)  
[![Dev Containers मध्ये उघडा](https://img.shields.io/static/v1?style=for-the-badge&label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/microsoft/phicookbook)

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/phicookbook.svg)](https://GitHub.com/microsoft/phicookbook/graphs/contributors/?WT.mc_id=aiml-137032-kinfeylo)  
[![GitHub issues](https://img.shields.io/github/issues/microsoft/phicookbook.svg)](https://GitHub.com/microsoft/phicookbook/issues/?WT.mc_id=aiml-137032-kinfeylo)  
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/phicookbook.svg)](https://GitHub.com/microsoft/phicookbook/pulls/?WT.mc_id=aiml-137032-kinfeylo)  
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com?WT.mc_id=aiml-137032-kinfeylo)  

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/phicookbook.svg?style=social&label=Watch)](https://GitHub.com/microsoft/phicookbook/watchers/?WT.mc_id=aiml-137032-kinfeylo)  
[![GitHub forks](https://img.shields.io/github/forks/microsoft/phicookbook.svg?style=social&label=Fork)](https://GitHub.com/microsoft/phicookbook/network/?WT.mc_id=aiml-137032-kinfeylo)  
[![GitHub stars](https://img.shields.io/github/stars/microsoft/phicookbook?style=social&label=Star)](https://GitHub.com/microsoft/phicookbook/stargazers/?WT.mc_id=aiml-137032-kinfeylo)  

[![Azure AI Community Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4?WT.mc_id=aiml-137032-kinfeylo)  

Phi हे मायक्रोसॉफ्टद्वारे विकसित केलेले एक ओपन सोर्स AI मॉडेल्सचे मालिकासंच आहे.  

Phi हे सध्या सर्वात प्रभावी आणि खर्चिकदृष्ट्या फायदेशीर लहान भाषा मॉडेल (SLM) आहे, ज्यामध्ये बहुभाषिकता, तर्कशक्ती, मजकूर/चॅट निर्मिती, कोडिंग, प्रतिमा, ऑडिओ आणि इतर विविध गोष्टींसाठी उत्कृष्ट कामगिरी आहे.  

Phi ला क्लाउड किंवा एज डिव्हाइसेसवर तैनात करता येते आणि मर्यादित संगणकीय क्षमतेसह जनरेटिव्ह AI अॅप्लिकेशन्स सहजपणे तयार करता येतात.  

या संसाधनांचा वापर सुरू करण्यासाठी खालील पायऱ्या फॉलो करा:
1. **रेपॉझिटरी फोर्क करा**: [![GitHub forks](https://img.shields.io/github/forks/microsoft/phicookbook.svg?style=social&label=Fork)](https://GitHub.com/microsoft/phicookbook/network/?WT.mc_id=aiml-137032-kinfeylo) वर क्लिक करा  
2. **रेपॉझिटरी क्लोन करा**: `git clone https://github.com/microsoft/PhiCookBook.git`  
3. [**मायक्रोसॉफ्ट AI डिस्कॉर्ड कम्युनिटीमध्ये सामील व्हा आणि तज्ञ व इतर डेव्हलपर्सशी चर्चा करा**](https://discord.com/invite/ByRwuEEgH4?WT.mc_id=aiml-137032-kinfeylo)  

![cover](../../translated_images/cover.2595d43b382944c601aebf88583314636768eece3d94e8e4448e03a4e5bedef4.mr.png)

## विषय सूची

- परिचय  
  - [Phi कुटुंबामध्ये स्वागत आहे](./md/01.Introduction/01/01.PhiFamily.md)  
  - [तुमचे वातावरण सेट करणे](./md/01.Introduction/01/01.EnvironmentSetup.md)  
  - [महत्त्वाच्या तंत्रज्ञानाची समज](./md/01.Introduction/01/01.Understandingtech.md)  
  - [Phi मॉडेल्ससाठी AI सुरक्षा](./md/01.Introduction/01/01.AISafety.md)  
  - [Phi हार्डवेअर समर्थन](./md/01.Introduction/01/01.Hardwaresupport.md)  
  - [Phi मॉडेल्स आणि प्लॅटफॉर्म्सवरील उपलब्धता](./md/01.Introduction/01/01.Edgeandcloud.md)  
  - [Guidance-ai आणि Phi चा वापर](./md/01.Introduction/01/01.Guidance.md)  
  - [GitHub मार्केटप्लेस मॉडेल्स](https://github.com/marketplace/models)  
  - [Azure AI मॉडेल कॅटलॉग](https://ai.azure.com)  

- विविध वातावरणात Phi चा वापर  
    - [Hugging face](./md/01.Introduction/02/01.HF.md)  
    - [GitHub मॉडेल्स](./md/01.Introduction/02/02.GitHubModel.md)  
    - [Azure AI Foundry मॉडेल कॅटलॉग](./md/01.Introduction/02/03.AzureAIFoundry.md)  
    - [Ollama](./md/01.Introduction/02/04.Ollama.md)  
    - [AI Toolkit VSCode (AITK)](./md/01.Introduction/02/05.AITK.md)  
    - [NVIDIA NIM](./md/01.Introduction/02/06.NVIDIA.md)  

- Phi कुटुंबाचा वापर  
    - [iOS मध्ये Phi चा वापर](./md/01.Introduction/03/iOS_Inference.md)  
    - [Android मध्ये Phi चा वापर](./md/01.Introduction/03/Android_Inference.md)  
- [Jetson मध्ये Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Jetson_Inference.md)
    - [AI PC मध्ये Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/AIPC_Inference.md)
    - [Apple MLX Framework सह Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/MLX_Inference.md)
    - [स्थानिक सर्व्हरवर Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Local_Server_Inference.md)
    - [AI Toolkit वापरून रिमोट सर्व्हरवर Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Remote_Interence.md)
    - [Rust सह Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Rust_Inference.md)
    - [स्थानिक Vision सह Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Vision_Inference.md)
    - [Kaito AKS, Azure Containers (अधिकृत समर्थन) सह Phi ची अंदाज वर्तविणे](./md/01.Introduction/03/Kaito_Inference.md)

- [Phi कुटुंबाचे प्रमाणन](./md/01.Introduction/04/QuantifyingPhi.md)
    - [llama.cpp वापरून Phi-3.5 / 4 चे प्रमाणन](./md/01.Introduction/04/UsingLlamacppQuantifyingPhi.md)
    - [onnxruntime साठी जनरेटिव AI विस्तार वापरून Phi-3.5 / 4 चे प्रमाणन](./md/01.Introduction/04/UsingORTGenAIQuantifyingPhi.md)
    - [Intel OpenVINO वापरून Phi-3.5 / 4 चे प्रमाणन](./md/01.Introduction/04/UsingIntelOpenVINOQuantifyingPhi.md)
    - [Apple MLX Framework वापरून Phi-3.5 / 4 चे प्रमाणन](./md/01.Introduction/04/UsingAppleMLXQuantifyingPhi.md)

- Phi चे मूल्यमापन
    - [उत्तरदायी AI](./md/01.Introduction/05/ResponsibleAI.md)
    - [मूल्यमापनासाठी Azure AI Foundry](./md/01.Introduction/05/AIFoundry.md)
    - [मूल्यमापनासाठी Promptflow वापरणे](./md/01.Introduction/05/Promptflow.md)

- Azure AI Search सह RAG
    - [Azure AI Search सह Phi-4-mini आणि Phi-4-multimodal (RAG) कसे वापरावे](https://github.com/microsoft/PhiCookBook/blob/main/code/06.E2E/E2E_Phi-4-RAG-Azure-AI-Search.ipynb)

- Phi अनुप्रयोग विकास नमुने
  - मजकूर आणि चॅट अनुप्रयोग
    - Phi-4 नमुने 🆕
      - [📓] [Phi-4-mini ONNX मॉडेलसह चॅट](./md/02.Application/01.TextAndChat/Phi4/ChatWithPhi4ONNX/README.md)
      - [Phi-4 स्थानिक ONNX मॉडेल .NET सह चॅट](../../md/04.HOL/dotnet/src/LabsPhi4-Chat-01OnnxRuntime)
      - [Sementic Kernel वापरून Phi-4 ONNX सह .NET कन्सोल अॅप चॅट](../../md/04.HOL/dotnet/src/LabsPhi4-Chat-02SK)
    - Phi-3 / 3.5 नमुने
      - [Phi3, ONNX Runtime Web आणि WebGPU वापरून ब्राउझरमध्ये स्थानिक चॅटबॉट](https://github.com/microsoft/onnxruntime-inference-examples/tree/main/js/chat)
      - [OpenVino चॅट](./md/02.Application/01.TextAndChat/Phi3/E2E_OpenVino_Chat.md)
      - [मल्टी मॉडेल - Phi-3-mini आणि OpenAI Whisper यांच्यातील संवादात्मक अनुभव](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-mini_with_whisper.md)
      - [MLFlow - रॅपर तयार करणे आणि Phi-3 MLFlow सह वापरणे](./md//02.Application/01.TextAndChat/Phi3/E2E_Phi-3-MLflow.md)
      - [मॉडेल ऑप्टिमायझेशन - Olive वापरून ONNX Runtime Web साठी Phi-3-min मॉडेल ऑप्टिमाइझ कसे करावे](https://github.com/microsoft/Olive/tree/main/examples/phi3)
      - [Phi-3 mini-4k-instruct-onnx सह WinUI3 अॅप](https://github.com/microsoft/Phi3-Chat-WinUI3-Sample/)
      - [WinUI3 मल्टी मॉडेल AI संचालित नोट्स अॅप नमुना](https://github.com/microsoft/ai-powered-notes-winui3-sample)
      - [Prompt flow सह सानुकूल Phi-3 मॉडेल्स फाइन-ट्यून करणे आणि एकत्रित करणे](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-FineTuning_PromptFlow_Integration.md)
      - [Azure AI Foundry मध्ये Prompt flow सह सानुकूल Phi-3 मॉडेल्स फाइन-ट्यून करणे आणि एकत्रित करणे](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-FineTuning_PromptFlow_Integration_AIFoundry.md)
      - [Microsoft च्या उत्तरदायी AI तत्त्वांवर लक्ष केंद्रित करून Azure AI Foundry मध्ये फाइन-ट्यून केलेल्या Phi-3 / Phi-3.5 मॉडेलचे मूल्यमापन](./md/02.Application/01.TextAndChat/Phi3/E2E_Phi-3-Evaluation_AIFoundry.md)
- [📓] [Phi-3.5-mini-instruct भाषा अंदाज नमुना (चिनी/इंग्रजी)](../../md/02.Application/01.TextAndChat/Phi3/phi3-instruct-demo.ipynb)
      - [Phi-3.5-Instruct WebGPU RAG Chatbot](./md/02.Application/01.TextAndChat/Phi3/WebGPUWithPhi35Readme.md)
      - [Windows GPU वापरून Phi-3.5-Instruct ONNX सह Prompt Flow Solution तयार करा](./md/02.Application/01.TextAndChat/Phi3/UsingPromptFlowWithONNX.md)
      - [Microsoft Phi-3.5 tflite वापरून Android अॅप तयार करा](./md/02.Application/01.TextAndChat/Phi3/UsingPhi35TFLiteCreateAndroidApp.md)
      - [Microsoft.ML.OnnxRuntime वापरून स्थानिक ONNX Phi-3 मॉडेलसह Q&A .NET उदाहरण](../../md/04.HOL/dotnet/src/LabsPhi301)
      - [Semantic Kernel आणि Phi-3 सह Console Chat .NET अॅप](../../md/04.HOL/dotnet/src/LabsPhi302)

  - Azure AI Inference SDK कोड आधारित नमुने 
    - Phi-4 नमुने 🆕
      - [📓] [Phi-4-multimodal वापरून प्रकल्प कोड तयार करा](./md/02.Application/02.Code/Phi4/GenProjectCode/README.md)
    - Phi-3 / 3.5 नमुने
      - [Microsoft Phi-3 कुटुंबासह स्वतःचे Visual Studio Code GitHub Copilot Chat तयार करा](./md/02.Application/02.Code/Phi3/VSCodeExt/README.md)
      - [Phi-3.5 सह GitHub मॉडेल्स वापरून स्वतःचे Visual Studio Code Chat Copilot Agent तयार करा](/md/02.Application/02.Code/Phi3/CreateVSCodeChatAgentWithGitHubModels.md)

  - प्रगत तर्कशक्ती नमुने
    - Phi-4 नमुने 🆕
      - [📓] [Phi-4-mini तर्कशक्ती नमुने](./md/02.Application/03.AdvancedReasoning/Phi4/AdvancedResoningPhi4mini/README.md)
  
  - डेमो
      - [Hugging Face Spaces वर होस्ट केलेले Phi-4-mini डेमो](https://huggingface.co/spaces/microsoft/phi-4-mini?WT.mc_id=aiml-137032-kinfeylo)
      - [Hugging Face Spaces वर होस्ट केलेले Phi-4-multimodal डेमो](https://huggingface.co/spaces/microsoft/phi-4-multimodal?WT.mc_id=aiml-137032-kinfeylo)
  - व्हिजन नमुने
    - Phi-4 नमुने 🆕
      - [📓] [Phi-4-multimodal वापरून प्रतिमा वाचा आणि कोड तयार करा](./md/02.Application/04.Vision/Phi4/CreateFrontend/README.md) 
    - Phi-3 / 3.5 नमुने
      -  [📓][Phi-3-vision-प्रतिमा मजकूर ते मजकूर](../../md/02.Application/04.Vision/Phi3/E2E_Phi-3-vision-image-text-to-text-online-endpoint.ipynb)
      - [Phi-3-vision-ONNX](https://onnxruntime.ai/docs/genai/tutorials/phi3-v.html)
      - [📓][Phi-3-vision CLIP Embedding](../../md/02.Application/04.Vision/Phi3/E2E_Phi-3-vision-image-text-to-text-online-endpoint.ipynb)
      - [डेमो: Phi-3 Recycling](https://github.com/jennifermarsman/PhiRecycling/)
      - [Phi-3-vision - Visual language assistant - Phi3-Vision आणि OpenVINO सह](https://docs.openvino.ai/nightly/notebooks/phi-3-vision-with-output.html)
      - [Phi-3 Vision Nvidia NIM](./md/02.Application/04.Vision/Phi3/E2E_Nvidia_NIM_Vision.md)
      - [Phi-3 Vision OpenVino](./md/02.Application/04.Vision/Phi3/E2E_OpenVino_Phi3Vision.md)
      - [📓][Phi-3.5 Vision मल्टी-फ्रेम किंवा मल्टी-इमेज नमुना](../../md/02.Application/04.Vision/Phi3/phi3-vision-demo.ipynb)
      - [Microsoft.ML.OnnxRuntime .NET वापरून Phi-3 Vision स्थानिक ONNX मॉडेल](../../md/04.HOL/dotnet/src/LabsPhi303)
      - [Microsoft.ML.OnnxRuntime .NET वापरून मेनू आधारित Phi-3 Vision स्थानिक ONNX मॉडेल](../../md/04.HOL/dotnet/src/LabsPhi304)

  - ऑडिओ नमुने
    - Phi-4 नमुने 🆕
      - [📓] [Phi-4-multimodal वापरून ऑडिओ ट्रान्सक्रिप्ट्स काढणे](./md/02.Application/05.Audio/Phi4/Transciption/README.md)
      - [📓] [Phi-4-multimodal ऑडिओ नमुना](../../md/02.Application/05.Audio/Phi4/Siri/demo.ipynb)
      - [📓] [Phi-4-multimodal स्पीच ट्रान्सलेशन नमुना](../../md/02.Application/05.Audio/Phi4/Translate/demo.ipynb)
      - [.NET कन्सोल अॅप्लिकेशन वापरून Phi-4-multimodal ऑडिओसह ऑडिओ फाइलचे विश्लेषण करा आणि ट्रान्सक्रिप्ट तयार करा](../../md/04.HOL/dotnet/src/LabsPhi4-MultiModal-02Audio)

  - MOE नमुने
    - Phi-3 / 3.5 नमुने
      - [📓] [Phi-3.5 Mixture of Experts Models (MoEs) सोशल मीडिया नमुना](../../md/02.Application/06.MoE/Phi3/phi3_moe_demo.ipynb)
      - [📓] [NVIDIA NIM Phi-3 MOE, Azure AI Search, आणि LlamaIndex वापरून Retrieval-Augmented Generation (RAG) पाइपलाइन तयार करणे](../../md/02.Application/06.MoE/Phi3/azure-ai-search-nvidia-rag.ipynb)
  - फंक्शन कॉलिंग नमुने
    - Phi-4 नमुने 🆕
      -  [📓] [Phi-4-mini सह Function Calling वापरणे](./md/02.Application/07.FunctionCalling/Phi4/FunctionCallingBasic/README.md)
  - मल्टीमोडल मिक्सिंग नमुने
    - Phi-4 नमुने 🆕
- [📓] [Phi-4-मल्टिमोडल तंत्रज्ञान पत्रकार म्हणून वापरणे](../../md/02.Application/08.Multimodel/Phi4/TechJournalist/phi_4_mm_audio_text_publish_news.ipynb)  
  - [.NET कन्सोल अॅप्लिकेशन वापरून Phi-4-मल्टिमोडलद्वारे प्रतिमा विश्लेषण](../../md/04.HOL/dotnet/src/LabsPhi4-MultiModal-01Images)

- Phi नमुने फाइन-ट्यून करणे  
  - [फाइन-ट्यूनिंग परिदृश्ये](./md/03.FineTuning/FineTuning_Scenarios.md)  
  - [फाइन-ट्यूनिंग vs RAG](./md/03.FineTuning/FineTuning_vs_RAG.md)  
  - [Phi-3 ला उद्योगातील तज्ज्ञ बनवण्यासाठी फाइन-ट्यूनिंग](./md/03.FineTuning/LetPhi3gotoIndustriy.md)  
  - [VS Code साठी AI टूलकिट वापरून Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/Finetuning_VSCodeaitoolkit.md)  
  - [Azure Machine Learning Service वापरून Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/Introduce_AzureML.md)  
  - [Lora सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_Lora.md)  
  - [QLora सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_Qlora.md)  
  - [Azure AI Foundry सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_AIFoundry.md)  
  - [Azure ML CLI/SDK सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_MLSDK.md)  
  - [Microsoft Olive सह फाइन-ट्यूनिंग](./md/03.FineTuning/FineTuning_MicrosoftOlive.md)  
  - [Microsoft Olive Hands-On Lab सह फाइन-ट्यूनिंग](./md/03.FineTuning/olive-lab/readme.md)  
  - [Weights आणि Bias सह Phi-3-vision फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_Phi-3-visionWandB.md)  
  - [Apple MLX Framework सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_MLX.md)  
  - [Phi-3-vision (अधिकृत समर्थन) सह फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_Vision.md)  
  - [Kaito AKS, Azure Containers (अधिकृत समर्थन) सह Phi-3 फाइन-ट्यून करणे](./md/03.FineTuning/FineTuning_Kaito.md)  
  - [Phi-3 आणि 3.5 Vision फाइन-ट्यून करणे](https://github.com/2U1/Phi3-Vision-Finetune)  

- Hands-on Lab  
  - [आघाडीचे मॉडेल्स एक्सप्लोर करणे: LLMs, SLMs, स्थानिक विकास आणि अधिक](https://github.com/microsoft/aitour-exploring-cutting-edge-models)  
  - [NLP क्षमता उघडणे: Microsoft Olive सह फाइन-ट्यूनिंग](https://github.com/azure/Ignite_FineTuning_workshop)  

- शैक्षणिक संशोधन पेपर्स आणि प्रकाशने  
  - [Textbooks Are All You Need II: phi-1.5 तांत्रिक अहवाल](https://arxiv.org/abs/2309.05463)  
  - [Phi-3 तांत्रिक अहवाल: तुमच्या फोनवर स्थानिक पातळीवर एक अत्यंत सक्षम भाषा मॉडेल](https://arxiv.org/abs/2404.14219)  
  - [Phi-4 तांत्रिक अहवाल](https://arxiv.org/abs/2412.08905)  
  - [लहान भाषा मॉडेल्स इन-व्हेईकल फंक्शन-कॉलिंगसाठी ऑप्टिमाइझ करणे](https://arxiv.org/abs/2501.02342)  
  - [(WhyPHI) PHI-3 साठी मल्टिपल-चॉईस प्रश्न उत्तरांसाठी फाइन-ट्यूनिंग: पद्धतशास्त्र, निकाल आणि आव्हाने](https://arxiv.org/abs/2501.01588)  

## Phi मॉडेल्स वापरणे  

### Azure AI Foundry वर Phi  

तुम्ही Microsoft Phi कसे वापरायचे आणि वेगवेगळ्या हार्डवेअर डिव्हाइसवर एंड-टू-एंड सोल्यूशन्स कसे तयार करायचे हे शिकू शकता. Phi स्वतः अनुभवण्यासाठी, मॉडेल्ससह प्रयोग करून आणि तुमच्या परिदृश्यांसाठी Phi सानुकूलित करून सुरू करा. [Azure AI Foundry Azure AI Model Catalog](https://aka.ms/phi3-azure-ai) मध्ये अधिक जाणून घ्या. [Azure AI Foundry](/md/02.QuickStart/AzureAIFoundry_QuickStart.md) सह सुरुवात करण्यासाठी येथे पहा.  

**Playground**  
प्रत्येक मॉडेलसाठी त्याचे स्वतःचे प्लेग्राउंड आहे जेथे तुम्ही मॉडेलची चाचणी घेऊ शकता: [Azure AI Playground](https://aka.ms/try-phi3).  

### GitHub Models वर Phi  

तुम्ही Microsoft Phi कसे वापरायचे आणि वेगवेगळ्या हार्डवेअर डिव्हाइसवर एंड-टू-एंड सोल्यूशन्स कसे तयार करायचे हे शिकू शकता. Phi स्वतः अनुभवण्यासाठी, मॉडेलसह प्रयोग करून आणि तुमच्या परिदृश्यांसाठी Phi सानुकूलित करून सुरू करा. [GitHub Model Catalog](https://github.com/marketplace/models?WT.mc_id=aiml-137032-kinfeylo) मध्ये अधिक जाणून घ्या. [GitHub Model Catalog](/md/02.QuickStart/GitHubModel_QuickStart.md) सह सुरुवात करण्यासाठी येथे पहा.  

**Playground**  
प्रत्येक मॉडेलसाठी [मॉडेल तपासण्यासाठी स्वतंत्र प्लेग्राउंड आहे](/md/02.QuickStart/GitHubModel_QuickStart.md).

### Hugging Face वरील Phi

तुम्ही मॉडेल [Hugging Face](https://huggingface.co/microsoft) वर देखील पाहू शकता.

**प्लेग्राउंड**  
[Hugging Chat प्लेग्राउंड](https://huggingface.co/chat/models/microsoft/Phi-3-mini-4k-instruct)

## जबाबदार AI 

Microsoft आपल्या ग्राहकांना AI उत्पादने जबाबदारीने वापरण्यास मदत करण्यासाठी वचनबद्ध आहे, आमचे अनुभव शेअर करणे, आणि पारदर्शकता नोट्स व प्रभाव मूल्यांकन यासारख्या साधनांद्वारे विश्वासावर आधारित भागीदारी तयार करणे. यापैकी अनेक साधने [https://aka.ms/RAI](https://aka.ms/RAI) येथे उपलब्ध आहेत.  
Microsoft चा जबाबदार AI साठीचा दृष्टिकोन आमच्या AI तत्त्वांवर आधारित आहे: न्याय्यता, विश्वासार्हता आणि सुरक्षितता, गोपनीयता आणि सुरक्षा, समावेशकता, पारदर्शकता, आणि उत्तरदायित्व.

मोठ्या प्रमाणावर नैसर्गिक भाषा, प्रतिमा, आणि आवाज मॉडेल्स - जसे की या नमुन्यात वापरले गेले आहेत - ते कधी कधी अन्यायकारक, अविश्वसनीय किंवा आक्षेपार्ह वर्तन करू शकतात, ज्यामुळे हानी होऊ शकते. जोखीम आणि मर्यादांविषयी माहिती घेण्यासाठी कृपया [Azure OpenAI सेवा पारदर्शकता नोट](https://learn.microsoft.com/legal/cognitive-services/openai/transparency-note?tabs=text) वाचा.

या जोखमींना कमी करण्यासाठी सुचवलेला दृष्टिकोन म्हणजे आपल्या आर्किटेक्चरमध्ये सुरक्षा प्रणाली समाविष्ट करणे, जी हानिकारक वर्तन शोधू व थांबवू शकते. [Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) एक स्वतंत्र संरक्षण स्तर पुरवते, जे वापरकर्त्यांनी तयार केलेल्या किंवा AI ने तयार केलेल्या हानिकारक सामग्रीला ओळखू शकते. Azure AI Content Safety मध्ये मजकूर व प्रतिमा API आहेत, जे हानिकारक सामग्री शोधण्याची क्षमता देतात. Azure AI Foundry च्या अंतर्गत, Content Safety सेवा तुम्हाला विविध प्रकारांमध्ये हानिकारक सामग्री शोधण्यासाठी नमुना कोड पाहण्याची, एक्सप्लोर करण्याची आणि प्रयत्न करण्याची परवानगी देते. खालील [क्विकस्टार्ट दस्तऐवज](https://learn.microsoft.com/azure/ai-services/content-safety/quickstart-text?tabs=visual-studio%2Clinux&pivots=programming-language-rest) तुम्हाला या सेवेसाठी विनंत्या करण्याच्या प्रक्रियेत मार्गदर्शन करतो.

दुसरा एक महत्त्वाचा पैलू म्हणजे एकूणच ऍप्लिकेशनचा कार्यक्षमतेचा विचार करणे. मल्टी-मोडल आणि मल्टी-मॉडेल ऍप्लिकेशन्ससाठी, कार्यक्षमता याचा अर्थ असा होतो की प्रणाली तुम्ही आणि तुमचे वापरकर्ते अपेक्षित करता तशी कार्य करते, ज्यामध्ये हानिकारक आउटपुट तयार न करणे याचाही समावेश आहे. तुमच्या ऍप्लिकेशनची एकूण कार्यक्षमता [Performance and Quality आणि Risk and Safety मूल्यांकन साधनांद्वारे](https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-metrics-built-in) तपासणे महत्त्वाचे आहे. तुम्हाला [कस्टम मूल्यांकन साधने](https://learn.microsoft.com/azure/ai-studio/how-to/develop/evaluate-sdk#custom-evaluators) तयार करण्याची आणि त्यांचे मूल्यांकन करण्याची क्षमता देखील आहे.

तुमच्या विकासाच्या वातावरणात [Azure AI Evaluation SDK](https://microsoft.github.io/promptflow/index.html) वापरून तुमच्या AI ऍप्लिकेशनचे मूल्यांकन करू शकता. चाचणी डेटासेट किंवा लक्ष्य दिल्यास, तुमच्या जनरेटिव्ह AI ऍप्लिकेशनच्या आउटपुटचे मोजमाप बिल्ट-इन किंवा तुमच्या पसंतीच्या कस्टम मूल्यांकन साधनांद्वारे केले जाते. Azure AI Evaluation SDK वापरून तुमच्या प्रणालीचे मूल्यांकन कसे करायचे हे जाणून घेण्यासाठी तुम्ही [क्विकस्टार्ट मार्गदर्शिका](https://learn.microsoft.com/azure/ai-studio/how-to/develop/flow-evaluate-sdk) फॉलो करू शकता. एकदा मूल्यांकन प्रक्रिया पूर्ण झाल्यावर, तुम्ही [Azure AI Foundry मध्ये निकाल पाहू शकता](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-flow-results).

## ट्रेडमार्क्स

या प्रकल्पामध्ये प्रकल्प, उत्पादने, किंवा सेवांसाठीचे ट्रेडमार्क्स किंवा लोगो असू शकतात. Microsoft ट्रेडमार्क्स किंवा लोगोचा अधिकृत वापर [Microsoft च्या ट्रेडमार्क व ब्रँड मार्गदर्शक](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general) पालन करण्याच्या अधीन आहे.  
या प्रकल्पाच्या सुधारित आवृत्त्यांमध्ये Microsoft ट्रेडमार्क्स किंवा लोगोचा वापर गोंधळ निर्माण करू नये किंवा Microsoft च्या प्रायोजकत्वाचा संकेत देऊ नये. तृतीय-पक्ष ट्रेडमार्क्स किंवा लोगोचा कोणताही वापर त्या तृतीय-पक्षांच्या धोरणांच्या अधीन आहे.

**अस्वीकरण**:  
हे दस्तऐवज मशीन-आधारित एआय भाषांतर सेवांचा वापर करून अनुवादित करण्यात आले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ भाषेतील मूळ दस्तऐवज हा अधिकृत स्रोत मानला पाहिजे. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवलेल्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार राहणार नाही.