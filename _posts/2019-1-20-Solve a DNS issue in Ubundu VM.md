---
layout:     post
title:      Solve a DNS issue in Ubundu VM
subtitle:   
date:       2019-1-20
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - ubundu
---


I once set up a virtual machine hosted in windows and installed Ubundu 16.04 LTS, it was running well and I could surf internet as well.

However, browsers got inaccessible for me yesterday. It always complained 'resolving host' while I tried to  surf on internet browser.  It looks the DNS could not interpret the domain name to IP address. I tried many ways I searched online, however, none of them could work for me. I began to suspect the old DNS may not work anymore for me, but the DNS configured on my host PC was working.  I used `ipconfig` to check net status in my host machine and it looks it has several DNS setup.  



Opening up the system setting in Ubundu and you can see 'Network' icon:

![](https://steemitimages.com/DQmWomiKq49DXBsAahnqqZheNZwpL5y6UFvUeVLSKvYnGpQ/image.png)



Open up the 'Network' and go to 'options',  choose the 'IPv4 Settings' tab,  put the DNS which is working in the host to the 'Additional DNS servers':

![](https://steemitimages.com/DQmS4qkMoSN6yXnqD4oovNzZvSbDBXAgCxFdQ1qbZy6ym9F/image.png)



All good now,  no need to restart the ubundu for me:)




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