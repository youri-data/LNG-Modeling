# LNG Modeling: Forecasting Natural Gas Returns

This project presents a complete modeling and forecasting analysis of U.S. Natural Gas futures (Henry Hub) returns using econometric techniques and machine learning. It was developed as part of a university assignment.

---

## Objective

- Analyze and forecast a financial time series (Natural Gas futures: `NG=F`)
- Generate log-return forecasts and assess model performance
- Compare various modeling approaches using out-of-sample metrics (RMSE, MAE)
- Build confidence intervals for forecasts where possible

---

## Data Source and Frequency

- Ticker: `NG=F` (Henry Hub Natural Gas Futures)
- Source: Yahoo Finance via `yfinance` library
- Frequency: Daily
- Sample: Until end of 2023 for training; 2024 held out for forecasting

---

## Step-by-Step Workflow

### 1. Data Analysis
- Calculated daily **log-returns** with 1-day lag using `.pct_change()`
- Applied **ADF test** to confirm stationarity of returns
- Visual checks: rolling mean & std, histogram
- Distribution stats: **skewness**, **kurtosis**
- Autocorrelation: ACF and PACF plots (up to 40 lags)

### 2. Econometric Modeling

#### ARMA(1,1)
- Trained only on pre-2024 data
- Used ACF/PACF to guide specification
- Estimated model with `statsmodels`
- Parameters tested for significance

#### GARCH(1,1)
- Fitted to pre-2024 returns
- Volatility clustering captured
- Persistence (α + β) found to be high (common in energy markets)
- Residual diagnostics applied

### 3. Machine Learning: XGBoost
- Forecasted next-day returns using:
  - 5 lagged returns (`t-1` to `t-5`)
  - 5-day rolling volatility
  - 5-day return momentum
- Trained only on data prior to 2024
- Forecasts generated for 2024
- Confidence intervals built using residual std (95%)
- Evaluated using RMSE and MAE

---

## Key Features
- 2024 is treated as **genuinely out-of-sample**
- Full pipeline of analysis, modeling, validation, forecasting
- Model residuals assessed for performance and stability
- Machine learning model includes feature importance and diagnostics

---

## Files

- `Forecasting analysis NatGas.py` — Main script with ARMA + GARCH
- `xgboost_lng_forecast.py` — Machine learning forecasting with lag features
- `README.md` — Project overview and methodology

---

## Next Steps
- Add macroeconomic or weather-related exogenous features
- Implement sequence models (e.g., LSTM)
- Build VaR model using GARCH volatility forecast
