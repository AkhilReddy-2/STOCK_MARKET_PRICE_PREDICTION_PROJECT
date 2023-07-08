# STOCK_MARKET_PRICE_PREDICTION_PROJECT

![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/b5054043-ca7b-42e7-88e1-a06c74274e54)

## Project Overview
Investment firms, hedge funds and even individuals have been using financial models to understand market behaviour better and make profitable investments and trades. A wealth of information is available in the form of historical stock prices and company performance data, suitable for machine learning algorithms to process.

Can we predict stock prices with machine learning? Investors make educated guesses by analyzing data. They will read the news, study the company history, industry trends, and other data points that go into making a prediction. The prevailing theories are that stock prices are totally random and unpredictable, raising the question of why top firms like Morgan Stanley and Citigroup hire quantitative analysts to build predictive models. We have this idea of the trading floor being filled with adrenaline infuse men with loose ties running around yelling something into a phone. However, these days we are more likely to see rows of machine learning experts quietly sitting in front of computer screens. About 70% of all orders on Wall Street are now placed by software. We are now living in the age of algorithms.

This project utilizes the ARIMA model for base predictions and then built a Deep Learning model to improve it further. Stock prices are predicted for Tech Giants like Apple, Google, Tesla, Microsoft and Amazon.

## Dataset
Webscraped https://in.finance.yahoo.com using selenium and BeautifulSoup.

## Exploratory Data Analysis
### Closing Price v/s Time
![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/90eeb55b-9b13-45ae-8e98-c20b305bc767)



We can see from the above graph that Telsa shares have tremendous growth in the 2020-2021 period.
If we follow the news, it can be due to

Emission Credit Sales
Tesla entering the Fast-Growing Compact SUV Market
Starting production in China
For the rest of the Companies, we can see that COVID-19 is the primary factor affecting the 2020-2021 period.

### Histogram plot of Percentage Daily Return
![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/1e24e8fd-d2e6-492d-97f6-74e2a9ccccd4)



### Correlation between the stocks daily returns

![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/a6362a2b-c242-4a8a-af1e-b3f52881d49c)



From the above plot, we can see that Microsoft and Google had the strongest correlation in stocks daily returns.
### Risk v/s Expected Returns
![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/4c6fb661-59ee-4739-8401-5d11ae232a94)




From the above graph, we can see that Tesla has the highest expected returns and the highest risk factor. Google has the lowest expected returns and the lowest risk factor.
## Deep Learning Model
### Model
![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/2de1c843-57d9-4538-b93f-9260725340a2)





We train the model using the training dataset records and then use it to forecast the following week’s closing values (i.e., the next five values as a week consists of five working days). The forecasting is done in a multi-step manner with a walk-forward validation mode.

The details of the design of each layer and the overall architecture of the model are as follows :
The input data’s shape to the network’s input layer is (5, 1), indicating that the previous five values (i.e., one week’s data) of the time series are used as the input. Only one attribute of the data (i.e., the closing value) is considered. The input layer passes the data onto the LSTM layer with 200 nodes at the output, with the Leaky ReLU activation function is used in these nodes. The LSTM layer’s output is passed to another LSTM layer with 200 nodes at the output, with the Leaky ReLU as an activation function. This layer’s output is then passed onto a dense layer with 200 nodes at its input and output, with Leaky ReLU activation. This layer’s output is passed onto another dense layer with 200 nodes at its input and 100 nodes with a Leaky ReLU activation function at the output. This layer’s output is passed onto another dense layer with 100 nodes at its input and 50 nodes with a Leaky ReLU activation function at the output. The dense layer is finally connected to the output layer that is also fully-connected. The output layer has 50 nodes at its input and 5 nodes at the output. The 5 nodes at the output produce the forecasted values for the five days of the following week. Again the output layer uses Leaky ReLU as an activation function. The model uses MSE as the loss function and ADAM as the optimizer with a custom learning rate.
### Custom Learning Rate
![image](https://github.com/HopeToLearn/STOCK_MARKET_PRICE_PREDICTION_PROJECT/assets/115106831/4d73bbe1-c969-41b2-85da-b1146f7ce67b)



## Results

ARIMA Model (RMSE)	Deep Learning Model (RMSE)
Apple	6.40	4.82
Tesla	108.11	66.40
Google	210.40	115.66
Microsoft	7.26	6.23
Amazon	113.18	87.48
## References
Mehtab, S. (2020, September 20). Stock Price Prediction Using Machine Learning and LSTM-Based Deep Learning Models. ArXiv.Org. https://arxiv.org/abs/2009.10819
Chauhan, N. S. (2020, January). Stock Market Forecasting Using Time Series Analysis. KDnuggets. https://www.kdnuggets.com/2020/01/stock-market-forecasting-time-series-analysis.html
Dev, U. (2020, June 21). EDA of Stock Market using Time Series - Usharbudha Dev. Medium. https://usharbudha-dev09.medium.com/eda-of-stock-market-using-time-series-9662fd18bfc5
