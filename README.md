![image](https://github.com/Myash21/Time-Series-Forecasting/assets/130383057/d3c212c6-c20e-489f-b196-6c55b73b9993)

# Time Series Forecasting

## About

Here I have tested 3 models, 1.ARIMA, 2.Linear Regression, 3.LSTM on _ dataset to predict the values of average temperature(AvgTemp) and evaluated their performances.

## Time series notes

Below are hand-written time series notes prepared by me while learning, Hope you find it useful.

### 1.Difference between interpolation and extrapolation:-
  -Interpolation is used to predict data within a dataset. Extrapolation is used to estimate beyond the dataset.
  -Interpolation makes estimates within the range of collected information. Extrapolation makes predictions about what happened before or after the range of collected data.
  -Predicting the sale of umbrellas tomorrow based on yesterday's or last month's sale of umbrellas is an example of extrapolation.

### 2.What is a stationary time series and why a time series needs to be stationary?
  -A stationary time series has statistical properties that remain constant over time. A non-stationary time series has statistical properties that change over time.
   i.e. constant mean, variance, no seasonality.
  -A stationary time series can lead to more accurate predictions because models can better capture the underlying dynamics.
  -Stationary series allow for meaningful sample statistics like means, variances, and correlations with other variables. These statistics are useful for describing future behavior.
  - You differentiate to make the time-series stationery and then you use the forecasted growth rates to predict the time-series moving forward

### 3.ARIMA
  -ARIMA is a combination of two types of models 1.Auto-Regressive(AR), 2.Moving Averages(MA)
  -AR(Auto-regressive)model uses past values of a time series to predict future values unlike linear regression use cases where there are seperate features through which we determine value of target.Its equation is similar to that used in linear regression(y = mx + c) just that in LR the x variable represents the value of independent variable whereas in AR model it represents the previous value(lag) of the target variable. The equation can also be of second order which means that the target value is dependent on its two previous lags in which case the equation may look like y = mx1 + mx2 + c, here 'm' and 'c' are constants.
  -Partial auto-correlation Function(PACF, It measures only the direct effect of previous time lags on current value) graph can be used to find out the lag value used in AR model.
  -MA(Moving Average)model predicts the future values of a time series using its past errors. Its equation will look something like y = μ + mx + x1, but here μ = mean, x = error made in previous prediction, x1 = error made in current time prediction  
  -Similar to AR model the MA model equation can be multiple degrees which can be decided in this case by using the Auto-Correlation Function(ACF, It measures direct and indirect effect of previous time lags on current value) graph.
  -Thus in ARIMA model using PACF and ACF graphs we calculate the order of AR and MA models. Here 'I' stands for integrating i.e. using differencing to convert non-stationary time series to stationary time series(If during differencing we are only subtracting by values of previous time lag then it is called first order differencing) from which the I parameter in for ARIMA model will be calculated depending on the order. Finally we combine them to get the parameters for ARMA model e.g.(2, 1, 3) where 2, 1 and 3 are orders of AR, I, MA respectively.
  -VAR(Vector Auto-Regression) is a slight modification of the AR model such that it predicts future values using its own previous time lags and lags of some other dependent variable.


### 4.Should use ARIMA over Linear Regression for time series forecasting?
  -A Linear Regression model is built on the assumption that there is no auto-correlation in residuals i.e.residuals from adjacent measurements in a time series are independent of one another. But this assumption is broken when forecasting using linear regression on time-series data.e.g.your forecast has a 10% error in 2012 and the 2013 projection is dependent on the error (or lack of error) in 2012 then you have autocorrelation in the error terms.
Now ARIMA was built to combat the issue of auto-correlation that we find when using linear regression to forecast, To get around this ARIMA uses differentiation (along with other methods) to make a time-series stationery; to oscillate around a single value. This should remove trends in the underlying data component so that we can try to find the relationships between the variables (including lagged values of the dependent variable). The idea is that we can then use these relationships to predict future behaviour. 
*In conclusion time series forecasting using linear regreesion requires feature engineering to be performed to create new features that capture the seasonality and trend in the data whereas for ARIMA/SARIMAX models require the time series data to be stationary which can be achieved through differencing process.Howewver one drawback of ARIMA/SARIMAX is that they can only be used on univariate time series data.(only two variables in which one is time and the other is the field to forecast) 

### ARIMA parameters-
 p:AR model lags, Identification of AR model lags is best given by PACF(Partial Auto Correlation)i.e.We note the point beyond which the partial auto correlations are
   equal to zero.
 d:differencing(How many times seasonal differencing is done before)
 q:MA lags, Identification of MA model lags is best given by ACF(Auto Correlation)i.e.We note the point after which auto correlation tapers towards zero and not
   exactly zero.
*SARIMAX additional parameter we specify that by how many number we are shifting while differencing.  


### 5.LSTM
  -LSTM(Long Short-Term Memory) is an RNN(Recurrent Neural Network) based model and generally RNNs are well-suited to tasks that involve sequential data and therefore can produce great results for time series forecasting.
  -LSTMs can hold information longer by forgetting and remembering information and thus help in solving the vanishing gradient problem occuring in normal RNNs.
  -Scaling th data can significantly improve results while working with LSTMs.

## Important Links

 - [About ARIMA](https://medium.com/@lewis_b/next-post-eb6b933256a4)
 - [Stationarity](https://towardsdatascience.com/stationarity-in-time-series-analysis-90c94f27322)
 - [Detecting Stationarity in Time series](https://towardsdatascience.com/detecting-stationarity-in-time-series-data-d29e0a21e638)
 - [Stationarity test-geeksforgeeks](https://www.geeksforgeeks.org/how-to-check-if-time-series-data-is-stationary-with-python/)
 - [ARIMA forecasting](https://medium.com/swlh/temperature-forecasting-with-arima-model-in-python-427b2d3bcb53)
 - [Time series playlist](https://www.youtube.com/playlist?list=PLqYFiz7NM_SMC4ZgXplbreXlRY4Jf4zBP)
 - [LSTM](https://www.youtube.com/watch?v=c0k-YLQGKjY)
