# Stock-Bot
A trading Bot in Python using simple moving avg stratey
Stock Trading Bot
This is a basic trading bot that uses a simple moving average crossover strategy to buy and sell stocks.

Requirements
Python 3.x
Pandas
Requests
Usage
Install the required libraries by running pip install -r requirements.txt
Replace the API_KEY variable in the code with your own Alpha Vantage API key.
Run the script by executing python trading_bot.py
The script will print out a list of trades that the bot would have made based on the moving average crossover strategy.
Backtesting
The script includes a function for backtesting the strategy on historical data. To backtest the strategy on a specific stock, call the backtest() function and pass the stock symbol and the short and long window for the moving averages.

Copy code
backtest('AAPL', 50, 200)
The function will print the trades that the bot would have made and the profit or loss from those trades. It's important to note that past performance is not indicative of future results, and it's always important to do your own research and make your own investment decisions.

Note
It's important to thoroughly test and backtest any trading bot before using it with real money. This bot is for educational purpose only.

Disclaimer
It's illegal to guarantee returns in the stock market, and any claims of guaranteed returns should be viewed with skepticism. It's always important to do your own research and make your own investment decisions, rather than relying solely on the advice of a trading bot or any other automated system.



