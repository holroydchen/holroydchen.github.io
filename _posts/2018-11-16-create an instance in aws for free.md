---
layout:     post
title:      create an instance in aws for free
subtitle:   
date:       2018-11-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - aws
---


It takes ages for normal computer to run through the script to download all listed historical price. Hence I applied Amazon Web Service. AWS has a one year free tier so we can apply for this option to low our cost. There is another advantage, you can get access to your personal data wherever you are. 



There are many such articles on the internet guiding how to apply and install a free EC2 instance in AWS, I won't do something redundant here. This is the one I found very informative:



https://www.brianlinkletter.com/create-a-free-virtual-private-server-on-amazon-web-services/



For me, the operation system I setup is ubuntu. You need to save the private key file to your computer for further usage to get access to the aws instance. 

Some tips:

1. Be aware of the geographic area you choose, I forgot to choose this and it defaulted to 'Ohio' in America. It takes a little bit of money and some trouble to migrate to another geographic section.  So you need to think of this in the first place. 

![1543381102102.png](https://cdn.steemitimages.com/DQmaZkH9tb8x91vrsGGSLkwJwcqwjcDfQr5mbmqU5yt6Nys/1543381102102.png)



2. You'd better just establish one instance since the free tier one year allows you to run EC2 750 hours  per month, so one instance is just right.



3. There is no need to use S3 service for data storage, since EC2 is enough for that. I once created a S3 bucket and upload all those files, the request exceeded 2000 then I was charged a little bit.



4. If you apply a domain name somewhere and want to link to the IP address in aws, you are using the Route 53 service in aws and this will charge you 0.55 USD per month. Another point is you need a fixed IP address to bond with your domain name.  To do this, you need to 'Allocate new address':

![1543382782587.png](https://cdn.steemitimages.com/DQmcF4ZNHgvKUYFBPuHk9L7W18XCPKjw6ZKWSgnUghEMi4b/1543382782587.png)

Also check if the previous IP address has been released, otherwise, you will be charged by Amazon, to check this, right click the IP address and the 'Release address' should be grayed out.

![1543383012953.png](https://cdn.steemitimages.com/DQmcAS5Lw6gxf4AcLidttmttXUytSaZqhSRvWvS5qaTpPte/1543383012953.png)



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