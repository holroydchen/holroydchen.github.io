---
layout:     post
title:      To share files between Windows and Unbundu
subtitle:   
date:       2018-1-20
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - ubundu
---


I once installed a VM with Unbundu in my host windows 10 system.  Having downloaded a huge file of 50GB, I  wanted to share this file with host windows system.  This is how to achieve it.


Step 1: Go to unbuntu and download samba:

```
sudo apt-get install samba
```

![](https://steemitimages.com/DQmUt5AB68xSh2vzmvdDs5APKP3uhLr7XphNETLo5vCULpu/image.png)


Step 2:  Setup password with existing account, holroyd is my account in unbundu:

```
smbpasswd -a holroyd
```

![](https://steemitimages.com/DQmaMJiEv8DPdXVVcF8aEeHYmGK6LDXnuAv3XLb39fXiQAS/image.png)


Step 3: make a fold in which you want to share your files:

```
mkdir ~/Desktop/Share
```

Step 4:   open the linux config file for samba: 

```
/etc/samba/smb.conf
```


scroll down to the end of the file and add lines like this:

```
[share]
path = /home/holroyd/share
available = yes
valid users = holroyd
read only = no
browsable = yes
public = yes
writable = yes
```

Save up this file.

Step 5:  execute the command to make the configuration work:

```
sudo service smbd restart
```


To visit this fold from Windows:

Step 1:  check your ip address in unbundu:

```
ifconfig -a
```

![](https://steemitimages.com/DQmZxvbTh41XrEzeviEvY1jonnPth7K8tqgxwp2SGauvDbx/image.png)

Step 2: access the fold like this: 

\\ipaddress\share fold

in my circumtance, it should be:

```
\\172.23.243.218\share
```



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