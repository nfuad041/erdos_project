# erdos_project

## Summary
It's a project on stock market prediction for Data Science Boot Camp 2024.
We use historical data from two types of stocks - index funds (ex. Nasdaq Composite) and individual stocks (ex. Apple). We aim to predict the closing stock price one day in the future. For this purpose we propose to use statistical modeling and forecasting based on moving averages to identify trends and seasonality in stock prices as well as extract autocorrelation times. Apart from statistical methods, we also plan to use machine learning techniques based on Long Short-Term Models (LSTM) and compare the predictions of statistical and machine learning methods. 
Our work would be particularly useful for day traders, and so our stakeholders would be financial brokers that offer online day trading services. According to [bankrate.com](https://www.bankrate.com/investing/best-online-brokers-for-day-trading/) , the best online brokers for day trading in May 2024 are,

1. Fidelity Investments

2. Interactive Brokers

3. Charles Schwab

4. E-trade Financial

5. Merrill Edge

6. TradeStation

7. tastytrade

The main company key performance indicators (KPIs) are,

1. Mean-squared error (MSE)

2. Root mean-squared error (RMSE)

3. R-squared for the variance

We perfrom initial baseline forcesting by implementing a Gaussian white noise model, Gaussian random walk model and simple exponential smoothing. We also evaluate the performance of the respective forecasts using average cross-validation root mean-squared error. Preliminary calculations show that naive forecasts perform better. Autocorrelation plots of the first differences do not show any particular trend or seasonality in the time-series data. So we perform an ARIMA calculation on the training data that gives the optimal values of (p,d,q) based on minimum AIC. Again using RMSE as the performance metric we see that ARIMA performs as good as the naive forecast.
