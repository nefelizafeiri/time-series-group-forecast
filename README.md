# Time Series Forecasting

Forecasting project from an MSBA Time Series class. Compared classical and
hybrid models on a monthly economic time series (with `layoffs`, `quits`,
`sales`, and `wages` as candidate exogenous regressors) to find the most
reliable forecast.

## Models Compared

| Model | Notes |
| --- | --- |
| Naive Forecast | Baseline — next value = most recent observation |
| ARIMA(1, 1, 1) | Standard ARIMA fit |
| ARIMAX(1, 1, 1) | ARIMA with four exogenous regressors: layoffs, quits, sales, wages |
| **12-Month Moving Average** | **Best model** — lowest MAPE, most stable forecasts |
| Hybrid (OLS + ARIMA on residuals) | Two-stage fit: linear trend + ARIMA on residuals |

## Why the 12-Month Moving Average Won

Smoothing over a full seasonal period captured the data's long-term pattern
without overfitting short-term noise. ARIMA and ARIMAX gave reasonable point
forecasts but had higher MAPE on held-out data. The hybrid added flexibility
but didn't beat the simpler average.

## Tech Stack

- **Python 3.10+**
- `pandas`, `numpy` — data handling
- `statsmodels` — ARIMA, ARIMAX, decomposition
- `matplotlib` — visualization

## Run It

```bash
pip install pandas numpy statsmodels matplotlib
jupyter notebook TimeSeriesFinalcode.ipynb
```

## Files

| File | What it is |
| --- | --- |
| `TimeSeriesFinalcode.ipynb` | Main notebook — model fitting, comparison, diagnostics |
| `submission_BEST.csv` | Final submission (12-month moving average) |
| `submission_arima.csv`, `submission_ets.csv`, `submission_moving_average.csv`, `submission_stl_arima.csv` | Per-model forecast outputs |
| `12_month_moving_average_forecast.csv` | Best-model forecast values |
| `sample_submission.csv`, `test-2.csv` | Class-provided templates |
