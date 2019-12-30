---
layout:     post
title:      How to extend my VM harddisk capacity in Ubundu
subtitle:   
date:       2018-10-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
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