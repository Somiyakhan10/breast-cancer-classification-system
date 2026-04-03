# 🔬 OncoPredict — Breast Cancer Classification System

**AI-Powered Diagnostic Tool · By Somiya Khan**

---

<div align="center">

![Accuracy](https://img.shields.io/badge/Accuracy-96.49%25-brightgreen)
![ROC-AUC](https://img.shields.io/badge/ROC--AUC-99.42%25-blue)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![Flask](https://img.shields.io/badge/Flask-3.1-black)
![MIT License](https://img.shields.io/badge/License-MIT-green)

</div>

---

> ⚠️ **Medical Disclaimer:** This tool is a demonstration model and is **NOT** intended for medical diagnosis. Always consult a qualified medical professional.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Live Demo](#-live-demo)
- [Screenshots](#-screenshots)
- [Model Performance](#-model-performance)
- [Dataset](#-dataset)
- [How It Works](#-how-it-works)
- [Technology Stack](#-technology-stack)
- [Installation](#-installation)
- [API Reference](#-api-reference)
- [Author](#-author)
- [License](#-license)

---

## 🔬 Overview

**OncoPredict** is an AI-powered web application that classifies breast tumors as **Benign** or **Malignant** using 30 computed features from Fine Needle Aspirate (FNA) biopsy images.

The system uses a **Random Forest Classifier** trained on the Wisconsin Breast Cancer Diagnostic Dataset, achieving **96.49% accuracy** and **99.42% ROC-AUC**.

---

## 🌐 Live Demo

The application is live and accessible at:

```
https://somiya-khan01-cancer-detection.hf.space
```

---

## 📸 Screenshots

### Home / Predict Page

*Interactive form with 30 adjustable features organized into Mean, Standard Error, and Worst categories*

<img width="1895" height="870" alt="image" src="https://github.com/user-attachments/assets/87301233-672c-46cf-a02b-26fa80d06d65" />


### Dashboard

*Model performance metrics, confusion matrix, and feature importance visualization*

<img width="1320" height="878" alt="image" src="https://github.com/user-attachments/assets/abc873bd-b753-4467-8367-13a49a543274" />


### About Page

*Project information, dataset details, and methodology*
<img width="1003" height="741" alt="image" src="https://github.com/user-attachments/assets/c861e91d-8b2f-484b-b4d8-27667e0f9e95" />


---

## 📊 Model Performance

| Metric | Value |
|--------|-------|
| **Accuracy** | 96.49% |
| **Precision** | 100.0% |
| **Recall** | 90.48% |
| **F1 Score** | 95.0% |
| **ROC-AUC** | 99.42% |

### Confusion Matrix

| | Predicted Benign | Predicted Malignant |
|---|-----------------|---------------------|
| **Actual Benign** | TN | FP |
| **Actual Malignant** | FN | TP |

### Top 10 Feature Importances

1. perimeter_worst
2. area_worst
3. concave points_worst
4. concave points_mean
5. (Additional features from Random Forest model)

---

## 📊 Dataset

| Property | Details |
|----------|---------|
| **Name** | Wisconsin Breast Cancer Dataset |
| **Source** | UCI ML Repository / Kaggle |
| **Total Samples** | 569 patient records |
| **Class Distribution** | 357 Benign (63%), 212 Malignant (37%) |
| **Features** | 30 computed features from digitized FNA images |
| **Missing Values** | None |

### Feature Categories

| Category | Description |
|----------|-------------|
| **Mean** | Average value across all nuclei in the sample |
| **Standard Error (SE)** | Statistical uncertainty of the measurement |
| **Worst** | The largest (most extreme) value found in the sample |

### Base Measurements (10 features × 3 categories = 30 features)

- Radius
- Texture
- Perimeter
- Area
- Smoothness
- Compactness
- Concavity
- Concave Points
- Symmetry
- Fractal Dimension

---

## ⚙️ How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                      USER INTERFACE                            │
│   User adjusts 30 sliders OR loads sample data                 │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      FRONTEND (React)                          │
│   Collects features → Sends POST request to /api/predict       │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BACKEND (Flask)                           │
│   Validates input → Scales features → Model prediction         │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                   RANDOM FOREST MODEL                          │
│   Returns: { label, confidence, probabilities }                │
└─────────────────────────┬───────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      RESULT DISPLAY                            │
│   Shows: Benign/Malignant, Confidence %, Probability bars      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

| Layer | Technology |
|-------|------------|
| **Machine Learning** | scikit-learn (Random Forest) |
| **Preprocessing** | StandardScaler |
| **Backend** | Flask 3.1 |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Charts** | Chart.js |
| **Deployment** | Hugging Face Spaces (Docker) |

---

## 📁 Project Structure

```
oncopredict/
│
├── app.py                 # Flask application + model training
├── data.csv               # Wisconsin Breast Cancer dataset
├── requirements.txt       # Python dependencies
├── Dockerfile             # Container configuration
├── README.md              # Documentation
│
├── templates/
│   └── index.html         # Main UI template
│
└── static/
    ├── css/
    │   └── style.css      # Stylesheet
    └── js/
        └── app.js         # Frontend logic + charts
```

---

## 🚀 Installation

### Prerequisites

- Python 3.10 or higher
- pip package manager

### Local Setup

```bash
# Clone the repository
git clone https://huggingface.co/spaces/somiya-khan01/cancer-detection

# Navigate to project directory
cd cancer-detection

# Install dependencies
pip install -r requirements.txt

# Run the application
python app.py

# Open browser and go to http://localhost:7860
```

### Dependencies

```
flask>=2.3.0
pandas>=1.5.0
numpy>=1.23.0
scikit-learn>=1.2.0
```

---

## 📡 API Reference

### GET `/api/health`

Health check endpoint.

**Response:**
```json
{
  "status": "ok",
  "service": "OncoPredict API",
  "author": "Somiya Khan"
}
```

### GET `/api/features`

Returns all 30 feature names.

**Response:**
```json
{
  "features": ["radius_mean", "texture_mean", ...]
}
```

### GET `/api/sample?type=benign`

Returns sample patient data (benign or malignant).

**Response:**
```json
{
  "radius_mean": 9.5,
  "texture_mean": 15.2,
  ...
}
```

### POST `/api/predict`

Send 30 features for classification.

**Request Body:**
```json
{
  "radius_mean": 17.99,
  "texture_mean": 10.38,
  ...
}
```

**Response:**
```json
{
  "label": "Malignant",
  "confidence": 98.24,
  "malignant_prob": 98.24,
  "benign_prob": 1.76
}
```

---

## 👩‍🔬 Author

**Somiya Khan**

Biomedical Engineer | AI/ML Enthusiast

---

## 📄 License

This project is licensed under the **MIT License**.

---

## ⚕️ Final Note

This tool is developed for **educational and research purposes only**. It is not a substitute for professional medical advice, diagnosis, or treatment. Always seek the advice of a qualified healthcare provider with any questions about a medical condition.

---

<div align="center">

**Built with ❤️ by Somiya Khan**

⭐ If you find this project useful, please consider giving it a star on Hugging Face!

</div>

---

## 📝 Acknowledgments

- **Dataset:** Wisconsin Breast Cancer Dataset — UCI Machine Learning Repository
- **Donated by:** Dr. William H. Wolberg, University of Wisconsin Hospitals
- **Inspired by:** The need for interpretable AI in medical diagnostics

---
