---
layout:     post
title:      How to host your Application to Heroku to build your own website
subtitle:   
date:       2015-1-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - heroku
---

Heroku is a platform as a service (PaaS) that enables developers to build, run, and operate applications entirely in the cloud.  It can provide free service for you to play with free domain name: 

![](https://steemitimages.com/DQmZ2sFueDbmUHPyyGpT1QYT1SxFqKNYHn9XGAetzvky4yb/image.png)

Here are the steps to import your applications to Heroku according to my own experience.



**Step 1**:  register in 'www.herokuapp.com';

**step 2**:  go to dashboard and click on 'New' and select 'create new App':

![](https://steemitimages.com/DQmVX1K4Aqei11s1fA3mZsLVxDfZzJdAbn65cBZ6EUNdQKL/image.png)

**step 3**: give a name for your App and select region to U.S then click 'Create app':

![](https://steemitimages.com/DQmXbUgpufUDfHd9PwSdEMqQHE7CYvVC9hVccQyjXZLbZbw/image.png)

**step 4**:  as for me, I don't need any additional feature, so I didn't choose pipeline.

![](https://steemitimages.com/DQmSswqtwgM4ZKh2LcGxP7PXqhxNbiPM95bLZ3i6xuUizxV/image.png)

Assuming you don't have a GitHub repository,  we select 'Heroku Git', so you need to install 'Heroku CL1':

![](https://steemitimages.com/DQmbbpNTs7MyKSWe2DZBN22bEM2Rizg2PQpJvLBrSikxkZP/image.png)



**step 5**:  install Heroku, install according to your local system.

![](https://steemitimages.com/DQmPjyPx7unhwDL7tt1G3V1DKLfC4JMuL5oijruGgndmNMV/image.png)

![](https://steemitimages.com/DQmaswnn2UYbDDq6ppd9sYSZVkqMwHBqYihSeW4AiW5JL7X/image.png)



**step 6**: open up git bash and put:

```
$ heroku login
```

![](https://steemitimages.com/DQmXNT7X3p5YtajkJMtUrq6DwDxidipQPAUpjReys3PEAVF/image.png)



**step 7**: Create a new Git repository:

```
$ cd your-project/
$ git init
$ heroku git:remote -a steemians-find-in-city
```



**step 8**: Deploy your application:

```
$ git add .
$ git commit -am "make it better"
$ git push heroku master
```



done:

![](https://steemitimages.com/DQmd4GJUyA4Lcxpwqh7c31C7vE6EbYXijR12mSuyQtCEfLT/image.png)



BTW, for existing Git repository, you just need this in step 7:

```
$ heroku git:remote -a steemians-find-in-city
```



**Trouble shot**:

After that, I run the application, but it complained error, then I checked the log:

`heroku logs`

and found:

`npm ERR! expresshello@0.0.0 start: node ./bin/www`



This makes sense to me, because my application should start like this:

`node app`

Then I went to `'package.json'` and amend the `scripts` section to this:

`"scripts": {`

    "start": "node app"
  `},`

then port the amendment to heroku:

`$ git add package.json`
`$ git commit -am "make it start"`
`$ git push heroku master`



Reopen the website:

https://steemians-find-in-city.herokuapp.com/



Found this error:

`Error R10 (Boot timeout) -> Web process failed to bind to $PORT within 60 seconds of launch`



The reason: Heroku dynamically assigns your app a port, so you can't set the port to a fixed number. Heroku adds the port to the env, so you can pull it from there. Switch your listen to this:

`.listen(process.env.PORT || 8888)`

That way it'll still listen to port 8888 when you test locally, but it will also work on Heroku.



Yeah, now it is working:

![](https://steemitimages.com/DQmWbCZ4VirWdXGNzmfpT6dsJWK6g3jxB9knAh8TQqwpvvL/image.png)