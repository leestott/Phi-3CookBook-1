# **Apple MLX ফ্রেমওয়ার্ক ব্যবহার করে Phi-3.5 কোয়ান্টাইজ করা**

MLX হলো অ্যাপল সিলিকনের জন্য একটি মেশিন লার্নিং গবেষণা ফ্রেমওয়ার্ক, যা অ্যাপল মেশিন লার্নিং রিসার্চ দ্বারা তৈরি।

MLX মেশিন লার্নিং গবেষকদের জন্য ডিজাইন করা হয়েছে, গবেষকদের দ্বারা। এই ফ্রেমওয়ার্কটি ব্যবহারকারী-বান্ধব হলেও মডেল ট্রেনিং এবং ডিপ্লয়মেন্টে কার্যকরী। ফ্রেমওয়ার্কটির ডিজাইন ধারণাগতভাবে সহজ। আমরা গবেষকদের নতুন আইডিয়া দ্রুত পরীক্ষা করার জন্য MLX বাড়ানো এবং উন্নত করা সহজ করতে চাই।

Apple Silicon ডিভাইসগুলোতে MLX ব্যবহার করে LLM গুলোকে ত্বরান্বিত করা যায়, এবং মডেলগুলো স্থানীয়ভাবে খুব সহজেই চালানো যায়।

এখন Apple MLX ফ্রেমওয়ার্ক Phi-3.5-Instruct(**Apple MLX Framework support**), Phi-3.5-Vision(**MLX-VLM Framework support**) এবং Phi-3.5-MoE(**Apple MLX Framework support**) এর কোয়ান্টাইজেশন কনভার্সন সাপোর্ট করে। আসুন এটি চেষ্টা করি:

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

### **🤖 Apple MLX সহ Phi-3.5 এর নমুনা**

| ল্যাব    | পরিচিতি | যান |
| -------- | ------- |  ------- |
| 🚀 ল্যাব-পরিচিতি Phi-3.5 Instruct  | Apple MLX ফ্রেমওয়ার্ক দিয়ে Phi-3.5 Instruct ব্যবহার করা শিখুন   |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-instruct.ipynb)    |
| 🚀 ল্যাব-পরিচিতি Phi-3.5 Vision (image) | Apple MLX ফ্রেমওয়ার্ক দিয়ে Phi-3.5 Vision ব্যবহার করে ইমেজ বিশ্লেষণ করা শিখুন     |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-vision.ipynb)    |
| 🚀 ল্যাব-পরিচিতি Phi-3.5 Vision (moE)   | Apple MLX ফ্রেমওয়ার্ক দিয়ে Phi-3.5 MoE ব্যবহার করা শিখুন  |  [Go](../../../../../code/09.UpdateSamples/Aug/mlx-phi35-moe.ipynb)    |

## **উপকরণসমূহ**

1. Apple MLX Framework সম্পর্কে জানুন [https://ml-explore.github.io/mlx/](https://ml-explore.github.io/mlx/)

2. Apple MLX GitHub রিপো [https://github.com/ml-explore](https://github.com/ml-explore/mlx)

3. MLX-VLM GitHub রিপো [https://github.com/Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)

**অস্বীকৃতি**:  
এই নথিটি মেশিন-ভিত্তিক এআই অনুবাদ পরিষেবার মাধ্যমে অনুবাদ করা হয়েছে। আমরা যথাসাধ্য সঠিক অনুবাদের চেষ্টা করি, তবে দয়া করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসঙ্গতি থাকতে পারে। নথিটির মূল ভাষায় রচিত আসল সংস্করণকে প্রামাণিক সূত্র হিসেবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ ব্যবহার করার পরামর্শ দেওয়া হয়। এই অনুবাদের ব্যবহারের ফলে সৃষ্ট যেকোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী থাকব না।