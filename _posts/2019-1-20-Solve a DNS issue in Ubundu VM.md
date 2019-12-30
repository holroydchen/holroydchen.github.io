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