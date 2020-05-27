
# Time Series & Linear Regression Modeling - A Yen for the Future

`Analyzing the future direction and risk of Japanese Yen Currencies `

![Yen Photo](Images/unit-10-readme-photo.png)

## Background

The financial departments of large companies often deal with foreign currency transactions while doing international business. As a result, they are always looking for anything that can help them better understand the future direction and risk of various currencies. Hedge funds, too, are keenly interested in anything that will give them a consistent edge in predicting currency movements.

Here we will test the many time-series tools to predict future movements in the value of the Japanese yen versus the U.S. dollar.

Hereby gain proficiency in the following tasks:

* Time Series Forecasting
    1. ARMA Model - Forecasting Returns
    2. ARIMA Model - Forecasting the Settle Price
    3. GARCH - Forecasting Volatatility
* Linear Regression Modeling

- - -

### Files

[Time-Series Starter Notebook](Starter_Code/time_series_analysis.ipynb)

[Linear Regression Starter Notebook](Starter_Code/regression_analysis.ipynb)

[Yen Data CSV File](Starter_Code/yen.csv)

- - -

#### Time-Series Forecasting

In this notebook, load historical Dollar-Yen exchange rate futures data and apply time series analysis and modeling to determine whether there is any predictable behavior.

**The steps outlined in the time-series Analysis:**

1. Decomposition using a Hodrick-Prescott Filter (Decompose the Settle price into trend and noise).

Trend           |  Noise
:-------------------------:|:-------------------------:
![alt-text-1](Images/Trend.png)  |  ![alt-text-2](Images/Noise.png)


2. Forecasting Returns using an **ARMA Model**.

Summary Report           |  Forecast Returns
:-------------------------:|:-------------------------:
<img src="Images/ARMA_summary.png" width="500" />  |  <img src="Images/ARMA_forecast.png" width="500" /> 


3. Forecasting the Settle Price using an **ARIMA Model**.

Summary Report           |  Forecast Settle Price
:-------------------------:|:-------------------------:
<img src="Images/ARIMA_summary.png" width="500" />   |  <img src="Images/ARIMA_forecast.png" width="500" />


4. Forecasting Volatility with **GARCH**.

Summary Report           |  Forecast Volatality
:-------------------------:|:-------------------------:
<img src="Images/GARCH_summary.png" width="500" />   |  <img src="Images/GARCH_forecast.png" width="500" />


Use the results of the time series analysis and modeling to answer the following questions:

1. Based on your time series analysis, would you buy the yen now?
> `Based on the above models, its more likely going to uptrend next 5 Business days`
2. Is the risk of the yen expected to increase or decrease?
> `Based on GARCH Modeling analysis, **the risk is expected to increase** for the Yen`
3. Based on the model evaluation, would you feel confident in using these models for trading?
> `For ARMA & ARIMA models, p < 0.05 and also, AIC & BIC values are way high. These are **not the best models** for trading the Yen`


#### Linear Regression Forecasting

In this notebook, Build a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with *lagged* Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects).

**The steps outlined in the regression_analysis:**

1. Data Preparation (Creating Returns and Lagged Returns and splitting the data into training and testing data)
2. Fitting a Linear Regression Model.

     ```python 
        # Create a Linear Regression model and fit it to the training data
        from sklearn.linear_model import LinearRegression
        model = LinearRegression()
        # Fit a SKLearn linear regression using just the training set (X_train, Y_train):
        model.fit(X_train, y_train)
     ```


3. Making predictions using the testing data.

    ```python
        predictions = model.predict(X_test)
    ```
    

    <img src="Images/linear_regression_prediction.png" width="500" />


4. Out-of-sample performance.

    > `Out-of-sample Root Mean Squared Error (RMSE): 0.41521640820129047`


5. In-sample performance.

    > `In-sample Root Mean Squared Error (RMSE): 0.5663352320297497`

* Does this model perform better or worse on out-of-sample data compared to in-sample data?

    > `RMSE for Out-of-sample is lower (0.415) as compared to in-sample (0.566). **Model performs better on out-of-sample data**`


- - -

### Hints and Considerations

* Out-of-sample data is data that the model hasn't seen before (Testing data).
* In-sample data is data that the model was trained on (Training data).

- - -
