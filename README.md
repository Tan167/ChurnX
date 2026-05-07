# 📉 ChurnX — Telco Customer Churn Prediction Platform

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![scikit-learn](https://img.shields.io/badge/Scikit--Learn-1.5.2-orange?style=for-the-badge&logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-3.0-red?style=for-the-badge)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-green?style=for-the-badge&logo=fastapi)
![MLflow](https://img.shields.io/badge/MLflow-2.14-blue?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**An end-to-end ML pipeline for predicting customer churn in the telecom industry — from raw data to a production-ready REST API.**

[Features](#-features) • [Architecture](#-architecture) • [Tech Stack](#-tech-stack) • [Setup](#-quick-start) • [API](#-api-usage)

</div>

---

## 🚀 What is ChurnX?

ChurnX is a production-grade machine learning system that predicts which telecom customers are likely to churn — enabling retention teams to act before it's too late.

It covers the **full ML lifecycle**:
- 📊 Exploratory Data Analysis (EDA)
- ⚙️ Feature engineering pipeline
- 🤖 Model training with hyperparameter tuning (Optuna)
- 📈 Experiment tracking (MLflow)
- ✅ Data validation (Great Expectations)
- 🚀 REST API serving (FastAPI)
- 🖥️ Interactive demo UI (Gradio)
- 🐳 Docker deployment

---

## ✨ Features

| Feature | Description | Tech |
|---------|-------------|------|
| 📊 EDA Notebook | Deep dive into churn patterns and feature distributions | Jupyter, Seaborn, Matplotlib |
| ⚙️ Feature Pipeline | Automated feature engineering and preprocessing | Scikit-learn Pipelines |
| 🤖 Multi-Model Training | XGBoost, LightGBM, and Scikit-learn models compared | XGBoost, LightGBM |
| 🔍 Hyperparameter Tuning | Automated tuning with Optuna | Optuna |
| 📈 Experiment Tracking | All runs logged with metrics and artifacts | MLflow |
| ✅ Data Validation | Schema and quality checks on input data | Great Expectations |
| 🚀 REST API | Production-ready prediction endpoint | FastAPI + Uvicorn |
| 🖥️ Demo UI | Interactive prediction interface | Gradio |
| 🐳 Containerized | One-command deployment | Docker |
| 🔄 CI/CD | Automated testing and workflows | GitHub Actions |

---

## 🏗️ Architecture

```
Raw Telco Data
      ↓
Data Validation (Great Expectations)
      ↓
Feature Engineering Pipeline
      ↓
Model Training → XGBoost / LightGBM / Sklearn
      ↓
Hyperparameter Tuning (Optuna)
      ↓
Experiment Tracking (MLflow)
      ↓
Best Model Selected
      ↓
┌─────────────────────┐
│   FastAPI REST API  │  ← Production serving
└─────────────────────┘
│   Gradio Demo UI    │  ← Interactive demo
└─────────────────────┘
```

---

## 📁 Project Structure

```
ChurnX/
│
├── notebooks/
│   └── EDA.ipynb                  # Exploratory data analysis
│
├── scripts/
│   ├── prepare_processed_data.py  # Data preprocessing
│   ├── run_pipeline.py            # Full training pipeline
│   ├── test_fastapi.py            # API tests
│   ├── test_pipeline_phase1.py    # Pipeline unit tests
│   └── test_pipeline_phase2.py    # Integration tests
│
├── src/
│   ├── app/                       # FastAPI application
│   ├── data/                      # Data loading & validation
│   ├── features/                  # Feature engineering
│   ├── models/                    # Model training & evaluation
│   ├── serving/                   # Prediction serving logic
│   └── utils/                     # Shared utilities
│
├── .github/workflows/             # CI/CD pipelines
├── dockerfile                     # Docker configuration
├── requirements.txt
└── README.md
```

---

## 🛠️ Tech Stack

```
ML Framework      →  Scikit-learn, XGBoost, LightGBM
Experiment Track  →  MLflow
Hyperparameter    →  Optuna
Data Validation   →  Great Expectations
API Serving       →  FastAPI + Uvicorn + Gunicorn
Demo UI           →  Gradio
Data Processing   →  Pandas, NumPy
Visualization     →  Matplotlib, Seaborn
Statistical       →  Statsmodels, SciPy
Containerization  →  Docker
CI/CD             →  GitHub Actions
```

---

## ⚡ Quick Start

### 1. Clone the repo
```bash
git clone https://github.com/Tan167/ChurnX.git
cd ChurnX
```

### 2. Create virtual environment
```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the full pipeline
```bash
python scripts/run_pipeline.py
```

### 5. Start the API server
```bash
uvicorn src.app.main:app --reload --port 8000
```

### 6. Launch Gradio demo
```bash
python src/app/gradio_app.py
```

---

## 🐳 Docker

```bash
# Build image
docker build -t churnx .

# Run container
docker run -p 8000:8000 churnx
```

---

## 🔌 API Usage

### Predict churn for a customer

```bash
POST /predict
```

```json
{
  "tenure": 24,
  "MonthlyCharges": 65.5,
  "TotalCharges": 1572.0,
  "Contract": "Month-to-month",
  "InternetService": "Fiber optic",
  "PaymentMethod": "Electronic check",
  "TechSupport": "No",
  "OnlineSecurity": "No"
}
```

**Response:**
```json
{
  "churn_probability": 0.82,
  "churn_prediction": true,
  "risk_level": "High",
  "confidence": 0.91
}
```

## 📊 Model Performance

| Model | Accuracy | ROC-AUC | Precision | Recall |
|-------|----------|---------|-----------|--------|
| XGBoost | ~80% | ~0.85 | ~0.78 | ~0.82 |
| LightGBM | ~79% | ~0.84 | ~0.77 | ~0.81 |
| Logistic Regression | ~76% | ~0.81 | ~0.74 | ~0.78 |

> Exact metrics depend on train/test split and hyperparameter tuning run.

---

## 📈 MLflow Experiment Tracking

All training runs are tracked with MLflow. To view the dashboard:

```bash
mlflow ui
```
Open **http://localhost:5000** to compare runs, metrics, and artifacts.




<div align="center">
Built with ❤️ using Python, Scikit-learn, XGBoost, FastAPI and MLflow
</div>
