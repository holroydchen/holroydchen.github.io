---
layout:     post
title:      get delayed price directly from ASX
subtitle:   
date:       2018-1-22
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - python
    - pandas
    - data mining
---


In the [previous post](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/), we talked about [a substitute for yahoo finance API](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/)  which was offline years ago.  Most people want some 'real time' market data for their own investment model, 'real time' data is not cheap, the good thing is most people just want delayed data. Fortunately, ASX has  a free API to obtain delayed realtime price.


e.g.

https://www.asx.com.au/asx/1/share/Z1P

result:

{"code":"Z1P","isin_code":"AU000000Z1P6","desc_full":"Ordinary Fully Paid","last_price":0.967,"open_price":0.96,"day_high_price":0.975,"day_low_price":0.96,"change_price":0.002,"change_in_percent":"0.207%","volume":168651,"bid_price":0.965,"offer_price":0.97,"previous_close_price":0.965,"previous_day_percentage_change":"0.521%","year_high_price":1.34,"last_trade_date":"2018-11-26T00:00:00+1100","year_high_date":"2018-02-01T00:00:00+1100","year_low_price":0.635,"year_low_date":"2017-12-21T00:00:00+1100","year_open_price":0.02438,"year_open_date":"2014-02-28T11:00:00+1100","year_change_price":0.94262,"year_change_in_percentage":"3,866.366%","pe":0,"eps":-0.0784,"average_daily_volume":758458,"annual_dividend_yield":0,"market_cap":290215070,"number_of_shares":300741005,"deprecated_market_cap":290215000,"deprecated_number_of_shares":300741005,"suspended":false}


Related topics: 

 - [Mine financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

 - [Get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

 - [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2020/01/12/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

 - [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

 - [build a python running environment in aws EC2 and use putty, winSCP to access your instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

 - [configure crontab in aws to schedule application.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)
