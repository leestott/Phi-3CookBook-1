# Olive वापरून Phi3 फाइन-ट्यून करा

या उदाहरणात तुम्ही Olive चा वापर करून खालील गोष्टी शिकाल:

1. Sad, Joy, Fear, Surprise या वर्गांमध्ये वाक्ये वर्गीकृत करण्यासाठी LoRA अडॅप्टर फाइन-ट्यून करा.
1. अडॅप्टरचे वजन बेस मॉडेलमध्ये विलीन करा.
1. मॉडेल `int4` मध्ये ऑप्टिमाइझ आणि क्वांटाइझ करा.

तसेच, ONNX Runtime (ORT) Generate API वापरून फाइन-ट्यून केलेल्या मॉडेलचे इन्फरन्स कसे करायचे ते दाखवले जाईल.

> **⚠️ फाइन-ट्यूनिंगसाठी, तुमच्याकडे योग्य GPU असणे आवश्यक आहे - उदाहरणार्थ, A10, V100, A100.**

## 💾 इंस्टॉल करा

Python साठी एक नवीन वर्चुअल एन्व्हायर्नमेंट तयार करा (उदाहरणार्थ, `conda` वापरून):

```bash
conda create -n olive-ai python=3.11
conda activate olive-ai
```

यानंतर, Olive आणि फाइन-ट्यूनिंग वर्कफ्लोच्या डिपेंडन्सी इंस्टॉल करा:

```bash
cd Phi-3CookBook/code/04.Finetuning/olive-ort-example
pip install olive-ai[gpu]
pip install -r requirements.txt
```

## 🧪 Olive वापरून Phi3 फाइन-ट्यून करा
[Olive कॉन्फिगरेशन फाइल](../../../../../code/04.Finetuning/olive-ort-example/phrase-classification.json) मध्ये खालील *पासेस* असलेला एक *वर्कफ्लो* आहे:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

उच्च-स्तरीय दृष्टीकोनातून, हा वर्कफ्लो खालीलप्रमाणे असेल:

1. [dataset/data-classification.json](../../../../../code/04.Finetuning/olive-ort-example/dataset/dataset-classification.json) डेटा वापरून Phi3 ला फाइन-ट्यून करा (150 स्टेप्ससाठी, जे तुम्ही बदलू शकता).
1. LoRA अडॅप्टरचे वजन बेस मॉडेलमध्ये विलीन करा. यामुळे ONNX फॉरमॅटमध्ये एकच मॉडेल आर्टिफॅक्ट मिळेल.
1. Model Builder मॉडेल ONNX runtime साठी ऑप्टिमाइझ करेल *आणि* मॉडेल `int4` मध्ये क्वांटाइझ करेल.

वर्कफ्लो चालवण्यासाठी, हे चालवा:

```bash
olive run --config phrase-classification.json
```

Olive पूर्ण झाल्यावर, तुमचे ऑप्टिमाइझ केलेले `int4` फाइन-ट्यून Phi3 मॉडेल येथे उपलब्ध असेल: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 फाइन-ट्यून केलेले Phi3 तुमच्या ॲप्लिकेशनमध्ये समाविष्ट करा 

ॲप चालवण्यासाठी:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

हे उत्तर वाक्याचे एकल शब्द वर्गीकरण (Sad/Joy/Fear/Surprise) असेल.

**अस्वीकरण**:  
हे दस्तऐवज मशीन-आधारित एआय अनुवाद सेवांचा वापर करून अनुवादित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ भाषेतील मूळ दस्तऐवज अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी, व्यावसायिक मानवी अनुवादाची शिफारस केली जाते. या अनुवादाचा वापर केल्यामुळे उद्भवणाऱ्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार राहणार नाही.