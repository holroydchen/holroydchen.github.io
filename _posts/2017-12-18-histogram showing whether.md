---
layout:     post
title:      histogram showing whether share price is expensive or cheap
subtitle:   
date:       2017-12-18
author:     Howard
header-img: img/post-bg-map.jpg
catalog: true
tags:
    - python
    - data
---


Each day, stock prices fluctuate around their value.  Finance market has some criteria to evaluate share price level, such PE, PB, dividend and price ratio.  If a historic chart could indicate the yearly maximum and minimum PE, dividend and price ratio, that could give investors a baseline to compare, thus have an idea of where the current prices levels are. This would be mostly useful for some companies with stable revenue and profit development. 
 
Here is an example:

![](https://steemitimages.com/DQmRCK2rVF9PUopN2gWPZMp4xLty2WD749hquWPZYr7dsoZ/image.png)

![](https://steemitimages.com/DQmRxbZj9FcKMeswGLg12Kfh6WnmLfXTdhQDrDfNGqTufTx/image.png)

Most people cannot understand how useful these histogram charts are for investors!
 
e.g. 
With knowledge of the historic highest and lowest dividends, investors can make decisions on the buy or sell based on these censuses.
I set the high dividend ratio to 0.05, low dividend to 0.037,  which means if the market price divided by dividend exceeds 0.05,  I will buy, if it is less than 0.037, I will sell; I will hold in other circumstances. We can do a back test on how much we can earn over 2015 and 2016:
 
2015-01-16 00:00:00 strategy [INFO] BUY 5060 IRE.AX at $8.78/share
2015-02-16 00:00:00 strategy [INFO] SELL 5060 IRE.AX at $9.96/share
2015-03-03 00:00:00 strategy [INFO] BUY 5721 IRE.AX at $8.85/share
2015-05-18 00:00:00 strategy [INFO] SELL 5721 IRE.AX at $10.04/share
2015-08-21 00:00:00 strategy [INFO] BUY 6355 IRE.AX at $8.87/share
2016-03-09 00:00:00 strategy [INFO] SELL 6355 IRE.AX at $10.76/share
2016-06-29 00:00:00 strategy [INFO] BUY 6598 IRE.AX at $10.37/share
2016-07-14 00:00:00 strategy [INFO] SELL 6598 IRE.AX at $11.18/share
 
Name of the company IRESS
Initial portfolio value: $50000.00
Final portfolio value: $80072.78
net profit percentage:$60.15%



BTW,  blue chips in Australia,  U.S. are too expensive compared with China!   In China,  it looks money will go nowhere else except blue chips in the share market.  I can confidently announce a bull market is just starting in Chinese stock market!



More technical articles on ubundu，python，aws，data analysis: 

- [Solve a DNS issue in Ubundu VM](http://engineerman.club/2019/01/20/Solve-a-DNS-issue-in-Ubundu-VM/)
- 
  [create an instance in aws for free](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

- 
  [build a rest API service to provide market data for yourself](http://engineerman.club/2018/11/16/build-a-rest-API-service-to-provide-market-data-for-yourself/)

- 
  [Schedule regular tasks in AWS](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)

- 
  [How to access the EC2 instance in AWS](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

- 
  [How to extend my VM harddisk capacity in Ubundu](http://engineerman.club/2018/10/16/How-to-extend-my-VM-harddisk-capacity-in-Ubundu/)

- 
  [get historical data with python](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

- 
  [To share files between Windows and Unbundu](http://engineerman.club/2018/01/20/To-share-files-between-Windows-and-Unbundu/)

- 
  [How to share fold in hosted windows system with VM ubundu](http://engineerman.club/2018/01/20/How-to-share-fold-in-hosted-windows-system-with-VM-ubundu/)

- 
  [An Alternative to Yahoo Finance API in Australian Share Market](http://engineerman.club/2018/01/18/An-Alternative-to-Yahoo-Finance-API-in-Australian-Share-Market/)


- [using financial data to analyze Australian share market with help of python/pandas](http://engineerman.club/2018/01/16/using-financial-data-to-analyze-Australian-share-market-with-help-of-python/)

- 
  [How to host your Application to Heroku to build your own website](http://engineerman.club/2015/01/16/How-to-host-your-Application-to-Heroku-to-build-your-own-website/)

- [virtual machine and windows combination](http://engineerman.club/2010/01/16/virtual-machine-and-windows/)