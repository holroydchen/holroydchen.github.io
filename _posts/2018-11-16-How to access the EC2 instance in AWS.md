---
layout:     post
title:      How to access the EC2 instance in AWS
subtitle:   
date:       2018-11-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - aws
---

After build an instance in AWS, the next thing is to access the instance to install software such as python, python modules and the rest API software. 


I am not going to rebuild the wheel, instead use the existing official document in amazon, which is quite useful and informative:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html

Prior to the process, we need to prepare the private key file and convert it to .ppk file following the instruction in the link above 'To convert your private key'. 

With Putty, we can get access to the terminal to install files and run applications. The first thing we need to do is to install python3, we can follow this instruction to accomplish:

https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-linux-python.html

My system in EC2 is ubuntu, so I used the following command:

`$ sudo apt-get install python3`


winSCP is a powerful tool to download and upload files with remote computers,  simply following the instruction above, it will prompt you to import settings, keys in putty during the process. Then we can exchange files with aws EC2 instance:

![winscp.JPG](https://cdn.steemitimages.com/DQmUAp1Xaq2wEnQGDbX1naPu3qfm1Ni6Y9ixA31fnVAMqWx/winscp.JPG)