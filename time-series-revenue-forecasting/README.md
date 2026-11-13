# Forecasting Hospital Revenue With ARIMA

Can daily revenue be forecasted from two years of history? This project checks the data for trend and seasonality, then builds an ARIMA model and tests the forecast against held-out data.

## Data

Daily hospital revenue (in millions of dollars) for 731 days, provided by WGU. It isn't included here. To run the notebook, put `D213_medical_time_series.csv` in a `data/` folder next to it.

## Approach

1. Converted the day counter to dates and confirmed there were no gaps, nulls, or duplicates.
2. Tested for stationarity with the Augmented Dickey-Fuller test. The raw series wasn't stationary (p = 0.20), so I differenced it (p < 0.001).
3. Looked at autocorrelation (ACF and PACF), spectral density, and a seasonal decomposition.
4. Used `auto_arima` to pick the model, then compared it to two other candidates by AIC.
5. Split 80/20 without shuffling (584 days to train, 147 to test), forecasted the test period, and calculated the error.

## Results

- Best model: ARIMA(1,1,0), with no seasonal component
- RMSE on the test period: 3.56 (MSE 12.68), with revenue measured in millions
- Every value in the test set fell inside the forecast's 95% confidence interval

The confidence interval gets pretty wide the farther out the forecast goes, so I'd want more history before forecasting further ahead.

## Tools

Python, pandas, statsmodels, pmdarima, scikit-learn, matplotlib
