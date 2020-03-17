---
layout:     post
title:      An Alternative to Yahoo Finance API in Australian Share Market
subtitle:   
date:       2018-1-18
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - python
    - pandas
    - data mining
---

I decided to provide this API service in the long run to help people like me used to struggle for financial data when trying to establish their own models. So as an investor and engineer, I will provide more data in the future according to your feedback and my own experience. This is some simple guide how to leverage it.

Get current market snapshot of a symbol, price in AUD.


HTTP Request
GET http://www.biglion.com.au/api/v1/asx/snapshot/

Query parameters:

symbol: instrument name, such as Z1P, APT, TTT.


e.g.

http://www.biglion.com.au/api/v1/asx/snapshot/?symbol=z1p

{"code":"Z1P","bid_price":1.035,"offer_price":1.04,"open_price":1.01,"last_price":1.035,"change_in_percent":"5.612%","change_price":0.055,"day_high_price":1.057,"day_low_price":1.01,"average_daily_volume":1114071,"volume":811261,"last_price":1.035,"previous_close_price":0.98,"previous_day_percentage_change":"-12.5%","eps":-0.0784,"pe":0,"annual_dividend_yield":0,"market_cap":293956184,"number_of_shares":299955290,"year_change_in_percentage":"4,145.283%","year_change_price":1.01062,"year_high_date":"2018-02-01T00:00:00+1100","year_high_price":1.34,"year_low_date":"2017-10-18T00:00:00+1100","year_low_price":0.555,"year_open_date":"2014-02-28T11:00:00+1100","year_open_price":0.02438}




Get all weekly price in one year.


HTTP Request

GET http://www.biglion.com.au/api/v1/asx/history/year

Query parameters:

symbol: instrument name.
frequency: interval of the share price, currently support: weekly, daily.
year: the year you want to get the share price, can go as early as 2015.

e.g.
http://www.biglion.com.au/api/v1/asx/history/year/?symbol=IRE&frequency=weekly&year=2018

