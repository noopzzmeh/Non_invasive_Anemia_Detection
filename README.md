# 🩸 Non-Invasive Anemia Detection using EfficientNetB0 and SVM

## 📌 Project Overview

This project presents a **non-invasive anemia detection system** that analyzes **nail bed and palm images** to classify individuals as **Anemic** or **Non-Anemic**. Instead of relying on invasive blood tests, the system uses deep learning for feature extraction and machine learning for classification.

The proposed approach combines:

- **EfficientNetB0** (pre-trained on ImageNet) for deep feature extraction
- **Support Vector Machine (SVM)** with an RBF kernel for classification
- **CLAHE-based image enhancement**
- **Data augmentation** to address class imbalance

The hybrid CNN-SVM architecture provides high classification performance while reducing computational complexity compared to training a deep neural network end-to-end.

---

## 🚀 Features

- Non-invasive anemia detection using nail and palm images
- Image enhancement using CLAHE
- Transfer learning with EfficientNetB0
- SVM classifier with RBF kernel
- Data augmentation for minority class balancing
- Performance evaluation using multiple metrics
- Memory-efficient feature extraction pipeline using TensorFlow Dataset API

---

# 📂 Dataset Structure

Place the dataset inside your Google Drive as follows:

```
dataset/
│
├── Nail/
│   ├── Anemic/
│   └── Non-Anemic/
│
└── Palm1/
    ├── Anemic/
    └── Non-Anemic/
```

Each folder should contain the corresponding image files.

---

# 🛠️ Methodology

## 1. Data Loading

- Load nail and palm images
- Convert images to RGB format
- Resize images to **224 × 224**

---

## 2. Image Preprocessing

Each image undergoes:

- RGB → YCrCb color conversion
- CLAHE (Contrast Limited Adaptive Histogram Equalization) on the luminance channel
- Merge channels
- Convert back to RGB
- Resize to **224 × 224**

This improves image contrast and highlights important visual features.

---

## 3. Train-Test Split

The dataset is divided into training and testing sets using **stratified sampling** to preserve class distribution.

```python
train_test_split(
    test_size=0.2,
    stratify=y,
    random_state=42
)
```

---

## 4. Data Augmentation

To overcome class imbalance, only the minority **Anemic** class is augmented using:

- Rotation
- Width shift
- Height shift
- Zoom
- Shear
- Horizontal flip

This improves the model's ability to generalize while reducing overfitting.

---

## 5. Feature Extraction

Deep features are extracted using a pre-trained **EfficientNetB0** model.

Configuration:

- ImageNet pretrained weights
- `include_top=False`
- Global Average Pooling
- Frozen convolutional layers

The extracted feature vectors are then used as input to the classifier.

---

## 6. Feature Scaling

The extracted features are normalized using **StandardScaler** before classification.

---

## 7. Classification

A Support Vector Machine (SVM) is trained using:

- RBF Kernel
- C = 10
- gamma = "scale"
- probability = True
- class_weight = "balanced"

This hybrid approach combines deep learning feature extraction with the robustness of SVM.

---

## 8. Model Evaluation

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- ROC Curve
- Area Under Curve (AUC)

---

# 📊 Workflow

```
Dataset
      │
      ▼
Image Preprocessing (CLAHE)
      │
      ▼
Data Augmentation
      │
      ▼
EfficientNetB0 Feature Extraction
      │
      ▼
Feature Scaling
      │
      ▼
Support Vector Machine
      │
      ▼
Prediction
      │
      ▼
Performance Evaluation
```

---

# 💻 Technologies Used

- Python
- TensorFlow 2.20
- Keras
- EfficientNetB0
- Scikit-learn
- OpenCV
- NumPy
- Matplotlib
- Seaborn

---

# 📦 Installation

Install the required packages:

```bash
pip install tensorflow==2.20.0
pip install scikit-learn
pip install opencv-python
pip install matplotlib
pip install seaborn
```

---

# ▶️ Running the Project

1. Open the notebook in **Google Colab**.

2. Mount Google Drive.

```python
from google.colab import drive
drive.mount('/content/drive')
```

3. Place the dataset inside:

```
/content/drive/MyDrive/dataset
```

4. Run all notebook cells sequentially.

The notebook performs:

- Data loading
- Image preprocessing
- Data augmentation
- Feature extraction
- Feature scaling
- Model training
- Performance evaluation

---

# 📈 Results

The proposed hybrid **EfficientNetB0 + SVM** model demonstrates excellent performance for anemia classification.

The implementation achieves:

- High Accuracy
- High Precision
- High Recall
- High F1-Score
- Excellent ROC-AUC

The combination of CLAHE preprocessing, transfer learning, and SVM classification effectively addresses class imbalance while providing robust anemia detection.

---

# 📁 Project Structure

```
Non_Invasive_Anemia_Detection/
│
├── AnemiaDetection.ipynb
├── README.md
├── requirements.txt
├── dataset/
│   ├── Nail/
│   └── Palm1/
└── results/
    ├── confusion_matrix.png
    ├── roc_curve.png
    └── sample_predictions.png
```

---

# 🔮 Future Improvements

- Mobile application for real-time anemia screening
- Lightweight deployment using TensorFlow Lite
- Integration with cloud-based healthcare systems
- Multi-class anemia severity prediction
- Explainable AI (Grad-CAM) for visualization
- Clinical validation on larger datasets

---

# 👨‍💻 Author

**Pentapati Noopura**

B.Tech Computer Science and Engineering

Project: **Non-Invasive Anemia Detection using EfficientNetB0 and SVM**

---
