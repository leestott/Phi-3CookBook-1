# **Apple MLX फ्रेमवर्क का उपयोग करके Phi-3.5 को क्वांटाइज़ करना**

MLX Apple सिलिकॉन पर मशीन लर्निंग शोध के लिए एक ऐरे फ्रेमवर्क है, जिसे Apple मशीन लर्निंग शोधकर्ताओं द्वारा विकसित किया गया है।

MLX को मशीन लर्निंग शोधकर्ताओं द्वारा मशीन लर्निंग शोधकर्ताओं के लिए डिज़ाइन किया गया है। यह फ्रेमवर्क उपयोगकर्ता के लिए सरल और सुविधाजनक होने के साथ-साथ मॉडल को ट्रेन और डिप्लॉय करने में प्रभावी है। फ्रेमवर्क का डिज़ाइन भी अवधारणात्मक रूप से सरल है। हमारा उद्देश्य शोधकर्ताओं के लिए MLX को विस्तारित और सुधारने में आसानी प्रदान करना है, ताकि वे नई अवधारणाओं को जल्दी से एक्सप्लोर कर सकें।

Apple सिलिकॉन डिवाइसों में MLX के माध्यम से LLMs को तेज़ी से चलाया जा सकता है, और मॉडल्स को आसानी से लोकल रूप से रन किया जा सकता है।

अब Apple MLX फ्रेमवर्क Phi-3.5-Instruct(**Apple MLX Framework support**), Phi-3.5-Vision(**MLX-VLM Framework support**) और Phi-3.5-MoE(**Apple MLX Framework support**) के क्वांटाइज़ेशन कन्वर्ज़न को सपोर्ट करता है। आइए इसे आज़माते हैं:

### **Phi-3.5-Instruct**

```bash

python -m mlx_lm.convert --hf-path microsoft/Phi-3.5-mini-instruct -q

```

### **Phi-3.5-Vision**

```bash

python -m mlxv_lm.convert --hf-path microsoft/Phi-3.5-vision-instruct -q

```

### **Phi-3.5-MoE**

```bash

python -m mlx_lm.convert --hf-path microsoft/Phi-3.5-MoE-instruct  -q

```

### **🤖 Apple MLX के साथ Phi-3.5 के सैंपल्स**

| लैब्स    | परिचय | जाओ |
| -------- | ------- |  ------- |
| 🚀 लैब-Phi-3.5 Instruct का परिचय  | जानें कि Apple MLX फ्रेमवर्क के साथ Phi-3.5 Instruct का उपयोग कैसे करें   |  [जाओ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 लैब-Phi-3.5 Vision (इमेज) का परिचय | जानें कि Apple MLX फ्रेमवर्क के साथ इमेज को एनालाइज़ करने के लिए Phi-3.5 Vision का उपयोग कैसे करें     |  [जाओ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 लैब-Phi-3.5 Vision (MoE) का परिचय   | जानें कि Apple MLX फ्रेमवर्क के साथ Phi-3.5 MoE का उपयोग कैसे करें  |  [जाओ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **संसाधन**

1. Apple MLX फ्रेमवर्क के बारे में जानें [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub रिपॉजिटरी [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub रिपॉजिटरी [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**अस्वीकरण**:  
यह दस्तावेज़ मशीन-आधारित एआई अनुवाद सेवाओं का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियां या अशुद्धियां हो सकती हैं। मूल दस्तावेज़, जो इसकी मूल भाषा में है, को प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।