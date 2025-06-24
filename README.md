
# 📈 Stock Market Trend Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Project-Complete-brightgreen)
![Model](https://img.shields.io/badge/Model-LSTM%20%7C%20SVM%20%7C%20RF-orange)
![Deployed](https://img.shields.io/badge/Interface-Flask-blue)

> End-to-end stock trend prediction using classical ML (SVM, RF) and deep learning (LSTM) models. Includes a Flask web interface.

---

## 🧩 Table of Contents

1. [Overview](#overview)  
2. [Installation](#installation)  
3. [Usage](#usage)  
4. [Model Insights](#model-insights)  
5. [Visualizations](#visualizations)  
6. [Project Structure](#project-structure)  
7. [Dependencies](#dependencies)  
8. [License](#license)

---

## 📌 Overview

This project predicts short-term stock market trends based on historical financial data using:
- 🧠 ML Models: **Random Forest**, **Support Vector Machine (SVM)**  
- 🔁 Deep Learning: **LSTM Recurrent Neural Networks**
- 🌐 Flask web app for interactive user input and predictions
- 📉 Technical indicators for trend classification

---

## ⚙️ Installation

Clone the repo and install dependencies:

```bash
git clone https://github.com/NPK05/Stock-Market-Trend-Prediction.git
cd Stock-Market-Trend-Prediction
pip install -r requirements.txt
```

---

## 🚀 Usage

### Run the Flask Web App:

```bash
python app.py
```

Visit `http://127.0.0.1:5000` to upload stock data and get predictions using selected models.

---

## 🧠 Model Insights

- **Random Forest & SVM**
  - Used for **classification** of short-term price direction (Up/Down)
  - Offers explainable insights via feature importance
- **LSTM**
  - Trained for **regression-based forecasting**
  - Captures sequential price movements

All models are saved in `model/` directory for reuse.

---

## 📊 Visualizations

| 🔍 Feature                  | 🖼️ Sample Output                              |
|----------------------------|-----------------------------------------------|
| Prediction vs Actual       | `outputs/predictions.png`                     |
| LSTM Training Loss Curve   | `outputs/loss_curve.png`                      |
| Confusion Matrix (SVM)     | `outputs/confusion_matrix.png` (if created)   |

---

## 🗂️ Project Structure

```
Stock-Market-Trend-Prediction/
├── app.py                       # Flask application
├── train_models.py              # ML training script
├── utils.py                     # Preprocessing, feature generation
├── upload.csv                   # Sample input file
├── model/                       # Stored model files (.pkl)
├── outputs/                     # Plots, forecasts, metrics
├── templates/                   # HTML forms for the web interface
├── static/                      # CSS, JS, and visual assets
├── requirements.txt             # Package dependencies
└── README.md
```

---

## 📦 Dependencies

- `pandas`, `numpy`, `scikit-learn`
- `matplotlib`, `seaborn`
- `tensorflow` / `keras` (for LSTM)
- `flask`, `joblib`, `yfinance`

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 👤 Author

**Pavan Kumar Nallabothula**  
📧 nallabothulapavan05@gmail.com  
🌐 [Portfolio Website](https://npk05.github.io/portfolio/)  
🔗 [LinkedIn](https://www.linkedin.com/in/pavan-nallabothula/)
