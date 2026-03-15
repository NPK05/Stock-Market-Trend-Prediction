# 📈 Stock Market Trend Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-orange?style=flat-square&logo=scikit-learn)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=flat-square&logo=tensorflow)
![Flask](https://img.shields.io/badge/Flask-2.x-black?style=flat-square&logo=flask)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)

> An end-to-end machine learning and deep learning system for forecasting NSE NIFTY sector indices — built with 8 algorithms on 8,918+ real trading records spanning 2003 to 2021.

🌐 **Live Demo:** [npk05.github.io/Stock-Market-Trend-Prediction](https://npk05.github.io/Stock-Market-Trend-Prediction/)

---

## Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [ML Models & Algorithms](#ml-models--algorithms)
- [Statistical Methods](#statistical-methods)
- [Visualizations](#visualizations)
- [Predictions](#predictions)
- [Business Recommendations](#business-recommendations)
- [Future Enhancements](#future-enhancements)
- [Tech Stack](#tech-stack)
- [Installation & Setup](#installation--setup)
- [Author](#author)

---

## Overview

Stock markets are driven by countless interacting factors, making reliable price direction signals difficult to identify from raw data alone. This project builds a comprehensive, end-to-end stock market trend prediction system targeting three NSE NIFTY sector indices:

- **NIFTY IT** — India's technology sector (TCS, Infosys, Wipro, HCL)
- **NIFTY Metal** — Metals and mining sector (JSW Steel, Tata Steel, Hindalco)
- **NIFTY Financial Services** — Banking and finance sector (HDFC Bank, ICICI, Bajaj Finance)

The system applies a multi-model ML framework — including classical regression, support vector machines, ensemble methods, and LSTM deep learning — to forecast closing prices and classify short-term price direction. All results are served through an interactive Flask web interface and an interactive HTML dashboard.

---

## Live Demo

The project is deployed as a static interactive dashboard:

**[https://npk05.github.io/Stock-Market-Trend-Prediction/](https://npk05.github.io/Stock-Market-Trend-Prediction/)**

### Dashboard Tabs

| Tab | Description |
|-----|-------------|
| 📊 Dataset | Data files, schema, index summaries |
| 🎯 Problem & Objectives | Business problem, abstract, scope |
| 🤖 ML Models | All 8 algorithms with comparison table |
| 📈 Visualizations | 6 interactive charts (Candlestick, OHLC, Heikin-Ashi, Volume, Line, Grouped Bar) |
| 📐 Statistical Methods | 12 mathematical foundations with formulas |
| 🔮 Predictions | Live date-based prediction with model comparison |
| 💼 Business Rec. | 8 actionable investment recommendations |
| 🚀 Future Enhancements | 6-phase production roadmap |
| 📬 Contact | Author details and links |

---

## Dataset

### Sources

| File | Index | Records | Period |
|------|-------|---------|--------|
| `NIFTY.csv` | All 3 Indices | 8,918 | 2003–2021 |
| `NIFTY IT_data.csv` | NIFTY IT | 4,355 | 2003–2021 |
| `NIFTY FIN SERVICE_data.csv` | NIFTY Financial Services | 2,232 | 2012–2021 |
| `NIFTY METAL_data.csv` | NIFTY Metal | 2,331 | 2011–2021 |

### Schema

| Column | Type | Description |
|--------|------|-------------|
| `Date` | datetime | Trading date (DD-MM-YYYY) |
| `Open` | float64 | Opening price of the index |
| `High` | float64 | Intraday highest price |
| `Low` | float64 | Intraday lowest price |
| `Close` | float64 | Closing price — **TARGET variable** |
| `Volume` | int64 | Number of shares/contracts traded |
| `Turnover` | float64 | Notional value of trades (INR) |
| `Indices` | string → int | NIFTY sub-index label (label-encoded) |

### Key Data Observations

- **NIFTY IT** surged +90% in 2020–2021 driven by global work-from-home demand
- **NIFTY Metal** is highly cyclical and correlated with global commodity prices
- **NIFTY Financial Services** shows the most consistent long-term growth trajectory (+3.66× from 2012 to 2021)
- **COVID-19 Impact**: Mar 2020 saw a sharp drop across all indices, followed by full recovery within 4 months

---

## Project Structure

```
Stock-Market-Trend-Prediction/
│
├── app/
│   ├── app.py                  # Flask application & route handlers
│   ├── utils.py                # All ML model functions & preprocessing
│   ├── train_models.py         # Orchestration: trains models, returns predictions
│   ├── poly.pkl                # Serialised PolynomialFeatures (degree=2)
│   ├── regressor.pkl           # Serialised RandomForestRegressor (15 trees)
│   └── upload.csv              # Sample input CSV for testing
│
├── data/
│   ├── model/
│   │   ├── NIFTY.csv           # Primary multi-index dataset (8,918 rows)
│   │   └── Untitled3.ipynb     # Exploratory modelling notebook
│   └── individual_stocks_5yr/
│       ├── NIFTY FIN SERVICE_data.csv
│       ├── NIFTY IT_data.csv
│       └── NIFTY METAL_data.csv
│
├── static/
│   ├── css/                    # Bootstrap + SB Admin 2 stylesheets
│   ├── js/                     # Chart.js demo scripts & custom main.js
│   └── scss/                   # SCSS source files
│
├── index.html                  # Interactive dashboard (GitHub Pages)
├── requirements.txt            # Python package dependencies
└── README.md                   # This file
```

---

## ML Models & Algorithms

Eight prediction models are implemented across three families. All classical models share a unified interface in `utils.py`.

### Model Performance Summary

| Algorithm | Type | Key Hyperparameters | Expected R² | Strength | Limitation |
|-----------|------|---------------------|-------------|----------|------------|
| **Random Forest** | Ensemble | n_estimators=15, poly deg=2 | 0.97–0.99 | Non-linear, feature importance | Can overfit |
| **LSTM** | Deep Learning | look_back=1, MinMaxScaler | 0.95–0.99 | Captures temporal dependencies | Needs large data |
| **SVR (RBF)** | SVM | C=1000, γ=0.1 | 0.90–0.96 | Robust to outliers | Slow on large datasets |
| **SVR (Linear)** | SVM | C=1000 | 0.85–0.92 | Fast, stable baseline | Misses non-linearity |
| **Linear Regression** | Baseline | — | 0.85–0.93 | Interpretable | Linear assumption only |
| **ElasticNet** | Regularised | L1+L2, random_state=0 | 0.82–0.90 | Less prone to overfitting | Linear assumption |
| **KNN** | Instance-based | k=2 | 0.70–0.85 | No training phase | Sensitive to noise |
| **Decision Tree** | Baseline | Unpruned CART | 0.95–1.0 (train) | Fully interpretable | Overfits on unseen data |

### Preprocessing Pipeline

```
Raw CSV Data
    │
    ├─ 1. Date Parsing         → Year, Month, Day, DayOfWeek, WeekOfYear
    ├─ 2. Label Encoding       → Indices (NIFTY IT / METAL / FIN) → 0, 1, 2
    ├─ 3. Feature Selection    → X = [Day, Month, Year, Indices]
    ├─ 4. Polynomial Expansion → PolynomialFeatures(degree=2): 4 → 15 features
    ├─ 5. MinMax Scaling       → Applied for LSTM path [0, 1] range
    ├─ 6. Look-Back Windowing  → create_dataset(look_back=1): X[t] → Y[t+1]
    └─ 7. Train-Test Split     → 67% train / 33% test (random for classical)
                                  Sequential split for LSTM (last 2 rows = test)
```

---

## Statistical Methods

Twelve statistical and mathematical techniques underpin the system:

| Method | Formula | Purpose |
|--------|---------|---------|
| Mean Squared Error | `Σ(yᵢ − ŷᵢ)² / n` | Primary evaluation metric |
| R² Score | `1 − SS_res / SS_tot` | Variance explained by model |
| Polynomial Feature Expansion | `PolyFeatures(degree=2)(X)` | Non-linear feature creation |
| Label Encoding | `LabelEncoder().fit_transform()` | Categorical → numeric |
| Min-Max Normalisation | `(x − min) / (max − min)` | Scale to [0,1] for LSTM |
| Sliding Window | `X[t] = close[t:t+k]` | Time-series supervision |
| Train-Test Split | `test_size=0.33` | Generalisation evaluation |
| Heikin-Ashi | `HA_Close = (O+H+L+C)/4` | Noise reduction in charts |
| Bootstrap Aggregating | `avg(Tree₁...Treeₙ)` | Random Forest variance reduction |
| ElasticNet Regularisation | `MSE + α·ρ·‖β‖₁ + α(1−ρ)/2·‖β‖₂²` | L1+L2 penalty |
| LSTM BPTT | `∂L/∂W = Σ ∂Lₜ/∂W` | Gradient-based LSTM training |
| Temporal Decomposition | `Date → {Year, Month, Day, ...}` | Seasonal pattern learning |

---

## Visualizations

Six production-grade charts built using real NIFTY dataset values (Chart.js):

| # | Chart | Index | Period | Key Insight |
|---|-------|-------|--------|-------------|
| 1 | Candlestick Chart | NIFTY IT | Dec 2020 – Feb 2021 | +18.6% bull rally in 3 weeks |
| 2 | Long-Term Line Chart | NIFTY IT | 2003–2021 | Full 18-year market cycle view |
| 3 | OHLC Bar Chart | NIFTY Metal | Jan–Feb 2021 | +27.7% breakout run |
| 4 | Heikin-Ashi Chart | NIFTY Fin Services | Dec 2020 – Feb 2021 | 50 consecutive bullish candles |
| 5 | Volume vs Price | NIFTY IT | Dec 2020 – Feb 2021 | Jan 11: 100.7M volume breakout |
| 6 | Yearly Grouped Bar | All 3 Indices | 2012–2021 | IT 3× outperformance vs Metal |

---

## Predictions

The prediction engine runs two modes:

### 1. Date-Based Rapid Inference (`/predict` route)
Uses the serialised pipeline (`poly.pkl` + `regressor.pkl`) for sub-second inference:
```python
# User inputs: Day, Month, Year, Index
X = np.array([[day, month, year, index_encoded]])
X_poly = pol.transform(X)          # Apply saved PolynomialFeatures
prediction = regresso.predict(X_poly)   # RandomForestRegressor
```

### 2. Multi-Model Comparison (Dashboard)
Runs all 5 algorithms on a selected date and plots predicted vs actual close price with MSE ranking:

| Rank | Model | Approx. MSE | Notes |
|------|-------|-------------|-------|
| 1 | LSTM | ~28,000 | Best — sequential awareness |
| 2 | Random Forest | ~34,000 | Close second — polynomial features help |
| 3 | SVR (RBF) | ~52,800 | Non-linear kernel advantage |
| 4 | Linear Regression | ~67,400 | Strong interpretable baseline |
| 5 | KNN (k=2) | ~124,600 | Highest variance on volatile days |

---

## Business Recommendations

Eight actionable strategies derived from model analysis:

1. **Use LSTM for short-term signals** — lowest MSE; deploy for 1–5 day ahead forecasting
2. **Use Random Forest for explainability** — SHAP-compatible; required for SEBI audit trails
3. **Sector rotation strategy** — use multi-index model to allocate capital across IT/Metal/Finance based on predicted momentum
4. **Integrate volatility filters** — pause signals when ATR exceeds 2× its 20-day average
5. **Retrain monthly with walk-forward validation** — prevents data leakage on shifting market regimes
6. **Backtest before live deployment** — track Sharpe ratio, max drawdown, and win rate
7. **Auto-fetch live data via yfinance** — daily 4 PM IST pipeline (yfinance already in requirements.txt)
8. **Add fundamental overlay** — event calendar filter for budget days, RBI policy, earnings releases

> ⚠️ **Disclaimer:** This project is for educational and research purposes only. All predictions are based on historical data and statistical models. Past performance does not guarantee future results. Stock market investments involve risk including potential loss of principal.

---

## Future Enhancements

A 6-phase roadmap to transform this into a production-grade system:

### Phase 1 — Authentication Layer
Add Flask-Login / JWT so multiple analysts can log in with personal dashboards. After 30+ prediction inputs, the system automatically identifies which algorithm performs best for each user's selected stocks.

**Stack:** Flask-Login · SQLite/PostgreSQL · Per-user accuracy tracking

### Phase 2 — Adaptive Algorithm Selection
Track rolling 30-day accuracy per model per user. Automatically promote the best-performing algorithm to "Recommended" and demote underperformers. Users can override manually.

**Stack:** Rolling MSE tracker · Auto-recommendation engine

### Phase 3 — Real-Time Data Pipeline
```python
# Daily 4 PM IST cron job
import yfinance as yf
ticker = yf.Ticker("^CNXIT")
df = ticker.history(period="1d")
# → append to dataset → re-engineer features → retrain models → push via WebSocket
```
**Stack:** APScheduler · yfinance · pandas · joblib · Flask-SocketIO

### Phase 4 — Technical Indicators
The `ta` library is already in `requirements.txt` but unused. Add:
- **Momentum:** RSI(14), MACD, MACD Signal
- **Volatility:** Bollinger Bands, ATR(14)
- **Volume:** OBV, MFI

### Phase 5 — NLP & Sentiment Analysis
Integrate NewsAPI for financial headlines → FinBERT sentiment classification → add sentiment score as an ML feature. Studies show this improves short-term accuracy by 8–15%.

**Stack:** NewsAPI · FinBERT (HuggingFace) · Sentiment feature pipeline

### Phase 6 — Production Deployment
Containerise with Docker, deploy on AWS EC2 or Azure App Service, expose as a REST API via FastAPI, and add CI/CD with GitHub Actions.

**Stack:** Docker · FastAPI · AWS/Azure · GitHub Actions

---

## Tech Stack

### Core ML & Data
| Package | Purpose |
|---------|---------|
| `pandas` | Data loading, manipulation, feature extraction |
| `numpy` | Numerical arrays and matrix operations |
| `scikit-learn` | All classical ML models + preprocessing |
| `tensorflow` / `keras` | LSTM deep learning model |
| `matplotlib` | Plot generation |
| `seaborn` | Statistical visualisations |

### Web Application
| Package | Purpose |
|---------|---------|
| `flask` | Web application framework |
| `joblib` | Efficient model serialisation |
| `werkzeug` | File upload handling |

### Data & Indicators
| Package | Purpose |
|---------|---------|
| `yfinance` | Yahoo Finance API for live data |
| `ta` | Technical analysis indicator library |
| `streamlit` | Alternative dashboard UI |

### Dashboard (Frontend)
| Library | Purpose |
|---------|---------|
| Chart.js 4.4 | All 6 interactive charts |
| Syne + DM Sans | Typography |
| Vanilla CSS/JS | Sidebar nav, tab switching, ticker |

---

## Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager
- ~1 GB disk space (TensorFlow)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/NPK05/Stock-Market-Trend-Prediction.git
cd Stock-Market-Trend-Prediction

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Navigate to the app directory
cd app

# 5. Run the Flask application
python app.py
```

Visit `http://127.0.0.1:5000` in your browser.

### Or view the static dashboard
Simply open `index.html` directly in any modern browser — no server required. All charts and interactions run client-side via Chart.js.

---

## Requirements

```
pandas
numpy
matplotlib
scikit-learn
tensorflow
keras
seaborn
yfinance
ta
streamlit
joblib
flask
```

---

## Author

**Pavan Kumar Nallabothula**
Data Analyst · Machine Learning · Financial Analytics

| | |
|--|--|
| 📧 Email | [npavankumarus72@gmail.com](mailto:npavankumarus72@gmail.com) |
| 💼 LinkedIn | [linkedin.com/in/nallabothulapavankumar-data-analyst](https://www.linkedin.com/in/nallabothulapavankumar-data-analyst/) |
| 🌐 Live Project | [npk05.github.io/Stock-Market-Trend-Prediction](https://npk05.github.io/Stock-Market-Trend-Prediction/) |
| 🐙 GitHub | [github.com/NPK05](https://github.com/NPK05) |

---

## License

This project is licensed under the **MIT License** — feel free to use, modify, and distribute with attribution.

---

<div align="center">

**Built with ❤️ for data-driven financial analysis**

*For educational purposes only · Not financial advice*

</div>
