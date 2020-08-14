


> Written with [StackEdit](https://stackedit.io/).
> 
> 
# **The Defense Sector and Authoritarian Regime Changes - A Stock Analysis:**
![alt text](https://i.imgur.com/NKAMBLy.jpg)
Photo by [Christine Roy](https://unsplash.com/@agent_illustrateur?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/international?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

# Project Motivation
Geopolitical events are often involve with the actions of financial actors in different industries, but how do geopolitical events impact financial actors in their performance on the market? This project examines connections between Lockheed Martin(LMT)’s stock and Adverse Regime Changes, regime changes in countries away from democracy. As well, a State Fragility Matrix is taken into account, analyzing countries by their fragility and effectiveness.

Focusing on Lockheed Martin(ticker: LMT) stock, if we can better understand the links between the military industrial complex and political events, we open the doors to better understanding of the defense sector. As well, we can examine the inverse, any impact of the performance of defense sector stocks on world events. The world changes and there are industries that especially shift based on the changes in state regimes. Is there a benefit to the military industrial complex to turmoil and slides away from democracy?

# Process overview

1. INSCR data on Adverse Regime Changes and State Fragility and Stock Market Data of LMT was collected.

2. On all data: Time Series Analysis: VAR modeling + Machine Learning with Prophet and Extreme Gradient Boosting Trees(XGBoost) performed.

3. Goal: Predict the performance of LMT.

4. Metric used: RMSE, a measure of how far off to expect a model to be on another given prediction.

5. Best/source of truth model: XGBoost tuned via. GridSearchCV beat out Prophet and LSTM methods in predictive power, as well as baseline naive persistence forecasting.

# **Data sources:**

- INSCR data: [http://www.systemicpeace.org/inscrdata.html](http://www.systemicpeace.org/inscrdata.html) 

- AlphaVantage API used for Lockheed Martin stock data: [https://www.alphavantage.co/documentation/](https://www.alphavantage.co/documentation/)

- Data was then examined, cleaned and merged. See below for an example data manipulation, shifting time series to achieve Granger causality of the mean average of magnitude for Adverse Regime Change Events and the Close price, both scaled, of LMT.

![alt text here](https://i.imgur.com/hGq9jHt.png)

![alt text](https://i.imgur.com/hhekFbk.png)

-Time series resampling was performed from yearly/daily data to Business Daily frequency for analysis and missing data filled. Analysis was performed on business daily frequency data.

# **Baseline modeling:**

-A naive persistence model was built (detail) and achieved  **RMSE: 3.639** on a differenced stationary dataset, as well as **RMSE: 0.026** on forward time shifted[see above for two of the major time series shifted], scaled data.

- Naive persistence model on differenced dataset:

![alt text](https://i.imgur.com/vtOCIjs.png)

- Naive persistence model on shifted, scaled data.

![alt text](https://i.imgur.com/AbWVRmb.png)


# Linear Modeling:

- Vector Autoregression used and outperformed baseline modeling slightly with **RMSE: 3.391**.

![alt text](https://i.imgur.com/LjcY9uS.png)


  

# Machine learning:

- [Facebook Prophet](https://facebook.github.io/prophet/) was used in both univariate(close price autoregression) and multivariate modes, producing mildly effective results compared to VAR. (Scores not given due to issues with scaling and Facebook Prophet as a library.)
![alt text](https://i.imgur.com/a4AmgzQ.png)

- Extreme Gradient Boosting Trees(XGBoost) was then used for its reliability, transparency compared to models such as deep learning, and speed, across variations of dataframes and targets/features, producing much better results with a GridSearchCV used on a full dataframe of stock, regime change, and fragility data of **0.0076 RSME**. This is the **best model** achieved and what the business recommendations and conclusions are based on.
![alt text](https://i.imgur.com/7JLN6JV.png)

  

# Deep learning:

- LSTM were used on both univariate and multivariate data, but did not produce much in the way of results and deserve further exploration in future work.

![alt text](https://i.imgur.com/Ygs8KsK.png)


# Conclusions:
- Stock data is known to be heavily autoregressive. That is to say, the previous day of the stock can predict well the next day of the stock. However, some exogenous outside variables showed to have some feature impact with the best performing model, gradient boosting trees. 
- See below for the intense impact of the training data's historical Close price, as well as impact by polynomial time features and the magnitude of Adverse Regime Changes in various countries.
![alt text](https://i.imgur.com/jeleMUI.png)

# Recommendations
- Go with conventional wisdom: Follow that for the most part, stock data has known quantities such as its persistent/autoregressive nature to be utilized in analysis. 
- Turmoil is good for business: It is a small impact, but the magnitude of collapses, violence, etc., did have an impact on the close price of LMT in the best performing(XGB) model. 
- Timing is everything: The most impactful non-close price feature was a time polynomial however, suggesting as ever it's important to pay attention to the trends, seasonality and so on of stocks and strike while the iron is hot.

# Future Work:
-   Neural networks and unsupervised learning(Hidden Markov Machines) for better performance and discovering latent trends.
    
-   Anomaly detection and changepoint detection, reframing the problem as finding outliers/anomalies in the autoregressive data.
    
-   Examining more stocks and deploying as a web application that users can plug in their own stocks and see how geopolitical factors may impact them historically and/or going forward.
