# erdos_project

## Summary
It's a project on stock market prediction for Data Science Boot Camp 2024.
We use historical data from two types of stocks - index funds (ex. Nasdaq Composite) and individual stocks (ex. Apple). We aim to predict the closing stock price a few days in the future. For this purpose we propose to use statistical modeling and forecasting based on moving averages to identify trends and seasonality in stock prices as well as extract autocorrelation times. Apart from statistical methods, we also plan to use deep learning techniques such as Recurrent Neural Networks (RNN) with Long Short-Term Memory (LSTM) cells, and compare the predictions of statistical and machine learning methods. 
Our work would be particularly useful for day traders, and so our stakeholders would be financial brokers that offer online day trading services. According to [bankrate.com](https://www.bankrate.com/investing/best-online-brokers-for-day-trading/) , the best online brokers for day trading in May 2024 are,

1. Fidelity Investments

2. Interactive Brokers

3. Charles Schwab

4. E-trade Financial

5. Merrill Edge

6. TradeStation

7. tastytrade

The main company key performance indicators (KPIs) are,

1. Mean-squared error (MSE), Root mean-squared error (RMSE), R-squared for the variance

2. Few day forecasting and confidence interval

3. Market movement analysis after a shock

We perform initial baseline forcasting by implementing a Gaussian white noise model, Gaussian random walk model and simple exponential smoothing. We also evaluate the performance of the respective forecasts using average cross-validation root mean-squared error. Preliminary calculations show that naive forecasts perform better. Autocorrelation plots of the first differences do not show any particular trend or seasonality in the time-series data. So we perform an ARIMA calculation on the training data that gives the optimal values of (p,d,q) based on minimum AIC. Again using RMSE as the performance metric we see that ARIMA performs as good as the naive forecast.

We move on to RNN-based techniques for predictive modeling of the time series data, notedly employing the LSTM cell to do multi-day forecasting. As a first step, we segment the historical stock data into time series snippets of length ~ 60 days, with the first 50 days used as training features and the last 10 days used as training target. To get rid of number variations between different batches (e.g., a snippet in 2020s would have a much larger mean and variance than a snippet in the 1980s) we preprocess each snippet of data by a standard scaler. MSE is used as the metric to evaluate the model effectiveness. Initial attempt using LSTM has demonstrated (see proj/LSTM_MarketAnalysis.ipynb) reasonable effectiveness of the RNN in modeling the market data. In the upcoming days, we shall focus on addressing the following set of questions: 

1. How to do model parameter tuning of the RNN to achieve better MSE metrics? 
2. With the best RNN model we create, how does it fair against classic statistical modeling method such as ARIMA? 
3. We shall focus on implementing a toolkit that not only gives forecasts but also confidence intervals (i.e., how confident are we that the stock price at day n is given by val).
4. We shall combine LSTM with a classifier to achieve the goal of informing stakeholders whether to buy, sell, or hold in the near term future.