{"2018-09-24":{"Open":"12.64","High":12.82,"Low":12.55,"Close":12.76,"Adjust Close":12.76,"Volume":319384.0},"2018-09-17":{"Open":"12.83","High":12.92,"Low":12.38,"Close":12.65,"Adjust Close":12.65,"Volume":1937329.0},"2018-09-10":{"Open":"12.92","High":13.12,"Low":12.81,"Close":12.83,"Adjust Close":12.83,"Volume":1150470.0},"2018-09-03":{"Open":"13.45","High":13.56,"Low":12.72,"Close":12.91,"Adjust Close":12.76,"Volume":1299226.0},"2018-08-27":{"Open":"13.65","High":13.69,"Low":13.28,"Close":13.44,"Adjust Close":13.28,"Volume":2625118.0},"2018-08-20":{"Open":"12.28","High":14.2,"Low":12.03,"Close":13.66,"Adjust Close":13.5,"Volume":2614749.0},"2018-08-13":{"Open":"11.75","High":12.33,"Low":11.75,"Close":12.27,"Adjust Close":12.12,"Volume":1401312.0},"2018-08-06":{"Open":"11.82","High":11.98,"Low":11.77,"Close":11.83,"Adjust Close":11.69,"Volume":1727845.0},"2018-07-30":{"Open":"11.84","High":11.91,"Low":11.54,"Close":11.8,"Adjust Close":11.66,"Volume":1444537.0},"2018-07-23":{"Open":"11.78","High":12.04,"Low":11.66,"Close":11.89,"Adjust Close":11.75,"Volume":1515612.0},"2018-07-16":{"Open":"11.76","High":11.91,"Low":11.6,"Close":11.84,"Adjust Close":11.7,"Volume":1061156.0},"2018-07-09":{"Open":"11.80","High":12.07,"Low":11.74,"Close":11.79,"Adjust Close":11.65,"Volume":1908495.0},"2018-07-02":{"Open":"12.03","High":12.26,"Low":11.58,"Close":11.79,"Adjust Close":11.65,"Volume":2028524.0},"2018-06-25":{"Open":"12.35","High":12.55,"Low":11.97,"Close":12.04,"Adjust Close":11.9,"Volume":1910314.0},"2018-06-18":{"Open":"11.88","High":12.48,"Low":11.85,"Close":12.33,"Adjust Close":12.18,"Volume":2092325.0},"2018-06-11":{"Open":"10.96","High":12.22,"Low":10.96,"Close":11.89,"Adjust Close":11.75,"Volume":3088854.0},"2018-06-04":{"Open":"10.61","High":11.06,"Low":10.56,"Close":10.96,"Adjust Close":10.83,"Volume":2697375.0},"2018-05-28":{"Open":"10.75","High":10.88,"Low":10.26,"Close":10.58,"Adjust Close":10.45,"Volume":2181597.0},"2018-05-21":{"Open":"10.86","High":10.99,"Low":10.55,"Close":10.76,"Adjust Close":10.63,"Volume":1368031.0},"2018-05-14":{"Open":"10.85","High":11.03,"Low":10.75,"Close":10.91,"Adjust Close":10.78,"Volume":1412793.0},"2018-05-07":{"Open":"10.79","High":11.16,"Low":10.73,"Close":10.81,"Adjust Close":10.68,"Volume":3472170.0},"2018-04-30":{"Open":"10.53","High":11.02,"Low":10.43,"Close":10.73,"Adjust Close":10.6,"Volume":2369764.0},"2018-04-23":{"Open":"10.21","High":10.55,"Low":10.05,"Close":10.52,"Adjust Close":10.39,"Volume":1573348.0},"2018-04-16":{"Open":"9.86","High":10.34,"Low":9.67,"Close":10.18,"Adjust Close":10.06,"Volume":1811849.0},"2018-04-09":{"Open":"9.42","High":9.87,"Low":9.37,"Close":9.85,"Adjust Close":9.73,"Volume":1899326.0},"2018-04-02":{"Open":"9.49","High":9.55,"Low":9.17,"Close":9.42,"Adjust Close":9.31,"Volume":2400276.0},"2018-03-25":{"Open":"9.68","High":9.69,"Low":9.32,"Close":9.49,"Adjust Close":9.38,"Volume":1906243.0},"2018-03-18":{"Open":"9.82","High":9.99,"Low":9.6,"Close":9.75,"Adjust Close":9.63,"Volume":1969429.0},"2018-03-11":{"Open":"10.09","High":10.21,"Low":9.81,"Close":9.82,"Adjust Close":9.7,"Volume":4100653.0},"2018-03-04":{"Open":"10.11","High":10.34,"Low":9.98,"Close":10.01,"Adjust Close":9.89,"Volume":2828019.0},"2018-02-25":{"Open":"10.73","High":10.79,"Low":10.01,"Close":10.13,"Adjust Close":9.75,"Volume":2082066.0},"2018-02-18":{"Open":"11.51","High":11.72,"Low":10.49,"Close":10.7,"Adjust Close":10.3,"Volume":3036963.0},"2018-02-11":{"Open":"11.58","High":11.64,"Low":11.39,"Close":11.49,"Adjust Close":11.06,"Volume":1307188.0},"2018-02-04":{"Open":"11.97","High":12.16,"Low":11.16,"Close":11.66,"Adjust Close":11.22,"Volume":2459720.0},"2018-01-28":{"Open":"12.06","High":12.12,"Low":11.91,"Close":11.96,"Adjust Close":11.51,"Volume":1989655.0},"2018-01-21":{"Open":"11.82","High":12.06,"Low":11.79,"Close":12.06,"Adjust Close":11.6,"Volume":578430.0},"2018-01-14":{"Open":"11.62","High":11.84,"Low":11.41,"Close":11.81,"Adjust Close":11.36,"Volume":1108662.0},"2018-01-07":{"Open":"11.85","High":11.85,"Low":11.4,"Close":11.62,"Adjust Close":11.18,"Volume":1520167.0}}




Get historical price within a range:


HTTP Request
GET  http://www.biglion.com.au/api/v1/asx/history/price/

Query parameters:

symbol: instrument name.
frequency: currently support weekly, daily.
datefrom: specify which date the data from.
dateto: specify which date you want the data to.

e.g.
http://www.biglion.com.au/api/v1/asx/history/price/?symbol=IRE&frequency=weekly&datefrom=18/05/2018&dateto=19/09/2018

