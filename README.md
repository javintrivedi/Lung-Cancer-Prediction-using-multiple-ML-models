# 🫁 Lung Cancer Prediction using Multiple ML Models

An AI-powered lung cancer detection system that classifies lung CT / histopathology images as **Benign**, **Malignant**, or **Normal** using four state-of-the-art machine learning models — with a full-stack interactive web interface.

---

## 📌 Overview

Lung cancer is among the leading causes of cancer deaths worldwide. Early detection significantly improves survival chances. This project leverages deep learning and classical ML techniques to build an automated multi-class classification system trained on the **IQ-OTH/NCCD Lung Cancer Dataset**.

The `website` branch extends the research notebooks with a complete **Flask backend + HTML/CSS/JS frontend** that lets anyone upload an image and receive instant predictions from all four models simultaneously.

---

## 🤖 Models

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| **VGG16** (Transfer Learning) | 97% | 97% | 97% | 97% |
| **KNN** | 98% | 98% | 98% | 98% |
| **SVM** | 98% | 98% | 98% | 98% |
| **Hybrid CNN-SVM** | **99%** | 99% | 99% | 99% |

All models classify images into three categories:
- 🟡 **Benign** — non-cancerous tumor present
- 🔴 **Malignant** — cancerous tissue detected
- 🟢 **Normal** — no tumor detected

---

## 🗂️ Project Structure

```
lung-cancer-analysis/
│
├── 📓 Cancer_Prediction_using_vgg16_Lung_Cancer_Image_dataset.ipynb
├── 📓 Cancer_prediction_KNN_Lung_Cancer_image_dataset.ipynb
├── 📓 Cancer_prediction_SVM.ipynb
├── 📓 Cancer_prediction_hybrid.ipynb
│
├── 📄 IQ-OTH_NCCD lung cancer dataset.txt
├── 📄 README.md
│
├── backend/
│   ├── app.py                  # Flask REST API (predict, metrics, health)
│   ├── requirements.txt        # Python dependencies
│   └── export_models_guide.py  # Guide to export trained models as .h5 / .pkl
│
├── frontend/
│   ├── index.html              # LungAI web interface
│   ├── style.css               # Styling (dark mode, glassmorphism)
│   └── app.js                  # Frontend logic (upload, API calls, charts)
│
└── start.sh                    # One-command launcher for backend + frontend
```

---

## 🌐 Web Interface (LungAI)

The `website` branch includes **LungAI** — a full interactive web app:

- 📂 **Drag & Drop** image upload (JPG, PNG, BMP, TIFF)
- 🔬 **Live predictions** from all four models with per-class confidence scores
- 📊 **Model performance metrics** — accuracy, precision, recall, F1
- 📈 **Comparative analytics charts** — accuracy comparison, precision/recall/F1 bars, confusion matrices for all four models
- 🌑 Dark mode UI with glassmorphism design

---

## 🚀 Quick Start

### Prerequisites
- Python 3.9+
- `pip`

### 1. Clone the repo (website branch)

```bash
git clone --branch website https://github.com/javintrivedi/Lung-Cancer-Prediction-using-multiple-ML-models.git
cd Lung-Cancer-Prediction-using-multiple-ML-models
```

### 2. One-command launch

```bash
chmod +x start.sh
./start.sh
```

This will:
1. Create a Python virtual environment in `backend/venv/`
2. Install Flask, Pillow, and NumPy
3. Start the Flask API at `http://localhost:5000`
4. Serve the frontend at `http://localhost:8080`
5. Automatically open the app in your browser

---

## 🔧 Manual Setup

### Backend

```bash
cd backend
python3 -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

The API will be available at `http://localhost:5000`.

### Frontend

```bash
cd frontend
python3 -m http.server 8080
```

Open `http://localhost:8080` in your browser.

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/health` | Health check |
| `POST` | `/predict` | Upload image → get predictions from all 4 models |
| `GET` | `/metrics` | Fetch performance metrics for all models |

### Example: `/predict` Response

```json
{
  "prediction": "Malignant",
  "confidence": 0.8923,
  "simulated": true,
  "model_results": {
    "VGG16":         { "prediction": "Malignant", "confidence": 0.91, "probabilities": {...} },
    "KNN":           { "prediction": "Malignant", "confidence": 0.88, "probabilities": {...} },
    "SVM":           { "prediction": "Malignant", "confidence": 0.87, "probabilities": {...} },
    "Hybrid CNN-SVM":{ "prediction": "Malignant", "confidence": 0.93, "probabilities": {...} }
  }
}
```

> **Note:** When trained model files (`vgg16_model.h5`, `knn_model.pkl`, etc.) are not present in `backend/models/`, the API uses a deterministic simulation based on image content. See `backend/export_models_guide.py` for instructions on exporting your trained models.

---

## 📦 Dependencies

```
flask==3.0.3
flask-cors==4.0.0
tensorflow==2.16.1
scikit-learn==1.4.2
Pillow==10.3.0
numpy==1.26.4
```

---

## 📊 Dataset

**IQ-OTH/NCCD Lung Cancer Dataset**
- CT scan images labeled as Benign, Malignant, and Normal
- 80:20 train/test split with data augmentation

See `IQ-OTH_NCCD lung cancer dataset.txt` for dataset details and source.

---

## ⚠️ Disclaimer

This tool is built for **academic and research purposes only**. It is **not a substitute for professional medical diagnosis**. Always consult a qualified medical professional for clinical decisions.

---

## 👤 Author

**Javin Trivedi**
[GitHub](https://github.com/javintrivedi)
