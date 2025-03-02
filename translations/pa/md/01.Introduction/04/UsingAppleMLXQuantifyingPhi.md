# **Apple MLX ਫ੍ਰੇਮਵਰਕ ਦੀ ਵਰਤੋਂ ਕਰਕੇ Phi-3.5 ਦਾ ਕਵਾਂਟਾਈਜ਼ ਕਰਨਾ**

MLX ਐਪਲ ਸਿਲੀਕਾਨ 'ਤੇ ਮਸ਼ੀਨ ਲਰਨਿੰਗ ਰਿਸਰਚ ਲਈ ਇੱਕ ਐਰੇ ਫ੍ਰੇਮਵਰਕ ਹੈ, ਜੋ ਐਪਲ ਮਸ਼ੀਨ ਲਰਨਿੰਗ ਰਿਸਰਚ ਦੁਆਰਾ ਲਿਆਂਦਾ ਗਿਆ ਹੈ।

MLX ਨੂੰ ਮਸ਼ੀਨ ਲਰਨਿੰਗ ਰਿਸਰਚਰਾਂ ਦੁਆਰਾ ਮਸ਼ੀਨ ਲਰਨਿੰਗ ਰਿਸਰਚਰਾਂ ਲਈ ਡਿਜ਼ਾਇਨ ਕੀਤਾ ਗਿਆ ਹੈ। ਇਹ ਫ੍ਰੇਮਵਰਕ ਉਪਭੋਗਤਾ-ਮਿੱਤਰ ਬਣਾਉਣ ਲਈ ਹੈ, ਪਰ ਫਿਰ ਵੀ ਮਾਡਲਾਂ ਨੂੰ ਟ੍ਰੇਨ ਅਤੇ ਡਿਪਲੌਇ ਕਰਨ ਵਿੱਚ ਕੁਸ਼ਲ ਹੈ। ਫ੍ਰੇਮਵਰਕ ਦਾ ਡਿਜ਼ਾਈਨ ਆਪੇ ਵਿੱਚ ਹੀ ਸੰਕਲਪਕ ਤੌਰ 'ਤੇ ਸਧਾਰਨ ਹੈ। ਅਸੀਂ ਚਾਹੁੰਦੇ ਹਾਂ ਕਿ ਰਿਸਰਚਰਾਂ ਲਈ MLX ਨੂੰ ਵਧਾਉਣਾ ਅਤੇ ਸੁਧਾਰਨਾ ਆਸਾਨ ਹੋਵੇ, ਤਾਂ ਜੋ ਨਵੀਆਂ ਵਿਚਾਰਧਾਰਾਵਾਂ ਨੂੰ ਤੇਜ਼ੀ ਨਾਲ ਪੜਤਾਲਿਆ ਜਾ ਸਕੇ।

Apple Silicon ਡਿਵਾਈਸਾਂ 'ਤੇ MLX ਰਾਹੀਂ LLMs ਨੂੰ ਤੇਜ਼ ਕੀਤਾ ਜਾ ਸਕਦਾ ਹੈ, ਅਤੇ ਮਾਡਲ ਬਹੁਤ ਹੀ ਆਸਾਨੀ ਨਾਲ ਸਥਾਨਕ ਤੌਰ 'ਤੇ ਚਲਾਏ ਜਾ ਸਕਦੇ ਹਨ।

ਹੁਣ ਐਪਲ MLX ਫ੍ਰੇਮਵਰਕ Phi-3.5-Instruct(**Apple MLX Framework support**), Phi-3.5-Vision(**MLX-VLM Framework support**) ਅਤੇ Phi-3.5-MoE(**Apple MLX Framework support**) ਦੀ ਕਵਾਂਟਾਈਜ਼ ਕਨਵਰਜਨ ਨੂੰ ਸਹਾਇਕ ਬਣਾਉਂਦਾ ਹੈ। ਚਲੋ ਅੱਗੇ ਇਸਨੂੰ ਅਜ਼ਮਾਈਏ:

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

### **🤖 Apple MLX ਨਾਲ Phi-3.5 ਲਈ ਨਮੂਨੇ**

| Labs    | ਜਾਣਕਾਰੀ | ਜਾਓ |
| -------- | ------- |  ------- |
| 🚀 Lab-Introduce Phi-3.5 Instruct  | ਜਾਣੋ ਕਿ Apple MLX ਫ੍ਰੇਮਵਰਕ ਨਾਲ Phi-3.5 Instruct ਦੀ ਵਰਤੋਂ ਕਿਵੇਂ ਕਰਨੀ ਹੈ   |  [ਜਾਓ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (image) | ਜਾਣੋ ਕਿ Apple MLX ਫ੍ਰੇਮਵਰਕ ਨਾਲ ਤਸਵੀਰ ਦਾ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰਨ ਲਈ Phi-3.5 Vision ਦੀ ਵਰਤੋਂ ਕਿਵੇਂ ਕਰਨੀ ਹੈ     |  [ਜਾਓ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 Lab-Introduce Phi-3.5 Vision (moE)   | ਜਾਣੋ ਕਿ Apple MLX ਫ੍ਰੇਮਵਰਕ ਨਾਲ Phi-3.5 MoE ਦੀ ਵਰਤੋਂ ਕਿਵੇਂ ਕਰਨੀ ਹੈ  |  [ਜਾਓ](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **ਸਰੋਤ**

1. Apple MLX Framework ਬਾਰੇ ਜਾਣੋ [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub ਰਿਪੋ [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub ਰਿਪੋ [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**ਅਸਵੀਕਾਰਣਾ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ ਮਸ਼ੀਨ ਅਧਾਰਿਤ AI ਅਨੁਵਾਦ ਸੇਵਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਲਈ ਯਤਨਸ਼ੀਲ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁਣਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼, ਜੋ ਕਿ ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਹੈ, ਨੂੰ ਅਧਿਕਾਰਤ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਅਸੀਂ ਇਸ ਅਨੁਵਾਦ ਦੇ ਪ੍ਰਯੋਗ ਤੋਂ ਪੈਦਾ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।