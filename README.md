# LNG Modeling: Forecasting Natural Gas Returns

This project models and forecasts U.S. Natural Gas (Henry Hub) daily returns using econometrics and machine learning.

---

## Overview

- Time series: Natural Gas Futures (`NG=F`)
- Models used:
  - ARMA(1,1)
  - GARCH(1,1)
  - XGBoost (with lagged returns, volatility, momentum)
- Forecasting target: 2024 daily log-returns
- Evaluation: RMSE, MAE, residual analysis
- Confidence intervals included for forecast uncertainty

---

## Files

- `Forecasting analysis NatGas.py`: ARMA + GARCH modeling
- `xgboost_lng_forecast.py`: ML-based return forecasting
- `README.md`: Project summary

---

## Key Points

- Full data analysis (stationarity, autocorrelation, distribution)
- Out-of-sample forecast for 2024
- Multiple model comparison with error metrics

---

## To Do

- Add exogenous variables
- Try LSTM for sequence modeling
