# **Ποσοτικοποίηση του Phi-3.5 με χρήση του Intel OpenVINO**

Η Intel είναι ο πιο παραδοσιακός κατασκευαστής επεξεργαστών με πολλούς χρήστες. Με την άνοδο της μηχανικής μάθησης και της βαθιάς μάθησης, η Intel έχει επίσης εισέλθει στον ανταγωνισμό για την επιτάχυνση της τεχνητής νοημοσύνης. Για την εξαγωγή μοντέλων, η Intel χρησιμοποιεί όχι μόνο GPUs και CPUs, αλλά και NPUs.

Ελπίζουμε να αναπτύξουμε τη σειρά Phi-3.x στην άκρη, προσδοκώντας να γίνει το πιο σημαντικό μέρος του AI PC και του Copilot PC. Η φόρτωση του μοντέλου στην άκρη εξαρτάται από τη συνεργασία διαφορετικών κατασκευαστών υλικού. Αυτό το κεφάλαιο επικεντρώνεται κυρίως στο σενάριο εφαρμογής του Intel OpenVINO ως ένα ποσοτικοποιημένο μοντέλο.


## **Τι είναι το OpenVINO**

Το OpenVINO είναι ένα εργαλείο ανοιχτού κώδικα για τη βελτιστοποίηση και την ανάπτυξη μοντέλων βαθιάς μάθησης από το cloud στην άκρη. Επιταχύνει την εξαγωγή συμπερασμάτων βαθιάς μάθησης σε διάφορες περιπτώσεις χρήσης, όπως γενετική τεχνητή νοημοσύνη, βίντεο, ήχος και γλώσσα, με μοντέλα από δημοφιλή frameworks όπως PyTorch, TensorFlow, ONNX, και άλλα. Μετατρέψτε και βελτιστοποιήστε μοντέλα και αναπτύξτε τα σε διάφορους συνδυασμούς υλικού και περιβαλλόντων της Intel®, είτε σε τοπικό επίπεδο είτε σε συσκευές, στο πρόγραμμα περιήγησης ή στο cloud.

Με το OpenVINO, μπορείτε πλέον να ποσοτικοποιήσετε γρήγορα το μοντέλο GenAI σε υλικό της Intel και να επιταχύνετε την αναφορά του μοντέλου.

Πλέον, το OpenVINO υποστηρίζει τη μετατροπή ποσοτικοποίησης των Phi-3.5-Vision και Phi-3.5 Instruct.

### **Ρύθμιση Περιβάλλοντος**

Παρακαλούμε βεβαιωθείτε ότι έχουν εγκατασταθεί οι παρακάτω εξαρτήσεις περιβάλλοντος, αυτό είναι το requirement.txt 

```txt

--extra-index-url https://download.pytorch.org/whl/cpu
optimum-intel>=1.18.2
nncf>=2.11.0
openvino>=2024.3.0
transformers>=4.40
openvino-genai>=2024.3.0.0

```

### **Ποσοτικοποίηση του Phi-3.5-Instruct με χρήση του OpenVINO**

Στο Terminal, εκτελέστε αυτό το script

```bash


export llm_model_id = "microsoft/Phi-3.5-mini-instruct"

export llm_model_path = "your save quantizing Phi-3.5-instruct location"

optimum-cli export openvino --model {llm_model_id} --task text-generation-with-past --weight-format int4 --group-size 128 --ratio 0.6  --sym  --trust-remote-code {llm_model_path}


```

### **Ποσοτικοποίηση του Phi-3.5-Vision με χρήση του OpenVINO**

Εκτελέστε αυτό το script σε Python ή Jupyter lab

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

### **🤖 Παραδείγματα για το Phi-3.5 με Intel OpenVINO**

| Εργαστήρια    | Περιγραφή | Μετάβαση |
| -------- | ------- |  ------- |
| 🚀 Εργαστήριο - Εισαγωγή στο Phi-3.5 Instruct  | Μάθετε πώς να χρησιμοποιείτε το Phi-3.5 Instruct στον AI PC σας    |  [Μετάβαση](../../../../../code/09.UpdateSamples/Aug/intel-phi35-instruct-zh.ipynb)    |
| 🚀 Εργαστήριο - Εισαγωγή στο Phi-3.5 Vision (εικόνα) | Μάθετε πώς να χρησιμοποιείτε το Phi-3.5 Vision για ανάλυση εικόνων στον AI PC σας      |  [Μετάβαση](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-img.ipynb)    |
| 🚀 Εργαστήριο - Εισαγωγή στο Phi-3.5 Vision (βίντεο)   | Μάθετε πώς να χρησιμοποιείτε το Phi-3.5 Vision για ανάλυση εικόνων στον AI PC σας    |  [Μετάβαση](../../../../../code/09.UpdateSamples/Aug/intel-phi35-vision-video.ipynb)    |



## **Πηγές**

1. Μάθετε περισσότερα για το Intel OpenVINO [https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html)

2. Αποθετήριο GitHub του Intel OpenVINO [https://github.com/openvinotoolkit/openvino.genai](https://github.com/openvinotoolkit/openvino.genai)

**Αποποίηση ευθυνών**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας υπηρεσίες μηχανικής μετάφρασης με τεχνητή νοημοσύνη. Παρόλο που καταβάλλουμε προσπάθειες για ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτοματοποιημένες μεταφράσεις ενδέχεται να περιέχουν λάθη ή ανακρίβειες. Το πρωτότυπο έγγραφο στη μητρική του γλώσσα θα πρέπει να θεωρείται η αυθεντική πηγή. Για κρίσιμες πληροφορίες, συνιστάται επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για τυχόν παρεξηγήσεις ή εσφαλμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.