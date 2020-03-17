---
layout:     post
title:      MEETUBE A private blog
subtitle:   
date:       2019-1-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - nodejs
    - mongodb
---

Why I built up this platform

Years ago, when I got bored of sharing information in public and annoyed by strangers in all those social medias, I tried to find one place in which I can keep things to myself, adding friends out of my own will and sharing information with individuals, however, I failed. Then I spent numerous nights in my spare time developing prototype  to meet these needs.  It is something like a blog but actually not.  I deployed it in Heroku for the app part and the database in a MongoDB server.  Now it is in use by many of my friends, we collect things privately and share information whenever we want. This is a peaceful place to go if your brains are congested with too much modern spams! 

The name "Meetube"  jumped out of my inspiration, it means focusing on 'myself'. People who use this website collect information for themselves, there will be no bothering of advertisements or 'hello' from any strangers. All you want to do is write diary or copy/paste important information for yourself and share individual post with some of your friends if you want to. You won't be disturbed by others' messages unless you want to surf to 'friendship circle' part. 

![meetube.gif](https://res.cloudinary.com/hpiynhbhq/image/upload/v1509671932/wvcmvzzarxc5fv2km7uj.gif)

With this system, I'd like to keep information to myself and share with my friends if needed. 

How to use this platform

This is quite simple, sign up--->login in---->post,  ask your friends to use it, and add them to your friend list.  You can follow the video at the beginning of this story.

Here is how it looks like:
http://privatetube.herokuapp.com/


How to setup one of your own?

The first thing is to find a place for the database, mongolab can provide 500M space for free:
https://mlab.com/home

After signing up, I got username/password, database name, write  down the MongoDB URI on the up left corner of the page.
![image.png](https://res.cloudinary.com/hpiynhbhq/image/upload/v1509674147/iz4unauied6nrsefpey8.png)

With this URL, I did some code change in the original db relevant files.


Then I need to get a home for my node.js application.


https://www.heroku.com/




It provides 512M space domain for free, but if the website hibernates for 30 mins or so, you need to re-login.


There are quite lots of options on the start, enter the 'Node.js Get Started":







My system is windows, so I downloaded  Heroku Toolbelt for Windows following instruction on the next page. Then follow the step -by -step instructions.




$ heroku login
Enter your Heroku credentials.

Email: youremail.
Password: yourpassword


$ heroku create

Be aware: Heroku generates a random name (in this case sharp-rain-871) for your app, or you can pass a parameter to specify your own app name. D on't worry about ssl certification, the heroku create will do for you.

I typed:
$ heroku create privatetube
The name may be used already by other clients, so you need to change if needed.


If the app has already existed, do this:

$ heroku git:remote -a privatetube

Next step, deploy the code:
$git init
$git add .
$git commit -m "Initial commit."
$ git push heroku master

All done.



Related topic:

- 
  [How to host your Application to Heroku to build your own website](http://engineerman.club/2015/01/16/How-to-host-your-Application-to-Heroku-to-build-your-own-website/)
