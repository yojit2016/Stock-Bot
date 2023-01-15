import pandas as pd
from datetime import datetime, timedelta
from pytz import timezone
import pytz

# function to fetch historical data for a stock
def fetch_data(stock_name):
    # specify the url for the stock data
    url = f'https://www.alphavantage.co/query?function=TIME_SERIES_DAILY_ADJUSTED&symbol={stock_name}&apikey={API_KEY}&datatype=csv'
    # read the data into a pandas dataframe
    data = pd.read_csv(url)
    # convert the date field to datetime
    data['date'] = pd.to_datetime(data['date'])
    # set the date field as the index
    data.set_index('date', inplace=True)
    # return the data
    return data

# function to calculate the moving average
def moving_average(data, window):
    return data['close'].rolling(window=window).mean()

# function to buy or sell based on moving average crossover
def trade(data, moving_average_short, moving_average_long):
    # initialize a position variable to keep track of the current position
    position = 0
    # initialize a list to store the trades
    trades = []
    # iterate through the data
    for i in range(len(data)):
        # if the short moving average is greater than the long moving average and the position is not long
        if data.iloc[i][moving_average_short] > data.iloc[i][moving_average_long] and position != 1:
            # buy
            trades.append((data.index[i], 'BUY', data.iloc[i]['close']))
            position = 1
        # if the short moving average is less than the long moving average and the position is not short
        elif data.iloc[i][moving_average_short] < data.iloc[i][moving_average_long] and position != -1:
            # sell
            trades.append((data.index[i], 'SELL', data.iloc[i]['close']))
            position = -1
    # return the trades list
    return trades

# function to backtest the strategy
def backtest(stock_name, moving_average_short, moving_average_long):
    # fetch the data
    data = fetch_data(stock_name)
    # calculate the moving averages
    data[moving_average_short] = moving_average(data, short_window)
    data[moving_average_long] = moving_average(data, long_window)
    # make the trades
    trades = trade(data, moving_average_short, moving_average_long)
    # iterate through the trades and calculate the profit
    profit = 0
    for trade in trades:
        if trade[1] == 'BUY':
