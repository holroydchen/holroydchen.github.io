---
layout:     post
title:      Schedule regular tasks in AWS
subtitle:   
date:       2018-11-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - aws
---

I spent lots of time on this tiny problem, I would like to tell you, all you see on other websites which teach you to use 'crobtab -e' or other method in Linux won't work in AWS, it looks AWS system  totally ignore those settings. I don't like those guys copy from each other without actually validating it, it really waste audiences' lots of time.

The only way to schedule regular tasks in aws via cron is to make a new file without any extension under this fold:

/etc/cron.d/

This is my setting:

vi /etc/cron.d/dailyPriceUpdate

![cron.d.PNG](https://cdn.steemitimages.com/DQmc6wYUXs5dvd2hqSHhDSCogPg1h8nu2iU5bSqWmzqXa3e/cron.d.PNG)
This means to use the 'root' role to:

1. go to directory /home/ubuntu/aushare, remember those environment path won't work automatically in cron;
2. execute /home/ubuntu/anaconda3/bin/python /home/ubuntu/aushare/ASXScrapShareDailyPrice.py;
3. log to /home/ubuntu/dailyPriceUpdate.log;
4. 2>&1 means log errors to the file as well.




Related topics: 

 - [Mine financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

 - [Get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

 - [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2020/01/12/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

 - [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

 - [build a python running environment in aws EC2 and use putty, winSCP to access your instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

 - [configure crontab in aws to schedule application.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)
