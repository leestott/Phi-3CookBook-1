# **एप्पल MLX फ्रेमवर्क प्रयोग गरी Phi-3.5 लाई क्वान्टाइज गर्ने**

MLX एप्पल सिलिकनमा मेसिन लर्निङ अनुसन्धानका लागि तयार गरिएको एउटा फ्रेमवर्क हो, जसलाई एप्पलको मेसिन लर्निङ अनुसन्धान टोलीले विकास गरेको हो।

MLX मेसिन लर्निङ अनुसन्धानकर्ताहरूका लागि डिजाइन गरिएको छ। यो फ्रेमवर्क प्रयोगकर्ता मैत्री मात्र नभई मोडेलहरूलाई प्रभावकारी रूपमा ट्रेन र डिप्लोय गर्न सक्षम छ। फ्रेमवर्कको डिजाइन पनि धेरै सरल छ, जसले अनुसन्धानकर्ताहरूलाई नयाँ विचारहरू छिटो परीक्षण गर्न सजिलो बनाउँछ। 

Apple Silicon उपकरणहरूमा MLX मार्फत LLMs लाई तीव्र गतिमा चलाउन सकिन्छ, जसले गर्दा मोडेलहरूलाई स्थानीय रूपमा सजिलै चलाउन सकिन्छ।

अहिले एप्पल MLX फ्रेमवर्कले Phi-3.5-Instruct(**Apple MLX Framework support**), Phi-3.5-Vision(**MLX-VLM Framework support**) र Phi-3.5-MoE(**Apple MLX Framework support**) को क्वान्टाइजेसन कनभर्सनलाई समर्थन गर्दछ। अब हामी यसलाई प्रयास गरौँ:

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

### **🤖 Apple MLX प्रयोग गरी Phi-3.5 का नमूनाहरू**

| प्रयोगशाला  | परिचय | जानुहोस् |
| -------- | ------- | ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | Apple MLX फ्रेमवर्क प्रयोग गरी Phi-3.5 Instruct कसरी प्रयोग गर्ने भनेर सिक्नुहोस् | [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb) |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | Apple MLX फ्रेमवर्क प्रयोग गरी Phi-3.5 Vision ले छविहरू कसरी विश्लेषण गर्ने भनेर सिक्नुहोस् | [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb) |
| 🚀 Lab-Introduce Phi-3.5 Vision (moE) | Apple MLX फ्रेमवर्क प्रयोग गरी Phi-3.5 MoE कसरी प्रयोग गर्ने भनेर सिक्नुहोस् | [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb) |

## **स्रोतहरू**

1. Apple MLX फ्रेमवर्कबारे जान्नुहोस् [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub रिपोजिटरी [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub रिपोजिटरी [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**अस्वीकरण**:  
यो दस्तावेज़ मेशिन-आधारित एआई अनुवाद सेवाहरू प्रयोग गरी अनुवाद गरिएको हो। हामी यथासम्भव सही अनुवाद प्रदान गर्न प्रयास गर्दछौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटि वा अशुद्धता हुन सक्छ। मूल भाषामा रहेको मूल दस्तावेजलाई प्रामाणिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीका लागि, व्यावसायिक मानव अनुवादको सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी जिम्मेवार हुने छैनौं।