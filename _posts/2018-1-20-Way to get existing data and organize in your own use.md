---
layout:     post
title:      Way to get existing data and organize in your own use
subtitle:   
date:       2018-1-20
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - python
    - pandas
    - data
---


As an individual investor in Australia stock market who want to establish your own trading system, one of the most important input is market data. However, market data is not cheap, and market data vendors' clients are mostly those institutes and fund managers.  Their data is too fine for most individual investors and most people don't like to pay so much for things overqualified.  There are ways to get some data for free which are public for private research.  I will describe how to use some technology to download those data and format it in .csv which is wide used by many people.   This is an outline. 
   1. [how to get financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](https://datatellstory.blogspot.com/2018/11/get-historical-data-with-python.html)
   2. [how to get delayed real time price directly from ASX.](https://www.biglion.com.au/2018/11/asx-has-free-api-for-delayed-data.html)
   3. [If you have an existing trading system which need rest API data input, how to organize and convert these data into format you need.](https://steemit.com/teamaustralia/@chenlocus/build-a-rest-api-service-to-provide-market-data-for-yourself) 
   4. [to make your data accessible wherever you are, create an instance in aws for free.](https://datatellstory.blogspot.com/2018/11/create-instance-in-aws-for-free.html)
   5. [build a python running environment  in aws EC2.](https://steemit.com/teamaustralia/@chenlocus/how-to-access-the-ec2-instance-in-aws)
   6. [use putty to get access to your EC2 instance.](https://steemit.com/teamaustralia/@chenlocus/how-to-access-the-ec2-instance-in-aws)
   7. [use winSCP to download/upload your program with aws.](https://steemit.com/teamaustralia/@chenlocus/how-to-access-the-ec2-instance-in-aws)
   8. [launch your software with nginx, gunicorn.](https://steemit.com/teamaustralia/@chenlocus/build-a-rest-api-service-to-provide-market-data-for-yourself)
   9. [configure crontab in aws to keep your historical data up to date.](https://datatellstory.blogspot.com//2018/12/schedule-regular-tasks-in-aws.html)