---
layout:     post
title:      How to share fold in hosted windows system with VM ubundu
subtitle:   
date:       2018-1-20
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - ubundu
---


We can [share files in VM ubundu with hosted windows](https://steemit.com/technology/@chenlocus/to-share-files-between-windows-and-unbundu),  we can also share a fold in hosted windows system to it VM ubundu.


Step 1: set up the shared fold in the VM setting:

![](https://steemitimages.com/DQmb5YuNzWciqyxannjGxxaAya1p1Pp5FbNoqHG6noC4JB9/image.png)

Step 2: There is problems with  vm hgfs modules of open-vm-tools and it has  not been resolved yet. So we need to walk around this. 

We should go to ubundu and download the patches:

```
git clone https://github.com/rasa/vmware-tools-patches.git
```

Step 3:  Obtain the lates version of the vmware-tools:

```
cd vmware-tools-patches
./download-tools.sh 8.1.0
Untar and apply the patches
./untar-and-patch.sh
```

Step 4:   Compile and install the patched files.

```
./compile.sh
```

Then we can see the shared fold here in ubundu:
/mnt/hgfs



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