<h1 align="center">Order Book Project</h1>
<p align="center">Created by Anjali and Finnley</p>

<p align="center">
  <a href="https://github.com/KeyErrorFinn/mthree-order-book-project/commits/main"><img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/KeyErrorFinn/mthree-order-book-project" /></a>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff" />
  <img alt="Streamlit" src="https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=fff" />
</p>

An educational Streamlit application for adding buy and sell orders, viewing bids and asks, and removing an order when it is purchased or sold into.

This demonstrates order-book concepts. It is not connected to an exchange and must not be used for real trading.

## Features

- Add buy and sell orders with a symbol, quantity, and total price.
- Display bids and asks in separate columns.
- Sort buy orders from highest to lowest price.
- Sort sell orders from lowest to highest price.
- Assign matching colours to orders at the same price.
- Purchase a selected sell order.
- Sell into a selected buy order.
- Remove the oldest matching order when duplicates exist.
- Validate empty, numeric, and negative inputs.

## Run locally

~~~bash
python -m pip install -r requirements.txt
streamlit run main.py
~~~

Streamlit normally opens the application in a browser. If it does not, use the local URL printed in the terminal.

## How the order book works

### Add an order

1. Choose **Add Stock Order**.
2. Select Buy or Sell.
3. Enter a stock symbol, quantity, and total price.
4. Submit the form.

The application uppercases the symbol, generates a six-digit order ID, records the current time, and assigns a colour based on the price.

### Complete an order

Choose **Purchase Sell Order** or **Sell to Buy Order**, then select a symbol and one of its displayed price and quantity combinations.

The app removes one complete matching order. It does not support partial fills.

## Current data behaviour

The order book is stored in Streamlit session state:

- Refreshing or restarting the session can reset the data.
- There is no database or file persistence.
- New sessions begin with demonstration orders already present in `main.py`.
- The app does not match compatible orders automatically.
- Prices are stored as entered strings and converted when sorting.

## Display rules

| Side | Sort order | Market term |
| --- | --- | --- |
| Buy | Highest price first | Bid |
| Sell | Lowest price first | Ask |

Orders with the same price share a colour. When several orders have the same symbol, price, and quantity, the oldest one is removed first.

## Project files

- `main.py`, complete Streamlit interface and in-memory order book.
- `requirements.txt`, pinned Python environment.
- `help.txt`, short launch reminder.
- `.vscode/settings.json`, editor configuration.

## Possible improvements

- Replace the demonstration data with an empty initial book option.
- Add persistent storage.
- Support partial fills and remaining quantities.
- Add automatic price matching.
- Separate the matching logic from the Streamlit interface.
- Add automated tests for validation and order priority.

## Licence

No project-level licence is currently included.
