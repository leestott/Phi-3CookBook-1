# Olive वापरून Phi3 फाइन-ट्यून करा

या उदाहरणात तुम्ही Olive वापरून खालील गोष्टी शिकाल:

1. LoRA अ‍ॅडॉप्टर फाइन-ट्यून करा ज्यामुळे वाक्य Sad, Joy, Fear, Surprise या श्रेणींमध्ये वर्गीकृत होतील.
1. अ‍ॅडॉप्टरचे वेट्स बेस मॉडेलमध्ये मर्ज करा.
1. मॉडेल `int4` मध्ये ऑप्टिमाइझ आणि क्वांटाइझ करा.

आम्ही तुम्हाला ONNX Runtime (ORT) Generate API वापरून फाइन-ट्यून केलेल्या मॉडेलसाठी इनफरन्स कसा करायचा तेही दाखवू.

> **⚠️ फाइन-ट्यूनिंगसाठी, तुमच्याकडे योग्य GPU उपलब्ध असणे आवश्यक आहे - उदाहरणार्थ, A10, V100, A100.**

## 💾 इंस्टॉल करा

नवीन Python वर्च्युअल एन्व्हायर्नमेंट तयार करा (उदाहरणार्थ, `conda` वापरून):

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
[Olive कॉन्फिगरेशन फाईल](../../../../../code/03.Finetuning/olive-ort-example/phrase-classification.json) मध्ये खालील *पासेस* असलेला *वर्कफ्लो* आहे:

Phi3 -> LoRA -> MergeAdapterWeights -> ModelBuilder

या वर्कफ्लोचा उच्च-स्तरीय आढावा असा आहे:

1. Phi3 ला फाइन-ट्यून करा (150 स्टेप्ससाठी, ज्यात तुम्ही बदल करू शकता) [dataset/data-classification.json](../../../../../code/03.Finetuning/olive-ort-example/dataset/dataset-classification.json) डेटाचा वापर करून.
1. LoRA अ‍ॅडॉप्टर वेट्स बेस मॉडेलमध्ये मर्ज करा. यामुळे तुम्हाला ONNX फॉरमॅटमध्ये सिंगल मॉडेल आर्टिफॅक्ट मिळेल.
1. Model Builder मॉडेल ONNX runtime साठी ऑप्टिमाइझ करेल *आणि* मॉडेलला `int4` मध्ये क्वांटाइझ करेल.

वर्कफ्लो रन करण्यासाठी, खालील आदेश वापरा:

```bash
olive run --config phrase-classification.json
```

Olive पूर्ण झाल्यानंतर, ऑप्टिमाइझ केलेले `int4` फाइन-ट्यून Phi3 मॉडेल येथे उपलब्ध असेल: `code/04.Finetuning/olive-ort-example/models/lora-merge-mb/gpu-cuda_model`.

## 🧑‍💻 फाइन-ट्यून केलेले Phi3 तुमच्या ॲप्लिकेशनमध्ये समाकलित करा

ॲप चालवण्यासाठी:

```bash
python app/app.py --phrase "cricket is a wonderful sport!" --model-path models/lora-merge-mb/gpu-cuda_model
```

या प्रतिसादात वाक्याचा वर्ग (Sad/Joy/Fear/Surprise) एका शब्दात दिला जाईल.

**अस्वीकरण**:  
हे दस्तऐवज मशीन-आधारित AI अनुवाद सेवा वापरून अनुवादित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये त्रुटी किंवा अचूकतेचा अभाव असू शकतो. मूळ भाषेतील मूळ दस्तऐवज हा अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी, व्यावसायिक मानवी अनुवादाची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुतींसाठी किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार राहणार नाही.