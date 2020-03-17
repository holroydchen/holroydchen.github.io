---
layout:     post
title:      How to extend my VM harddisk capacity in Ubundu
subtitle:   
date:       2018-10-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - ubundu
---


I setup a VMWare with guest machine running in Ubundu,  the capacity of hard disk was set to 40G.  It is too small for me now, I wanted to extend to 100G. 

Step 1:   Go to VM-->setting, click the hard disk option,  then select 'utilities',  and click on 'Extend', put the capacity to 100G.

Step 2:   In Ubundu, open up terminal, and install partition tool---gparted.

```
$sudo apt-get install gparted 
```

Step 3: open up gparted:
```
$sudo gparted 
```

then you can see the extended partition:
![](https://steemitimages.com/DQmcyYqLQKDqfcjBe9n4MVPqRCMqPjr8SP7tEeXr8GieFGK/image.png)

With gparted,  it is very easy to format the extended partition, then apply the change.


Step 4:  mount the extended partition to a point:

create a fold:
```
$sudo mkdir share
```

mount extended partition to share fold:

```
$sudo mount /dev/sda3 /home/chenlocus/share
```

Step 5:  setup automatic mount on Ubundu startup:

open up /etc/fstab with gedit:

```
$sudo gedit /etc/fstab
```

and put this(customize to your own conditions):

/dev/sda3   /home/chenlocus/share    auto   defaults  0   1

![](https://steemitimages.com/DQmThMDUqZNQgGHbtw42fLQyZdNKy6QursVNqN75G1h6uoj/image.png)


Save up.

Then even if you restart up your VM,  the extended partition will still be mounted to the share fold.



Related topics: 

- [Solve a DNS issue in Ubundu VM](http://engineerman.club/2019/01/20/Solve-a-DNS-issue-in-Ubundu-VM/)

- 
  [How to extend my VM harddisk capacity in Ubundu](http://engineerman.club/2018/10/16/How-to-extend-my-VM-harddisk-capacity-in-Ubundu/)

- 
  [To share files between Windows and Unbundu](http://engineerman.club/2018/01/20/To-share-files-between-Windows-and-Unbundu/)

- 
  [How to share fold in hosted windows system with VM ubundu](http://engineerman.club/2018/01/20/How-to-share-fold-in-hosted-windows-system-with-VM-ubundu/)


- [virtual machine and windows combination](http://engineerman.club/2010/01/16/virtual-machine-and-windows/)