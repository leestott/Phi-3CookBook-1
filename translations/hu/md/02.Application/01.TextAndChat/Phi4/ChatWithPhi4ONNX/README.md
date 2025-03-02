# **Beszélgetés Phi-4-mini ONNX-szal**

***ONNX*** egy nyílt formátum, amelyet gépi tanulási modellek reprezentálására hoztak létre. Az ONNX egy közös operátorkészletet határoz meg - a gépi tanulási és mélytanulási modellek építőelemeit -, valamint egy közös fájlformátumot, amely lehetővé teszi az AI fejlesztők számára, hogy modelleket különböző keretrendszerekkel, eszközökkel, futtatókörnyezetekkel és fordítókkal használjanak.

Célunk generatív AI modellek telepítése edge eszközökre, valamint azok használata korlátozott számítási kapacitású vagy offline környezetekben. Most ezt a célt kvantált módon történő modellkonvertálással érhetjük el. A kvantált modellt GGUF vagy ONNX formátumba tudjuk konvertálni.

A Microsoft Olive segíthet az SLM kvantált ONNX formátumba történő konvertálásában. A modellkonvertálás módja nagyon egyszerű.

**Microsoft Olive SDK telepítése**

```bash

pip install olive-ai

pip install transformers

```

**CPU ONNX támogatás konvertálása**

```bash

olive auto-opt --model_name_or_path Your Phi-4-mini location --output_path Your onnx ouput location --device cpu --provider CPUExecutionProvider --precision int4 --use_model_builder --log_level 1

```

***Megjegyzés*** ez a példa a CPU-t használja.


### **Phi-4-mini ONNX modell futtatása ONNX Runtime GenAI segítségével**

- **ONNX Runtime GenAI telepítése**

```bash

pip install --pre onnxruntime-genai

```

- **Python kód**

*Ez az ONNX Runtime GenAI 0.5.2-es verziója*

```python

import onnxruntime_genai as og
import numpy as np
import os


model_folder = "Your Phi-4-mini-onnx-cpu-int4 location"


model = og.Model(model_folder)


tokenizer = og.Tokenizer(model)
tokenizer_stream = tokenizer.create_stream()


search_options = {}
search_options['max_length'] = 2048
search_options['past_present_share_buffer'] = False


chat_template = "<|user|>\n{input}</s>\n<|assistant|>"


text = """Can you introduce yourself"""


prompt = f'{chat_template.format(input=text)}'


input_tokens = tokenizer.encode(prompt)


params = og.GeneratorParams(model)


params.set_search_options(**search_options)
params.input_ids = input_tokens


generator = og.Generator(model, params)


while not generator.is_done():
      generator.compute_logits()
      generator.generate_next_token()

      new_token = generator.get_next_tokens()[0]
      print(tokenizer_stream.decode(new_token), end='', flush=True)

```

*Ez az ONNX Runtime GenAI 0.6.0-es verziója*

```python

import onnxruntime_genai as og
import numpy as np
import os
import time
import psutil

model_folder = "Your Phi-4-mini-onnx model path"

model = og.Model(model_folder)

tokenizer = og.Tokenizer(model)
tokenizer_stream = tokenizer.create_stream()

search_options = {}
search_options['max_length'] = 1024
search_options['past_present_share_buffer'] = False

chat_template = "<|user|>{input}<|assistant|>"

text = """can you introduce yourself"""

prompt = f'{chat_template.format(input=text)}'

input_tokens = tokenizer.encode(prompt)

params = og.GeneratorParams(model)

params.set_search_options(**search_options)

generator = og.Generator(model, params)

generator.append_tokens(input_tokens)

while not generator.is_done():
      generator.generate_next_token()

      new_token = generator.get_next_tokens()[0]
      token_text = tokenizer.decode(new_token)
      # print(tokenizer_stream.decode(new_token), end='', flush=True)
      if token_count == 0:
        first_token_time = time.time()
        first_response_latency = first_token_time - start_time
        print(f"firstly token delpay: {first_response_latency:.4f} s")

      print(token_text, end='', flush=True)
      token_count += 1

```

**Felelősségkizárás**:  
Ez a dokumentum gépi AI fordítási szolgáltatásokkal készült fordítást tartalmaz. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az eredeti nyelvén tekintendő hiteles forrásnak. Kritikus információk esetén javasolt professzionális, emberi fordítást igénybe venni. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy téves értelmezésekért.