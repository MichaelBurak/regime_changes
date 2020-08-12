


> Written with [StackEdit](https://stackedit.io/).
> 
> 
**The Defense Sector and Authoritarian Regime Changes - A Stock Analysis:**
![alt text](https://i.imgur.com/NKAMBLy.jpg)
Photo by [Christine Roy](https://unsplash.com/@agent_illustrateur?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/international?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

# Project Motivation
Geopolitics is inherently linked with the actions of financial actors in different industries, but are shifts in geopolitics linked to shifts in their performance on the market? This project examines connections between Lockheed Martin(LMT)’s stock and Adverse Regime Changes, regime changes in countries away from democracy. 

If we can better understand the links between the military industrial complex and political events, we open the doors to better understanding of the defense sector, possibly any impact of the performance of defense sector stocks on world events, and understand the financial implications of adverse geopolitical events. Who benefits from the slide away from democracy?

# Process overview
1. INSCR data on Adverse Regime Changes and State Fragility + Stock Market Data of LMT

2. On both data - Time Series Analysis: VAR modeling + Machine Learning and Deep Learning(?)

3. —> Predict the performance of LMT + Mean Magnitude of Regime Change Events.

# **Data sources:**

-Link to INSCR page

-AlphaVantage API used for Lockheed Martin stock data

-Data was then examined(include the viz of two time series + details on granger causality), cleaned and merged

![alt text here](https://i.imgur.com/hGq9jHt.png)

![alt text](https://i.imgur.com/hhekFbk.png)

-Time series resampling was performed from yearly/daily data to Business Daily and data filled

# **Baseline modeling:**

-A naive persistence model was built (detail) and achieved RMSE of [ ] **(Justify RMSE as a metric?)**

![alt text](https://i.imgur.com/vtOCIjs.png)

# Linear Modeling:

-VAR used and outperformed baseline modeling slightly (include viz and results)

![alt text](https://i.imgur.com/LjcY9uS.png)

-Linear regression was performed(?)

  

# Machine learning:

-Trees were used (?)

  

# Deep learning:

-LSTM were used(?)

![alt text](https://i.imgur.com/Ygs8KsK.png)


# Conclusions:
[TBD]
