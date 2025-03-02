# **Phi-3.5 चे क्वांटायझेशन Apple MLX फ्रेमवर्क वापरून**

MLX हे Apple सिलिकॉनसाठी मशीन लर्निंग संशोधनासाठी एक अॅरे फ्रेमवर्क आहे, जे Apple मशीन लर्निंग संशोधन विभागाने विकसित केले आहे.

MLX मशीन लर्निंग संशोधकांसाठी तयार केले गेले आहे, जे वापरण्यास सोपे असूनही मॉडेल्स प्रशिक्षण आणि डिप्लॉय करण्यासाठी कार्यक्षम आहे. या फ्रेमवर्कची रचना संकल्पनेने सोपी ठेवण्यात आली आहे, ज्यामुळे संशोधकांना MLX सहजपणे विस्तारित आणि सुधारित करता येईल, नवीन कल्पना जलदपणे शोधून काढता येतील.

Apple सिलिकॉन डिव्हाइसवर MLX वापरून LLMs अधिक वेगाने चालवता येतात आणि मॉडेल्स स्थानिक स्तरावर अगदी सोयीस्करपणे चालवता येतात.

आता Apple MLX फ्रेमवर्क Phi-3.5-Instruct (**Apple MLX Framework support**), Phi-3.5-Vision (**MLX-VLM Framework support**) आणि Phi-3.5-MoE (**Apple MLX Framework support**) च्या क्वांटायझेशन कन्व्हर्जनसाठी समर्थन करते. चला पुढे पाहूया:

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

### **🤖 Apple MLX सह Phi-3.5 चे नमुने**

| प्रयोगशाळा    | ओळख | जा |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | Apple MLX फ्रेमवर्कसह Phi-3.5 Instruct कसे वापरावे ते शिका   |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | Apple MLX फ्रेमवर्क वापरून Phi-3.5 Vision कसे प्रतिमा विश्लेषणासाठी वापरावे ते शिका     |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (moE)   | Apple MLX फ्रेमवर्कसह Phi-3.5 MoE कसे वापरावे ते शिका  |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **स्रोत**

1. Apple MLX फ्रेमवर्कबद्दल जाणून घ्या [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub रिपॉझिटरी [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub रिपॉझिटरी [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**अस्वीकरण**:  
हे दस्तऐवज मशीन-आधारित AI भाषांतर सेवांचा वापर करून अनुवादित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित भाषांतरांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ भाषेतील मूळ दस्तऐवज हा अधिकृत स्रोत मानावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या भाषांतराच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थ लावण्यास आम्ही जबाबदार राहणार नाही.