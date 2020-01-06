---
layout:     post
title:      get historical data with python
subtitle:   
date:       2018-1-22
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - python
    - pandas
    - data
---

When we want share prices, the first thing we may ask ourselves: how many companies are listed in ASX?  Here is what we can see in ASX official website:

https://www.asx.com.au/asx/research/ASXListedCompanies.csv

( there is a constant in stock.cons.py to remember this:

ASXLIST_FILE = 'https://www.asx.com.au/asx/research/ASXListedCompanies.csv')



So we can download historical market data based on this list.  But be aware, although there are 2257 companies listed in this spread sheet,  there are lots 'dead' codes which may be delisted without updating the document or no trades at all, so actually there are about 1800 equity codes.  We will use some data clean technology to filter out these 'dead' instruments.



Some pre-conditions should be met before you run this python script, and I will explain some most parts of the code.  



ASXScrapShareDailyPrice.py is the script you can run. Before that, something need to be carried out:

1. go to https://www.python.org/downloads/ to download the latest python version, 3.7.1 should be fine;

2. use pip install to setup these modules: selenium, bs4, lxml, pandas. 

3. download phantomjs (http://phantomjs.org/download.html), unzip and put it in the fold:  /usr/local/bin/phantomjs or any other fold you can specify in the code: 

   `browser = webdriver.PhantomJS(executable_path='/usr/local/bin/phantomjs')` 

To run the python script:

```
cd /aushare

python ASXScrapShareDailyPrice.py
```



These two lines are to get the right link to obtain daily historical data, there are '%s' for further customization inside the codes, DAILY_PRICE is the place  to get historical data if this has never been executed before,  while the purpose of  DAILY_PRICE_DELTA is to keep your historical data file up to date.



`DAILY_PRICE_DELTA = "https://au.finance.yahoo.com/quote/%s.AX/history?period1=%s&period2=%s&interval=1d&filter=history&frequency=1d"`
`DAILY_PRICE ='https://au.finance.yahoo.com/quote/%s.AX/history?period1=0&period2=%s&interval=1d&filter=history&frequency=1d'`



These codes read all the codes listed in ASX:



`df =pd.read_csv(ASXLIST_FILE_NAME,header=1)`
`codelist = df['ASX code'].values`

`for symbol in codelist:`



If you have already executed the script and there is historical price data file, the script will read the existing file and get the latest date, then it will snatch data from this point after so that no duplicate work is needed for the existing data. These are implemented here:



`if os.path.isfile(file_name):`
       

```
 df = pd.read_csv(file_name,header=0, index_col =0,date_parser=_parser,skipfooter =1,engine='python')
        if (df.empty):
            continue
        df.reset_index(inplace =True)
        recent_date = df['Date'].max()
        print(recent_date)
        s1 = recent_date +timedelta(days=1)
        print(s1)
```

​        `period1= int(time.mktime(s1.timetuple()))`

        url = DAILY_PRICE_DELTA%(symbol,period1,period2)
        no_of_pagedowns = 2
    else:
        period2= int(time.mktime(s2.timetuple()))
        url = DAILY_PRICE%(symbol,period2)
        no_of_pagedowns = 50
After downloading the data, we need to filter out those duplicated ones, I noted there are quite lots of invalid duplicated prices in yahoo finance, but we should not complain about it since it is free.  This is to clean out duplicated data:



`result.drop_duplicates(inplace=True)`



The final format and location of the historical data file would be defined in stock.cons.py:

`DAILY_PRICE_FILE = 'data/daily/%s_price.csv'`



So if the symbol name is 'Z1P', the file will be located in data/daily and the file name will be Z1P_price.csv.



Some people ( like me ) prefer to analyze share market using fundamental financial report, to catch balance sheet,  annual revenue report and cash flow, you need to run these python scripts with jupyter notebook ( to install jupyter you can go here: http://jupyter.org/ ):

ASXDataScrapBalance.ipynb

ASXDataScrapRevenue.ipynb

ASXDateScrapCashflow.ipynb



The mechanism of these scripts are almost the same as ASXScrapShareDailyPrice, but much simpler. 



Please note: don't use threadpool in downloading data, this can overwhelm the server and you will be given an error code 429 or even IP ban. 



All codes are here in github for educational purpose:

https://github.com/chenlocus/aushare



Related topics: 

 - [Mine financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

 - [Get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

 - [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2018/11/16/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

 - [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

 - [build a python running environment in aws EC2 and use putty, winSCP to access your instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

 - [configure crontab in aws to schedule application.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)
