# 📈 Stock Market Trend Prediction

A complete machine learning pipeline to analyze and predict stock market trends using historical data and advanced time series models.

![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-Production-blue.svg)
![Made with](https://img.shields.io/badge/Made%20with-Python-orange.svg)

---

## 🔍 Overview

This project aims to predict future stock price trends using supervised learning algorithms including LSTM, SVM, and Random Forest. It integrates data preprocessing, model training, evaluation, and insightful visualizations.

---

## 📊 Key Features

- 📅 Time series forecasting using **LSTM** models
- 🔍 Technical analysis indicators (SMA, EMA, RSI)
- 📈 Visualization of trends, volatility, and momentum
- 💡 Comparative study using SVM, Random Forest, and baseline models
- ✅ Cleaned and prepared data pipeline for reproducibility

---

## 🧠 Model Insights

### LSTM (Long Short-Term Memory)
- Best suited for sequence modeling, used here to learn from past stock prices.
- Captures temporal dependencies in daily stock movement.
- Produces future price trend predictions for 'n' steps ahead.

### Random Forest
- Ensemble method providing feature importance.
- Effective in short-term up/down trend classification.

### Support Vector Machine (SVM)
- Used for trend direction classification (up/down).
- Effective on high-dimensional data after feature engineering.

---

## 🖼️ Visual Outputs

| 📌 Insight                  | 📊 Chart |
|----------------------------|----------|
| Training & Validation Loss | ![loss](assets/loss_plot.png) |
| Predicted vs Actual Prices | ![pred](assets/prediction_vs_actual.png) |
| Trend Classification       | ![trend](assets/trend_classification.png) |

---

## 📁 Project Structure

```
├── data/                # Raw and cleaned CSV files
├── models/              # Saved model weights
├── notebooks/           # EDA, modeling, LSTM training
├── utils/               # Helper scripts (e.g., indicators, preprocess)
├── assets/              # Images and plots
├── app.py               # Streamlit dashboard (if available)
└── README.md            # Project documentation
```

---

## 📦 Dataset

- Historical stock data fetched from **Yahoo Finance** and **Kaggle**.
- Example: [NSE Stock Data](https://www.kaggle.com/datasets/)

*Only a sample subset is uploaded due to GitHub size restrictions.*

---

## 🛠️ Technologies Used

- Python, Pandas, NumPy
- Matplotlib, Seaborn, Plotly
- TensorFlow / Keras
- Scikit-learn
- Streamlit (for optional dashboard)

---

## 🤖 Future Enhancements

- Integrate real-time API for live stock predictions
- Add sentiment analysis from Twitter or news
- Incorporate ARIMA or Prophet models for hybrid forecasting

---

## 📚 References

- *Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow* - Aurélien Géron
- Blogs from TowardsDataScience, Analytics Vidhya
- Kaggle community notebooks and kernels
- GPT-4 for optimization, formatting, and markdown generation

---

## 🙌 Contribution

Feel free to fork and raise PRs for any enhancements! Star ⭐ the repo if you find it useful.

---

## 📬 Contact

Author: Pavan Kumar  
Email: [nallabothulapavan05@gmail.com](mailto:nallabothulapavan05@gmail.com)  
Portfolio: [npk05.github.io/portfolio](https://npk05.github.io/portfolio)