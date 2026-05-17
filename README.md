# 📈 NSE Stock Time Series Analysis & Portfolio Forecasting

<div align="center">

<h3>📊 Time Series Forecasting • 📈 Portfolio Optimization • 💹 NSE Stock Analysis</h3>

</div>

---

# 📌 Project Overview

This project presents a comprehensive **Time Series Analysis and Forecasting Pipeline** for selected **NSE (National Stock Exchange of India)** stocks using statistical forecasting models and portfolio optimization techniques.

The notebook performs:

- 📥 Historical stock data acquisition
- 🧹 Data preprocessing and cleaning
- 📈 ARIMA-based forecasting
- 🤖 Facebook Prophet forecasting
- 📊 Volatility and trend analysis
- 💼 Portfolio construction strategies
- 📉 Forecast evaluation and performance tracking
- 📑 Dashboard visualization and PDF report generation

The project combines **financial analytics**, **time series modeling**, and **risk-based portfolio allocation** into a complete end-to-end workflow.

---

# 🏢 Selected NSE Stocks

Five major Indian companies from different sectors were selected to ensure portfolio diversification.

| Stock | Sector |
|------|------|
| HDFCBANK.NS | Banking |
| TCS.NS | Information Technology |
| SUNPHARMA.NS | Pharmaceutical |
| HINDUNILVR.NS | FMCG |
| MARUTI.NS | Automobile |

---

# ⚙️ Technologies Used

<div align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white"/>
<img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white"/>
<img src="https://img.shields.io/badge/Matplotlib-11557C?style=flat-square"/>
<img src="https://img.shields.io/badge/Seaborn-4C72B0?style=flat-square"/>
<img src="https://img.shields.io/badge/Statsmodels-2C5AA0?style=flat-square"/>
<img src="https://img.shields.io/badge/Facebook_Prophet-4267B2?style=flat-square"/>
<img src="https://img.shields.io/badge/yFinance-6001D2?style=flat-square"/>
<img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white"/>

</div>

---

# 🧠 Concepts & Theories Used

## 📈 Time Series Analysis
Time series analysis studies data points collected sequentially over time. In stock markets, time series techniques help identify:

- Trends
- Seasonal patterns
- Cyclic behavior
- Volatility
- Future price movement

---

## 📉 Stationarity

A stationary time series has:
- Constant mean
- Constant variance
- No time-dependent structure

Most stock prices are non-stationary, so differencing is required before applying ARIMA models.

### ADF Test
The **Augmented Dickey-Fuller (ADF) Test** was used to verify stationarity.

- Raw prices → Non-stationary
- Differenced prices → Stationary

---

## 📊 Log Returns

Log returns were computed using:

```math
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
```

Advantages:
- Handles compounding naturally
- Stabilizes variance
- Widely used in quantitative finance

---

## 📈 ARIMA Model Theory

ARIMA stands for:

- **AR** → Auto Regression
- **I** → Integrated (Differencing)
- **MA** → Moving Average

General notation:

```math
ARIMA(p,d,q)
```

Where:
- `p` = autoregressive terms
- `d` = differencing order
- `q` = moving average terms

### Why ARIMA?
ARIMA works well for:
- Historical trend modeling
- Linear temporal dependencies
- Short-term forecasting

---

## 🤖 Facebook Prophet Theory

Facebook Prophet is an additive forecasting model designed for time series with:

- Trend
- Seasonality
- Holiday effects

General Prophet equation:

```math
y(t) = g(t) + s(t) + h(t) + \epsilon_t
```

Where:
- `g(t)` → Trend
- `s(t)` → Seasonality
- `h(t)` → Holiday effects
- `εt` → Error term

Advantages:
- Handles missing data
- Captures seasonality effectively
- Easy to tune

---

## 📊 Volatility Analysis

Volatility measures the dispersion of returns and indicates risk.

### Annualized Volatility Formula

```math
\sigma_{annual} = \sigma_{daily} \times \sqrt{252}
```

Where:
- `252` = average trading days in a year

Higher volatility → Higher risk

---

## 📉 STL Decomposition

STL stands for:

### Seasonal-Trend decomposition using Loess

It separates a time series into:
- Trend component
- Seasonal component
- Residual component

Useful for identifying long-term market behavior.

---

## 💼 Portfolio Optimization

Two allocation strategies were used:

### Strategy A — Forecast-Based Allocation
Weights assigned based on:
- Predicted future returns
- Ensemble forecast signals

### Strategy B — Inverse Volatility Allocation
Weights inversely proportional to risk:

```math
w_i \propto \frac{1}{\sigma_i}
```

Lower volatility stocks receive higher allocation.

---


# 1️⃣ Data Collection

Historical stock prices were downloaded using the **yFinance API**.

### Data Range
```python
2021-01-01 → 2025-12-31
```

