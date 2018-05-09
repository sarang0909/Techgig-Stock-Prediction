# Techgig-Stock-Prediction
Techgig Hackathon-Stock prediction Challenge

Challenge Description:
Stock markets have always been a fancy for companies, investors and traders. There is a plethora of investors investing or exiting the stocks at any point of time with different trading strategies and investment horizons. However the underlying objective of every type of investor is common "Maximize the returns and minimize the losses." To achieve this objective every investor is intrigued with one question “Is my stock price going to rise or fall in future". People have been trying to find this answer from various angles. For some investors fundamentals are important and hence they rely on the fundamental strength of the stock. Others try to predict the movement of the stock based on technical analysis. Some try to predict the movement based on news about stocks and overall market sentiment while other tries to track the trend to predict the price of stock.
In this competition we challenge you to identify the predictability in the market based on technical analysis of stocks.

Goal:
The problem statement for this competition is to design a decision-making framework that can be used to predict actual return value of stock after 30th trading days.
To elaborate, we want to predict for list of given stocks and their return after 30th trading days.In this competition we have given you 12 stocks of Banking and IT sector in csv format with last 5 years of stock details.

Above stock data has been downloaded from Yahoo Finance, but participants are free to download any other historical data from Yahoo finance if they are interested. File format for stock data
Following technical indicators should be generated using any open source packages available in R or python for technical Analysis ( like TTR in R or Talib in Python) Simple Moving Average ( 30, 40, 50 Days) Exponential Moving Average ( 30, 40, 50 Days) Aroon Oscillator ( 30, 40, 50 Days) MACD signals Relative Strength Index (RSI) Bollinger Bands ( 30, 40, 50 Days) Stochastic Oscillator Stochastic momentum Indicator Chande Momentum Oscillator Commodity Channel Index ( 30, 40, 50 Days) Chakin Volatility indicator ( 30, 40, 50 Days) Trend Detection Index (30, 40, 50 Days) Rate of Price Change (30, 40, 50 Days) Rate of Volume Change (30, 40, 50 Days) William % R (30, 40, 50 Days) Participants are free to transform and derive more features from the above set of indicators from short term as well as long term perspective.



1.Select base model:1_base_model.ipynb
We have data of 12 diffenret stocks,but we will pick only one for exploration
data preporcessing:
  remove rows and  with any null value
  Create new column to show closing price after 30th day'''
Evaluation matrix chosen is Mean Absolute Error/MAE
Try out couple of regression models to choose base model'''
We wil go with  RandomForestRegressor as base model to help with feature engineering'''

2.Feature Engineering:2_feature_engineering.ipynb
Try diffenret feature using TALib
Evaluate MAE for each featureSelect features which improves MAE

3.Select best model:3_select_best_model.ipynb
Create featured dataset from previous step.
Try different regression model on whole dataset and compare MAE
It turns out out LinearRegression and BayesianRidge perrform better.

Create Training and test set:
  KFoldCrossvalidation is not useful in timeseries data.
  TimeSeriesSplit is used with 6 fold(6 is decided after trying many otherr values).
For each fold create 1 model.As we have chosen 2 algorithms.
We'll have total 12 models.
Now we have 12 predicted values from 12 different models,one way to select final values is averaging output of 12 models
but a biased model can give outlier as result which in turn will afect averaging.
So new approach is considered:Treat output of 12 models as features


4.Run final model on test data:4_run_final_model.ipynb
Create new model and consider output of 12 models as features.
Ridge model is considered to give more importance/weight to more correct models from 12 models.
This model will give final value.
Run this model on 4th April data,it'll predict 16th May data.




Future work:
Create model according to sector
Conside Quartery,yearly data for training
