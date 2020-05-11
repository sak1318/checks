# TradeBot
## Description




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
#### Architecture
![Architecture](/Ananta_architecture.png) 
