# TradeBot - Ananta
## Description
Ananta - The trading bot uses Algorithmic strategies and places buy/sell orders on trading platform. The strategies are based on historical data of the stocks 
and some technical indicators (example - moving average, exponential moving average etc.).

I have implemented two simple strategies for this project so that I can focus on Advanced python of the implementation.
(Disclaimer : ) 


## Steps to run the bot

1. Clone the git hub repo
2. Install MongoDB 
    ```
    brew install mongodb 
    ```
3. Run a MongoDB
    ```shell script
    mongod --dbpath /tradebot/data
    ```
4. Install all the required packages from pipenv
    ```python
    pipenv install
    ```
5. Make migrations for Django Models and run server
   ```python
   python manage.py makemigrations
   python manage.py migrate
   python manage.py runserver
    ```
    You should be able to see two tabs on the website - Daily Orders, Profit/Loss
6. After market is closed, run script make_orders.py. Provide all the symbols you want to trade as the **tickers**. This will generate the orders using strategies for you
7. 15 minutes before market closes, run close_orders.py. This will close all the orders and populate the profit/loss page of the website.
8. Check the website on for summary of orders and profit/loss.

## Implementation Details
### Architecture
![Architecture](/Ananta_architecture.png) 

**Alphavantage API:** I have used aplhavantage api for extracting historical stock data and technical indicators required for strategies

**Arctic:** This is a database for time series which sits on top of the MongoDB. This is designed by ManAHL data engineers team. This data base suited for efficient time series data querying.

**Strategies** I have written two simple strategies for this bot. (These strategies are not back date tested for making money on so beware before using the bot :) ). These classes create a buy or sell triggers and provide buy/sell price, target price and stop loss for each of the stock.

**Aplaca API** Alpaca provides a commission free trading platform. They support their official python API for algorithmic trading
They also provide platform for paper trading (which I have used for development). The bot places orders using the triggers and the prices provided by strategies.

**Website** All the summary of orders placed for that day and the profit/loss for the day are published on the website powered by Django  

**Luigi** The workflow for data download

### More Details on code structure and Challenges

1. 
