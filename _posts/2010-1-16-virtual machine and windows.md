---
layout:     post
title:      virtual machine and windows combination
subtitle:   
date:       2010-1-16
author:     Howard
header-img: img/post_fly_to_au.jpg
catalog: true
tags:
    - engineer
    - ubuntu
---

My home computer is Chinese languaged based windows system and my child cannot understand.  It is required to install a  linux  and English based system similiar to the school in my computer.  I don't want to switch from one system to another so I need to install the linux system in a VM. 

I once installed ubuntu 16.4 in my office PC using hyper-V as the virtual machine, the speed is acceptable and it is quite stable. However the office PC is windows 10.  My home PC is windows 7 and hyper-V cannot work in a workstation , it should work in a server or connect to a server, thus I cannot use hyper-V in windows 7.

I tried oracle virtual Box  as VM with ubuntu 17,  it is  fragile and reported memory broken several times,  failed.
Then I tried the same VM with 16.4, this time it is better,  however, it still threw out exception.

Finally I tried VM ware with ubuntu 16.4, this proved to be quite stable.

Updated 2017/9/2:  VM ware with ubuntu 16.4 is too slow and unacceptable, I tried with Apple Mac os x 10.10 today and it is much better. 

There are many bloggers who made comparsion between different virual machine softwares without really experience them. So be cautious about them.


Related topics: 

- [Solve a DNS issue in Ubundu VM](http://engineerman.club/2019/01/20/Solve-a-DNS-issue-in-Ubundu-VM/)

- 
  [How to extend my VM harddisk capacity in Ubundu](http://engineerman.club/2018/10/16/How-to-extend-my-VM-harddisk-capacity-in-Ubundu/)

- 
  [To share files between Windows and Unbundu](http://engineerman.club/2018/01/20/To-share-files-between-Windows-and-Unbundu/)

- 
  [How to share fold in hosted windows system with VM ubundu](http://engineerman.club/2018/01/20/How-to-share-fold-in-hosted-windows-system-with-VM-ubundu/)


- [virtual machine and windows combination](http://engineerman.club/2010/01/16/virtual-machine-and-windows/)