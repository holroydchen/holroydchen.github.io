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