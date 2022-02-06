# Financial Planning Tools

This is a financial tool to help clients plan for emergencies and for retirement. First, it helps them visualize their current savings to determine if they have enough for an emergency fund. Then, it uses forecast tools to estimate the performance of their portfolios in 10-30 years.  

---

## Technologies
This project uses Jupyter Notebook (within [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/)) and the standard Python 3.8 libraries. In addition, this project requires the following libraries and/or dependencies:

* [Pandas](https://pandas.pydata.org/) - a software library designed for open source data analysis and manipulation

* [matplotlib](https://matplotlib.org/) - a cross-platform, data visualization and graphical plotting library for Python and its numerical extension NumPy

* [os](https://docs.python.org/3/library/os.html) - provides a portable way of using operating system dependent functionality 

* [requests](https://docs.python-requests.org/en/latest/) - allows you to send HTTP/1.1 requests extremely easily. There’s no need to manually add query strings to your URLs, or to form-encode your POST data. Keep-alive and HTTP connection pooling are 100% automatic

* [json](https://docs.python.org/3/library/json.html) - stands for JavaScript Object Notation. JSON is a lightweight data format used for data interchange between multiple different languages. It is easy to read for humans and easily parsed by machines

* [dotenv](https://pypi.org/project/python-dotenv/) - reads key-value pairs from a .env file and can set them as environment variables

* [alpaca_trade_api](https://pythonrepo.com/repo/alpacahq-alpaca-trade-api-python-python-third-party-apis-wrappers) - a python library for the Alpaca Commission Free Trading API. It allows rapid trading algo development easily, with support for both REST and streaming data interfaces

* MCForecastTools - the document named "MCForecastTools.py" contains the code functions needed to run the Monte Carlo Simulations (MCSimulation) used in this project

* All stock and bond data was pulled in using Alpaca API calls to the Alpaca SDK. The ETH and BTC data were pulled in using the Requests library from the following links: [btc_url]("https://api.alternative.me/v2/ticker/Bitcoin/?convert=USD"), [eth_url]("https://api.alternative.me/v2/ticker/Ethereum/?convert=USD")

Example of all the required imports: 
```
import os
import requests
import json
import pandas as pd
from dotenv import load_dotenv
import alpaca_trade_api as tradeapi
from MCForecastTools import MCSimulation
%matplotlib inline
```

---

## Methods

For this analysis, the following steps were taken:

1. **Create a financial planner for emergencies:** The household monthly income data was used to calculate the amount needed for emergencies. Then, the Python Requests library was used to access the current value of the client's cryptocurrency wallet. The Alpaca SDK was used to access the current value of the client's stock and bond portions of the portfolio. The emergency fund was evaluated to see if they had enough saved. 

2. **Create a financial planner for retirement:** The Alpaca API was used to obtain historical closing prices for the retirment portfolio. Then, Monte Carlo simulations were created for the stock and bond portfolio. The first simulation consisted of 500 samples, a 30-year time period, and a weight of 40% to bonds and 60% to stocks. The client was wondering if they can retire in 10 years by investing in stocks more heavily. Therefore, a second simulation was created and consisted of 500 samples, a 10-year time period, and a weight of 20% to bonds and 80% to stocks.

---

## Findings

In response to the question of whether weighting the portfolio more heavily toward stocks will allow the clients to retire after only 10 years, my analysis indicates these recommendations:

Based on the results of the simulations, I am not comfortable recommending retirement after only 10 years. 

I do not recommend retirement after only 10 years because the clients will likely receive a return somewhere in the middle of the 95% confidence interval range of 101,623.51 and 956,990.35 dollars. For example, the client might receive the average return of 357,423 dollars. If you were to receive the lower confidence interval amount of 101,623.51 dollars or the average amount of 357,423 dollars, it would not be enough to retire with. Even if the client received the upper confidence interval amount of 956,990.35 dollars, the client would likely want more money than that so they can travel and enjoy their retirement. 

Looking at the 30-year simulation, the client might receive the average return of 3,334,956.3 dollars. There is 95% confidence that the client will receive between 513,698.60 and 10,647,236.04 dollars, but it is highly unlikely that they will receive either the lower or the upper end. People typically receive a return somewhere between the lower and upper bound. A return between 513,698.60 and 10,647,236.04 dollars would be plenty for retirement. Therefore, I do not recommend retiring in 10 years, but the client may be able to retire in 15-20 years. The client may not need to continue working for the full 30 years, but I would not recommend stopping after 10 years. 

Most experts say your retirement income should be about 80% of your final pre-retirement annual income. This client's household income is 12,000 dollars per month, so 144,000 dollars annually. Eighty percent of 144,000  is 115,200 dollars. This client needs 115,200 dollars per year to live a comfortable lifestyle in retirement. The average life expectancy in the US is about 79 years. Let's say the client wants to retire early at age 45, leaving 34 years of retirement (79-45 years = 34 years). Multiplying 115,200 * 34 results in 3,916,800 dollars. Therefore, the client will not be able to retire after only 10 years.  

The client also has cryptocurrency money (currently has 66,003.05 dollars). This will likely increase in value, so it is another factor that can be considered when discussing the money available for retirement. 

Another interesting measure to look at is the standard deviation. The standard deviation for the 30-year simulation is 41.64 whereas the standard deviation for the 10-year simulation is 3.12. The 40% weight in bonds and 60% weight in stocks appears to be riskier than the 20% weight in bonds and 80% weight in stocks. Typically, stocks are riskier than bonds, so this case is different than what is typical. However, the simulations are comparing two different lengths of time (30 years vs. 10 years), so it is hard to directly compare them. The important factor is noting that it is okay to have more risk when you are far away from retirement, and you should have less risk as you get closer to retirement. You can find a happy medium such as weighting 30% to bonds and 70% to stocks, for example. Another factor involves how much money you will take out of the stocks vs. how much you will continue to invest. However, this is an individualized discussion that requires more data and information from the client. 

---

## Contributors
Catherine Croft

Email: catherinecroft1014@gmail.com

LinkedIn: [catherine-croft](https://www.linkedin.com/in/catherine-croft-4715481aa/)

---

## License

MIT