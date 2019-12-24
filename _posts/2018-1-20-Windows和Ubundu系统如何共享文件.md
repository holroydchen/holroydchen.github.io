---
layout:     post
title:      Windows和Ubundu系统如何共享文件
subtitle:   
date:       2018-1-20
author:     土猪
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - ubundu
---


我在自己的windows10主机上装了个虚拟机，虚拟机上装了ubundu操作系统。前不久，我在ubundu上下载了一个50G的大文件，然后我想把这文件共享到我的windows系统上。



先转到ubundu上下载samba：

sudo apt-get install samba

![](https://steemitimages.com/DQmUt5AB68xSh2vzmvdDs5APKP3uhLr7XphNETLo5vCULpu/image.png)


再来设置用户名和密码，holroyd是我在ubundu上的账号：

smbpasswd -a holroyd

![](https://steemitimages.com/DQmaMJiEv8DPdXVVcF8aEeHYmGK6LDXnuAv3XLb39fXiQAS/image.png)


然后再来设置个文件夹，把要分享的文件拷贝过去：

mkdir ~/Desktop/Share


打开这个文件进行编辑：

/etc/samba/smb.conf

编辑结果如下：

[share] 
path = /home/holroyd/share
available = yes 
valid users = holroyd
read only = no 
browsable = yes 
public = yes 
writable = yes

保存下这个文件，执行这个命令：

sudo service smbd restart


从windows访问这个文件夹：

\\ipaddress\share fold

用这个命令看ubundu的机器ip地址：
ifconfig -a

![](https://steemitimages.com/DQmZxvbTh41XrEzeviEvY1jonnPth7K8tqgxwp2SGauvDbx/image.png)

那么我就这样访问：
\\172.23.243.218\share