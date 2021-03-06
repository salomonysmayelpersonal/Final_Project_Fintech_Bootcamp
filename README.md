# Final_Project_Fintech_Bootcamp
## by Salomón Ysmáyel


# Time Series Forecasting for Algorithmic Trading
## with Multi Step Recurrent Neural Network LSTM Model.


Moving Average Convergence Divergence (MACD) generates a crossover signal for securities historic prices analysis. MACD is an indicator of momentum that results useful in showing that a reversal on a securities price has occurred. By studying the relationship between two moving averages calculated with different periods, one "slow" and one "fast", we can assess when an upward on downward trend in well on the way. This is by no means a future estimation since all the information used to calculate the estimator is past prices, but it helps to smooth out the price movements by doing some "depuration" of the noise in the time series. The signal that a reversal has occurred is when the graph of the slow and fast Exponential Moving Averages cross. Sometimes this is called Crossover signal.

The MACD has proven really useful at Algorithmic Trading. It doesn't mean that by following the signal we are going to be able to profit. Just following the signal would always put the investor in a "late to the party" situation. But it can help prevent mayor loses or ride on some upward momentum to recover certain position. Especially if the trend proves to be strong. So having the signals well tuned can be very useful to support an algorithmic trading strategy.

The question that fueled this project was. Is there a way to forecast the crossover signal a bit sooner than by just MACD using Deep Learning? This would make the MACD even more useful for algorithmic trading purposes. As it happens, there is a Deep Neural Network model that is especially good at working with time series, Recurrent Neural Networks. When time has an influence on the features, then using a regular feedforward Neural Network we lose important information that time has on the sequence for making predictions. On the other hand, RNNs extract what time has to say about the data. This is achieved by taking each input as a sequence where the first section acts as the features and the following section of the sequence as the target. Then we start feeding the network with sections of the whole sequence (in this case the closing price of certain stock) and moving forward from the first point until we reach the end of the data. The sub sequences all have the same size and contain both our features and targets. To test the model we use future points of the sequence that the training process never saw.

The values of Fast and Slow EMA were used to train a RNN model. Once the model was trained a future sequence was extracted from the historic prices and given to the model to predict the next 6 days in prices that directly follow the sequence. This was performed on days were the a crossover signal was generated. For instance, if the MACD generated a signal on 12-31-2019 the data given to the trained model was the prices from  12-01-2019 to 12-24-2019 to forecast the prices from 12-25-2019 to  12-31-2019 and see if the predicted values would predict the signal sometime before the 12-31-2019. 

The data used was the closing prices for Devon Energy Company, because of its volatility. A MACD on this data generates many crossover points. The section of the time series used to train the model was from 02-17-2015 to 4-27-2018. And the data used to predict was from 4-27-2018 to the present.

The following is a plot of the historic prices for Devon Energy and the MACD with short window of 10 days and long window of 40 days.

IMAGE 

Four signal points from the sequence 4-27-2018 to the present were studied. on the following dataframes we can see were the 1 entry/exit point ws generated. the values shown on these dataframes are precicely the ones to be forecasted by the model.

IMAGE OF DATAFRAMES WITH SIGNALS


