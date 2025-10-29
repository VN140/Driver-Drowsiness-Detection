# 💤 Driver Drowsiness Detection

A real-time driver drowsiness detection system using **computer vision** and **deep learning** to enhance road safety.  
This project detects a driver’s level of alertness by analyzing facial cues through live video input.

---

## 📘 Overview

Drowsy driving is a leading cause of road accidents worldwide.  
This project introduces a **deep learning-based system** that identifies driver drowsiness from real-time webcam footage using face detection and classification models.

### Key Features
- Real-time face and drowsiness detection using webcam.
- Ensemble of deep learning models (ResNet50, MobileNetV3, CNN).
- Comparison of multiple face and eye detection methods (Haar Cascades and YOLOv8).
- High accuracy and fast inference suitable for real-world use.

---

## 🧠 Methodology

### 1. Dataset
The project uses the **Driver Drowsiness Detection Dataset (DDD)** from Kaggle.  
It contains balanced classes of drowsy and non-drowsy drivers under varying conditions.  
Dataset: [Kaggle - Driver Drowsiness Dataset (DDD)](https://www.kaggle.com/datasets/ismailnasri20/driver-drowsiness-dataset-ddd)

**Data Preprocessing (PyTorch Transforms):**
- Resize to (224, 224)
- Random horizontal flip, rotation, and affine transform
- Color jitter (brightness, contrast, saturation, hue)
- Gaussian blur
- Normalization with ImageNet mean/std

These augmentations improve model robustness against lighting and pose variations.

---

### 2. Model Development

The system evaluates and compares multiple architectures:

| Model | Description | Accuracy | F1-score |
|:------|:-------------|:----------|:----------|
| Custom CNN | Baseline CNN architecture | ~78% | ~0.76 |
| ResNet50 | Deep CNN for rich feature extraction | ~95% | ~0.93 |
| MobileNetV3 | Lightweight and efficient model | ~96% | ~0.95 |
| CNN + ResNet50 | Hybrid model combining CNN and ResNet50 | ~97% | ~0.96 |
| **CNN + MobileNetV3** | **Final selected model** – best trade-off between accuracy and speed | **~99%** | **~0.98** |

**Techniques Used:**
- Dropout layers to reduce overfitting  
- Learning rate tuning and optimizer adjustments  
- Early stopping to prevent overtraining  
- Model evaluation via accuracy, precision, recall, and F1-score (using sklearn.metrics)

---

### 3. Face & Eye Detection

The project experimented with three face detection methods:

| Method | Description | Result |
|:--------|:-------------|:--------|
| haarcascade_eye.xml | Traditional eye detection | Many false positives |
| haarcascade_frontalface_default.xml | Full face detection | Better but unstable in real-time |
| YOLOv8n | Deep learning-based object detector | Detected general person regions, not always faces; requires fine-tuning |

💡 **Future direction:** Fine-tune YOLO to detect only facial regions for higher precision.

---

## ⚙️ Experimental Setup

- **Environment:** Python, PyTorch, OpenCV  
- **Hardware:** Standard webcam for live video input  
- **Objective:** Real-time monitoring and alertness classification  

---

## 📊 Results

- The hybrid **CNN + MobileNetV3** model achieved the **highest accuracy (~99%)**.
- Demonstrated real-time inference capability on standard hardware.
- Detected faces and classified drowsiness with minimal latency.

---

## 👥 Authors
- **Jakkaphat Jumratboonsom** — [jakkaphat.jum@student.mahidol.edu](mailto:jakkaphat.jum@student.mahidol.edu)  
- **Vichayuth Ngamsittipong** — [vichayuth.nga@student.mahidol.edu](mailto:vichayuth.nga@student.mahidol.edu)

**Institution:**  
Faculty of Information and Communication Technology, Mahidol University, Thailand