{"2018-09-17":{"Open":"12.83","High":12.92,"Low":12.38,"Close":12.65,"Adjust Close":12.65,"Volume":1937329.0},"2018-09-10":{"Open":"12.92","High":13.12,"Low":12.81,"Close":12.83,"Adjust Close":12.83,"Volume":1150470.0},"2018-09-05":{"Open":"0.16 Dividend","High":null,"Low":null,"Close":null,"Adjust Close":null,"Volume":null},"2018-09-03":{"Open":"13.45","High":13.56,"Low":12.72,"Close":12.91,"Adjust Close":12.76,"Volume":1299226.0},"2018-08-27":{"Open":"13.65","High":13.69,"Low":13.28,"Close":13.44,"Adjust Close":13.28,"Volume":2625118.0},"2018-08-20":{"Open":"12.28","High":14.2,"Low":12.03,"Close":13.66,"Adjust Close":13.5,"Volume":2614749.0},"2018-08-13":{"Open":"11.75","High":12.33,"Low":11.75,"Close":12.27,"Adjust Close":12.12,"Volume":1401312.0},"2018-08-06":{"Open":"11.82","High":11.98,"Low":11.77,"Close":11.83,"Adjust Close":11.69,"Volume":1727845.0},"2018-07-30":{"Open":"11.84","High":11.91,"Low":11.54,"Close":11.8,"Adjust Close":11.66,"Volume":1444537.0},"2018-07-23":{"Open":"11.78","High":12.04,"Low":11.66,"Close":11.89,"Adjust Close":11.75,"Volume":1515612.0},"2018-07-16":{"Open":"11.76","High":11.91,"Low":11.6,"Close":11.84,"Adjust Close":11.7,"Volume":1061156.0},"2018-07-09":{"Open":"11.80","High":12.07,"Low":11.74,"Close":11.79,"Adjust Close":11.65,"Volume":1908495.0},"2018-07-02":{"Open":"12.03","High":12.26,"Low":11.58,"Close":11.79,"Adjust Close":11.65,"Volume":2028524.0},"2018-06-25":{"Open":"12.35","High":12.55,"Low":11.97,"Close":12.04,"Adjust Close":11.9,"Volume":1910314.0},"2018-06-18":{"Open":"11.88","High":12.48,"Low":11.85,"Close":12.33,"Adjust Close":12.18,"Volume":2092325.0},"2018-06-11":{"Open":"10.96","High":12.22,"Low":10.96,"Close":11.89,"Adjust Close":11.75,"Volume":3088854.0},"2018-06-04":{"Open":"10.61","High":11.06,"Low":10.56,"Close":10.96,"Adjust Close":10.83,"Volume":2697375.0},"2018-05-28":{"Open":"10.75","High":10.88,"Low":10.26,"Close":10.58,"Adjust Close":10.45,"Volume":2181597.0},"2018-05-21":{"Open":"10.86","High":10.99,"Low":10.55,"Close":10.76,"Adjust Close":10.63,"Volume":1368031.0}}




Get balance sheet for a symbol in a year:


HTTP Request
GET  http://www.biglion.com.au/api/v1/asx/financial/balancesheet/

Query parameters:

symbol: instrument name.
year: which year you want the financial report in balance sheet.

e.g.
http://www.biglion.com.au/api/v1/asx/financial/balancesheet/?symbol=APT&year=2016
{"2016-06-30":{"totalasset":38992.195,"totaldebt":931.358,"receivable":7767.586,"payable":675.434,"currentassets":27521.269,"currentdebts":928.413,"totalcash":19723.472,"nettangibleassets":27227.504}}





Get cash flow for a symbol in a year:


HTTP Request
GET  http://www.biglion.com.au/api/v1/asx/financial/cashflow/

Query parameters:

symbol: instrument name.
year: which year you want the financial report in cash flow.

e.g.
http://www.biglion.com.au/api/v1/asx/financial/cashflow/?symbol=IRE&year=2017

{"2017-12-31":{"cashfromoperating":83743,"capitalexpenditure":-18945,"cashfrominvestment":-21606,"cashfromfinancing":-61176,"changeincash":5664}}





Get revenue for a symbol in a year:


HTTP Request
GET  http://www.biglion.com.au/api/v1/asx/financial/revenue/

Query parameters:

symbol: instrument name.
year: which year you want the financial report in income report.

e.g.
http://www.biglion.com.au/api/v1/asx/financial/revenue/?symbol=IRE&year=2017

{"2017-12-31":{"totalrevenue":429952,"costofrevenue":290020.0,"grossprofit":139932.0,"totalopexpense":346096.0,"EBIT":83856.0,"incomebeforetax":77765,"netincome":59755}}

To get valuation of the security in current market:
http://www.biglion.com.au/api/v1/asx/financial/valuation/?symbol=IRE

{"IRE":{"marketcap":"1.96B","enterprisevalue":"2.29B","PE":"31.60","anticipatedPE":"0","PEG":"0","PS":"4.37","PB":"4.85","enterprisevalue2revenue":"5.10","enterprisevalue2EBITDA":"22.23"}}

For those who is keen to use excel to do analysis, this is a guide how to import api data to spread sheet:

https://youtu.be/Hz4HTnQpTBw


Keep on update on this blog:

https://datatellstory.blogspot.com/2018/10/an-alternative-to-yahoo-finance-api-in.html



Related topic: 

- [Data crawl and organize in restful API service in aws](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/)