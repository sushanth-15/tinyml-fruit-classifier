# tinyml-fruit-classifier
TinyML-based dual-stage fruit ripeness classifier for mangoes and bananas using Raspberry Pi and TFLite
# 🍌🥭 Fruit Ripeness Classification using TinyML (Mango & Banana)

This project implements a dual-stage fruit ripeness classification system using MobileNetV2 and TensorFlow Lite. It detects whether a **mango or banana** is **ripe** or **raw** in real time on a **Raspberry Pi 5**, with no internet connection required.

---

## 🚀 Project Overview

The Raspberry Pi captures a fruit image using a Pi camera, performs HSV-based color segmentation, and runs a two-stage classification pipeline:

1. **Mango Classifier**  
   → Detects: Ripe Mango / Raw Mango / Not a Mango

2. **Banana Classifier**  
   → Detects: Ripe Banana / Raw Banana

If the image is not classified as a mango, the system forwards it to the banana classifier. Final output is displayed within **3 seconds**, completely offline.

---

## 📊 Model Accuracy

| Classifier        | Accuracy |
|------------------|----------|
| Mango Classifier | 99.3%    |
| Banana Classifier| 99.0%    |

---

## 📓 Colab Notebook

The entire pipeline — from data preparation and training to TFLite conversion — is available in the notebook below:

👉 [Open Colab Notebook](https://colab.research.google.com/drive/1Uj5kCupCCYUeReAOisSMSmGoAU3qPqit#scrollTo=JmBXU7G_iVyR)

---

## 🧠 TFLite Models

You can find both final trained and quantized models here in the `models/` folder:

- `mango_classifier_model.tflite`
- `banana_classifier_model.tflite`

---

## 🗂️ Dataset

We used a publicly available dataset of mango and banana images collected from online sources, with four categories:

- Ripe Mango  
- Raw Mango  
- Ripe Banana  
- Raw Banana  

All images were manually curated and renamed for consistency.  
We applied data augmentation (rotation, brightness, zoom, etc.) to improve the model's robustness under varied lighting and background conditions.

📌 Dataset is used strictly for academic and research purposes. Source links will be added once finalized.

---

## 🛠️ Tech Stack

- Python  
- TensorFlow / TensorFlow Lite  
- MobileNetV2 (Transfer Learning)  
- Raspberry Pi 5  
- OpenCV (HSV masking for fruit segmentation)

---

## 🧪 Inference Pipeline

```plaintext
[Pi Camera Capture]
      ↓
[HSV Color Masking]
      ↓
[Mango Classifier]
      ↓                ↘
[Ripe/Raw]      → [Not a Mango? → Banana Classifier]
                         ↓
                   [Ripe/Raw Output]
