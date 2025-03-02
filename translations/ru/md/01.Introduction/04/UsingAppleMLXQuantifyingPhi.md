# **Квантование Phi-3.5 с использованием Apple MLX Framework**

MLX — это фреймворк для исследований в области машинного обучения на устройствах с Apple Silicon, созданный исследовательской командой Apple.

MLX разработан исследователями в области машинного обучения для таких же исследователей. Фреймворк создан с целью быть простым в использовании, но при этом эффективным для обучения и развертывания моделей. Его концептуальный дизайн также максимально упрощен. Мы стремимся сделать процесс расширения и улучшения MLX легким, чтобы ускорить исследование новых идей.

LLM-модели могут быть ускорены на устройствах с Apple Silicon с помощью MLX, что позволяет удобно запускать их локально.

Теперь Apple MLX Framework поддерживает преобразование для квантования Phi-3.5-Instruct (**поддержка Apple MLX Framework**), Phi-3.5-Vision (**поддержка MLX-VLM Framework**) и Phi-3.5-MoE (**поддержка Apple MLX Framework**). Давайте попробуем:

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

### **🤖 Примеры для Phi-3.5 с использованием Apple MLX**

| Лаборатории    | Описание | Перейти |
| -------- | ------- |  ------- |
| 🚀 Лаборатория: Введение в Phi-3.5 Instruct  | Узнайте, как использовать Phi-3.5 Instruct с Apple MLX Framework   |  [Перейти](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 Лаборатория: Введение в Phi-3.5 Vision (изображения) | Узнайте, как использовать Phi-3.5 Vision для анализа изображений с Apple MLX Framework     |  [Перейти](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 Лаборатория: Введение в Phi-3.5 Vision (moE)   | Узнайте, как использовать Phi-3.5 MoE с Apple MLX Framework  |  [Перейти](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **Ресурсы**

1. Узнайте больше об Apple MLX Framework [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Репозиторий Apple MLX на GitHub [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. Репозиторий MLX-VLM на GitHub [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**Отказ от ответственности**:  
Этот документ был переведен с использованием автоматических сервисов перевода на основе ИИ. Хотя мы стремимся к точности, пожалуйста, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его родном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется профессиональный перевод человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникающие в результате использования этого перевода.