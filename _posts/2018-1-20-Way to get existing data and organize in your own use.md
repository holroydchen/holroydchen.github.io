---
layout:     post
title:      a substitute solution of yahoo-finance
subtitle:   
date:       2018-1-20
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - python
    - pandas
    - data mining
    - aws
---

As an individual investor in Australia stock market who want to establish your own trading system, one of the most important input is market data. However, market data is not cheap, and market data vendors' clients are mostly those institutes and fund managers.  Their data is too fine for most individual investors and most people don't like to pay so much for things overqualified.  



As most individual investors, I liked to use [yahoo-finance](https://pypi.org/project/yahoo-finance/) to do security analysis.  However, maybe due to intellectual property reason, Yahoo Finance stock feed has gone offline years ago, see [this thread](https://forums.whirlpool.net.au/archive/2678938).  Then I checked an alternative such as google finance, however, its APIs are quite limited.  After searching for a while, I have to stick to yahoo finance,  although its API was down, its website can still provide all the information I needed.  What I need to do is to crawl data from those website and wrap APIs to provide historical data in need.  This application should be running as a regular job in a server each day, each week and each month.  There should be another application running as an API provider which can respond with financial data in certain format such as json. I  compared some technical implantations, then was determined to use python for this is a light server and the flask framework in python can provide a concise and efficient solution for such purpose. I don't like those heavy and redundant solutions.  I want to keep them FREE for use,  so I got to know aws can provide one-year free use.  



In another earlier post of mine, I tried to provide [an alternative to Yahoo Finance API in Australian Share Market](http://engineerman.club/2018/01/18/An-Alternative-to-Yahoo-Finance-API-in-Australian-Share-Market/), however this free service was stopped due to some reasons.





Now I would publicly explain all the technology details and I hope these can help you to build a free restful API for your private use or educational purpose.   I believe these technologies can be applied to other areas as well.  So I want to divide this project into several sub topics and describe them in separate posts as linked below: 

   1. [How to get financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

   2. [How to get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

   3. [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2020/01/12/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

   4. [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

   5. [Build a python running environment  in aws EC2.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

   6. [Use putty to get access to your EC2 instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

   7. [Use winSCP to download/upload your program with aws.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

   8. [Configure crontab in aws to keep your historical data up to date.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)