### Features Used
- Open
- High
- Low
- Close
- Adjusted Close
- Volume

---

# 2️⃣ Data Preprocessing

## Missing Value Handling
Missing values were treated using:
- Forward Fill
- Backward Fill

This ensured a continuous time series.

---

## Train-Test Split

| Dataset | Period |
|------|------|
| Training | Up to 2025-06-30 |
| Testing | From 2025-07-01 |

---

## Stationarity Testing

ADF tests confirmed:
- Raw stock prices were non-stationary
- Differenced series became stationary

This step was necessary before ARIMA modeling.

---

# 3️⃣ Forecasting Models

---

## 📈 ARIMA Forecasting

### Model Selection
Grid search optimization was performed to identify the best:

```python
(p, d, q)
```

combination using minimum AIC score.

### Evaluation Metrics
- RMSE
- MAPE
- Directional Accuracy

---

## 🤖 Facebook Prophet Forecasting

Prophet models were fitted with:
- Weekly seasonality
- Yearly seasonality

Forecasts were generated and compared against actual values.

---

# 📊 Model Comparison

| Stock | Better Model |
|------|------|
| HDFCBANK | ARIMA |
| TCS | Prophet |
| SUNPHARMA | ARIMA |
| HINDUNILVR | Prophet |
| MARUTI | ARIMA |

### Observation
- ARIMA performed better for 3 out of 5 stocks
- Prophet captured seasonality better for IT and FMCG sectors

---

# 📉 Volatility & Trend Analysis

## Annualized Volatility

| Stock | Volatility |
|------|------|
| MARUTI | Highest |
| HINDUNILVR | Lowest |

---

## Rolling Volatility
30-day rolling volatility was plotted to visualize changing market risk over time.

---

# 📌 STL Trend Analysis

### Upward Trend
- HDFCBANK
- SUNPHARMA
- MARUTI

### Downward Trend
- TCS
- HINDUNILVR

---

# 💼 Portfolio Construction

## Strategy A — Forecast Guided

Portfolio weights assigned based on:
- Ensemble forecasts
- Predicted positive returns

---

## Strategy B — Inverse Volatility

Lower-risk assets received higher allocation.

---

## Final Blended Strategy

Final portfolio:

```text
50% Forecast Strategy
+
50% Risk-Based Strategy
```

---

# 💰 Final Capital Allocation

Initial Capital:

```python
₹1,000,000
```

| Stock | Allocation |
|------|------|
| HDFCBANK.NS | 38.0% |
| TCS.NS | 16.4% |
| SUNPHARMA.NS | 25.9% |
| HINDUNILVR.NS | 10.5% |
| MARUTI.NS | 9.1% |

---

# 📈 Prediction Performance Tracking

## Actual vs Predicted Prices

Live market data for the first two trading days of January 2026 was downloaded.

---

## Forecast Error

| Metric | Value |
|------|------|
| Day 1 MAPE | 7.97% |
| Day 2 MAPE | 7.90% |

---

## Directional Accuracy

The models struggled with short-term movement prediction.

```text
Correct Direction Predictions = 0/5
```

---

## Portfolio Performance

| Metric | Result |
|------|------|
| Portfolio Return | +0.1661% |
| Profit | ₹1,661 |

---

# 📊 Dashboard & Visualizations

The project generated:

✅ Portfolio Allocation Charts  
✅ Correlation Heatmaps  
✅ ARIMA Forecast Plots  
✅ Prophet Forecast Plots  
✅ Rolling Volatility Graphs  
✅ STL Decomposition Charts  
✅ Prediction Error Charts  

---

# 📄 PDF Report Generation

All generated charts and dashboards were exported into:

```bash
capstone_charts.pdf
```

---

# 📦 Libraries Used

```python
pandas
numpy
matplotlib
seaborn
statsmodels
prophet
yfinance
scikit-learn
jupyter
```

---

# 🛠 Installation & Setup

## Clone Repository

```bash
git clone https://github.com/your-username/nse-time-series-analysis.git
```

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Run Notebook

```bash
jupyter notebook
```

---

# 🚀 Future Improvements

- 🔥 LSTM & Deep Learning Forecasting
- 📰 Financial News Sentiment Analysis
- 📡 Real-Time Data Streaming
- 🌐 Streamlit Dashboard Deployment
- ⚡ Automated Portfolio Rebalancing
- 📈 Sharpe Ratio Optimization
- 🤖 Reinforcement Learning-based Trading

---

# 📚 Key Learnings

- Financial data is highly non-stationary
- ARIMA performs well on stable trends
- Prophet handles seasonality effectively
- Volatility-based allocation reduces portfolio risk
- Short-term stock direction prediction remains difficult

---

# Author

## CH.K.D.M.Lakshmi
Data Science • Machine Learning • Financial Analytics

---

# ⭐ If you found this project useful, consider giving it a star!
