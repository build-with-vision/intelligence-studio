# Multi-Asset Financial Direction Forecasting using Machine Learning and Deep Learning

## Overview

This project explores whether short-term market direction can be predicted using historical financial data, technical indicators, machine learning models, and deep learning techniques.

To improve the modelling approach, the project was reformulated into a classification problem focused on predicting whether the market direction over the next five trading days would move upward or downward.

The final project therefore became less focused on building a highly accurate trading system and more focused on building a technically correct and realistic financial forecasting pipeline.

---

# Project Structure

```bash
Gold_ETF_MultiAsset_Price_Forecasting/
│
├── notebooks/
│   └── Multi_Asset_5D_Direction_Forecasting_Notebook.ipynb
│   └── Gold_ETF_MultiAsset_Price_Forecasting_EDA.ipynb
│
├── reports/
│   └── Financial_Forecasting_Report.docx
│
├── visualisation/
│   ├── 01_gld_price_trend.png
│   ├── 02_gld_volume_ma30.png
│   ├── 03_gld_daily_return_distribution.png
│   ├── 04_gld_moving_averages.png
│   ├── 05_gld_rolling_volatility.png
│   ├── 06_1_gld_vs_slv.png
│   ├── 06_2_gld_vs_spy.png
│   ├── 06_3_gld_vs_uup.png
│   ├── 07_correlation_heatmap.png
│   ├── 08_market_regime_analysis.png
│   ├── 09_gld_price_with_events.png
│   ├── 10_acf_pacf_analysis.png
│   └── 11_seasonal_decomposition.png
│
├── requirements.txt
└── README.md
```

---

# Dataset

The dataset contains historical market data collected across multiple financial assets including stocks and exchange-traded funds (ETFs).

The available columns include:

- Date
- Open
- High
- Low
- Close
- Adjusted Close
- Volume
- Ticker
- Asset Type

The final version of the project uses the complete dataset across all assets instead of filtering only GLD data.

This decision increased the number of training observations and allowed the deep learning models to learn from a larger sequence of market behaviour.

---

# Problem Statement

The final objective of the project is to predict:

```python
1 = future upward movement
0 = future downward or neutral movement
```

using a five-day forecasting horizon.

The project does not attempt to predict exact future prices because the experiments showed that exact short-term return prediction produced very weak and unstable results.

---

# Methodology

## 1. Data Preparation

The dataset is first sorted chronologically by ticker and date to preserve time-series order.

Missing values and invalid observations are then handled before feature engineering begins.

---

## 2. Feature Engineering

One of the most important parts of the project is leakage-safe feature engineering.

All rolling calculations and lag operations are performed separately for each ticker using grouped operations. This prevents information from one asset incorrectly influencing another asset.

The engineered features include:

- Daily returns
- Lagged returns
- Rolling moving averages
- Rolling volatility
- Momentum indicators
- RSI indicators
- Trend-based indicators
- Multi-day rolling statistics

---

## 3. Target Construction

The original regression target was replaced with a classification target because the regression models struggled to predict exact future returns.

Final Target:

- 1 → Upward movement over the next 5 trading days
- 0 → Downward or neutral movement

---

## 4. Time-Series Splitting

The project uses chronological train, validation, and test splitting.

Random shuffling was intentionally avoided because random splitting introduces leakage in financial forecasting tasks.

---

## 5. Models Used

The following models were trained and evaluated:

### Logistic Regression
Used as a baseline model to measure whether the engineered features contained meaningful directional signal.

### Decision Tree
Used to test whether nonlinear decision boundaries could capture short-term market behaviour.

### Random Forest
Used to improve stability and reduce overfitting compared to a single decision tree.

### LSTM Neural Network
Used to capture temporal dependencies within the financial time-series data.

---

# Model Performance Summary

| Model | Accuracy | ROC-AUC | Observation |
|---|---|---|---|
| Logistic Regression | 59.24% | 0.5447 | Best overall balance |
| Decision Tree | ~50% | ~0.50 | Performed close to random guessing |
| Random Forest | 56.98% | 0.5137 | Biased toward upward predictions |
| LSTM | 56.56% | 0.5408 | Showed overfitting behaviour |

---

# Key Observations

The Logistic Regression model produced the most stable overall performance in this project.

The Random Forest model achieved slightly stronger classification metrics in some areas, but confusion matrix analysis showed that the model frequently predicted upward movement regardless of the actual market direction.

The LSTM model did not produce meaningful improvement over the simpler machine learning models. Training accuracy improved steadily, but validation performance remained relatively flat, suggesting that the model memorised noise rather than learning stable market patterns.

One of the most important findings from the project was that technically correct forecasting pipelines do not automatically produce strong predictive performance.

Financial markets contain high levels of randomness, especially when predicting short-term movements across multiple assets.

---

# Visualisations Included

The project includes multiple exploratory and analytical visualisations:

- GLD price trend analysis
- Volume trend analysis
- Daily return distribution
- Moving average analysis
- Rolling volatility analysis
- Cross-asset comparison plots
- Correlation heatmaps
- Market regime analysis
- Event-based market behaviour
- ACF/PACF analysis
- Seasonal decomposition

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow / Keras
- Statsmodels

---

# How to Run the Project

## Clone Repository

```bash
git clone <repository_url>
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```bash
notebooks/Multi_Asset_5D_Direction_Forecasting_Notebook.ipynb
notebooks/Gold_ETF_MultiAsset_Price_Forecasting_EDA.ipynb
```

---

# Future Improvements

Possible future improvements include:

- Adding macroeconomic indicators
- Introducing sentiment analysis features
- Using XGBoost models
- Building sector-specific forecasting models
- Predicting longer forecast horizons
- Introducing market regime classification

---

# Final Conclusion

This project does not claim to produce a highly accurate trading system.

Instead, the project focuses on building a technically correct and realistic financial forecasting workflow using both machine learning and deep learning techniques.

The strongest contribution of the project is the methodology, leakage-safe preprocessing, realistic evaluation, and honest interpretation of the limitations of financial forecasting.
