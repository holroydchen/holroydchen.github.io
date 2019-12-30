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