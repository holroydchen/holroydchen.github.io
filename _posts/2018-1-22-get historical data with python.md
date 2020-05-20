---
layout:     post
title:      get historical data with python
subtitle:   
date:       2018-1-22
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - python
    - pandas
    - data mining
---

In the [previous post](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/), we talked about [a substitute for yahoo finance API](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/)  which was offline years ago.  In this post, I would like to explain how to crawl data from yahoo finance and after filtering duplicated, blanked data then dispatch them to categorized .csv files.  I would describe how to make it work with my existing python scripts then explain the details of some of the key codes. 



All codes are here in github for educational purpose:

https://github.com/chenlocus/aushare



When we want share prices, the first thing we may ask ourselves: how many companies are listed in ASX?  Here is what we can see in ASX official website:

https://www.asx.com.au/asx/research/ASXListedCompanies.csv

( there is a constant in stock.cons.py to keep this:

ASXLIST_FILE = 'https://www.asx.com.au/asx/research/ASXListedCompanies.csv')



So we can download historical market data based on this list.  But be aware, although there are 2257 companies listed in this spread sheet,  there are lots 'dead' codes which may be delisted without updating the document or no trades at all, so actually there are about 1800 equity codes.  We will use some data clean technology to filter out these 'dead' instruments.



Some pre-conditions should be met before you run this python script, and I will explain some most parts of the code.  



ASXScrapShareDailyPrice.py is the script you can run. Before that, something need to be carried out:

1. go to https://www.python.org/downloads/ to download the latest python version, 3.7.1 should be fine;
2. use pip install to setup these modules: selenium, bs4, lxml, pandas. 

```
pip install selenium

pip install bs4

pip install lxml

pip install pandas
```

3. download phantomjs (http://phantomjs.org/download.html), unzip and put it in the fold:  /usr/local/bin/phantomjs or any other fold you can specify in the code: 

`browser = webdriver.PhantomJS(executable_path='/usr/local/bin/phantomjs')` 



To run the python script:

```
cd /aushare

python ASXScrapShareDailyPrice.py
```



Inside 'ASXScrapShareDailyPrice.py', there are two lines to get the right link to obtain daily historical data, there are '%s' for further customization inside the codes, DAILY_PRICE is the place  to get historical data if this has never been executed before,  while the purpose of  DAILY_PRICE_DELTA is to keep your historical data file up to date.



`DAILY_PRICE_DELTA = "https://au.finance.yahoo.com/quote/%s.AX/history?period1=%s&period2=%s&interval=1d&filter=history&frequency=1d"`
`DAILY_PRICE ='https://au.finance.yahoo.com/quote/%s.AX/history?period1=0&period2=%s&interval=1d&filter=history&frequency=1d'`



These codes read all the security codes listed in ASX:



`df =pd.read_csv(ASXLIST_FILE_NAME,header=1)`
`codelist = df['ASX code'].values`

`for symbol in codelist:`



If you have already executed the script and there is historical price data file, the script will read the existing file and get the latest date, then it will scrape data from this point after so that no duplicate work is needed for the existing data. These are implemented here. 

```
for symbol in codelist:
    file_name = ct.DAILY_PRICE_FILE%symbol
    
```

    if os.path.isfile(file_name):
        df = pd.read_csv(file_name,header=0, index_col =0,date_parser=_parser,skipfooter =1,engine='python')
        if (df.empty):
            continue
        df.reset_index(inplace =True)
        earliest_date = df['Date'].min()
        print(earliest_date)
        s2 = earliest_date -timedelta(days=1)
        print(s2)
        period2= int(time.mktime(s2.timetuple()))

​    

```
url = DAILY_PRICE_DELTA%(symbol,period2)
    no_of_pagedowns = 50
else:
    print('file does not exist')
```


​    
​    
When we surf a web page, usually we need to scroll down to view the whole page, in order not to miss anything, I hard coded the scroll pages as 50. 


There are quite a few webdrivers to interact with html in web pages, I once tried chrome driver, but it cannot run in the background, the chrome had to show up and down which not only exaust lots of memories but also made the scraping task extremely slow. So I switched to PhantomJS to run the task in background without any UI showing up.



```
browser = webdriver.PhantomJS(executable_path='/usr/local/bin/phantomjs')                
print(url)
browser.get(url)
time.sleep(1)
elem = browser.find_element_by_tag_name("body")
```

   

    while no_of_pagedowns:
        browser.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(0.5)
        no_of_pagedowns-=1
        
    source_data = browser.page_source    




'BeautifulSoup' is a perfect module to analyze source html data from web page,  the 'attrs' may need to change from time to time in case the website changes the attributes in the pages.  Data is combined to the existing data from the file then flush the file. I have tried to append them to the existing file for efficiency but no way.  Redundant data is removed by the function  'drop_duplicates' in pandas. 

```
try:
        soup = BeautifulSoup(source_data, "lxml")
        tb = soup.find("table",attrs = {"data-test":"historical-prices"})
        na_values = ['NaN', 'N/A', '-']
        df1 = pd.read_html(str(tb),header=0,index_col=0,na_values=na_values)
        if df1[0] is not None:
            if os.path.isfile(file_name):
                df2 = df1[0]
                print(df2)
                df = pd.read_csv(file_name,header=0, index_col =0)
                df=df[:-1]
                print(df)
                df3 = [df,df2]
                result = pd.concat(df3)
                print(result)
                result.drop_duplicates(inplace=True)
                print('okokok nearly ok')
                result.to_csv(file_name)
            else:
                print('file does not exist')
    except:
        print("The instrument may be delisted.")
        continue
    browser.close()
    browser.quit()
```

'browser.close()' and 'browser.quit()' are very import after each time scraping data since they will actually purify the memory for the next run.  I have tried using the 'close' only, but after tens of run, the memory will be exhausted thus the whole application stuck. It looks only after I 'quit' the PhantomJS, it can actually release memories, so this is very important to let the application run a long time to scrape all financial data from yahoo finance.
    



The format and location of the historical data file to be exported is defined in stock.cons.py:

`DAILY_PRICE_FILE = 'data/daily/%s_price.csv'`

So if the symbol name is 'Z1P', the file will be located in data/daily and the file name will be 'Z1P_price.csv'.

cons.py is an important file defining where to scrape data and where to save:

```
ASXLIST_FILE_NAME = './data/ASXlistcodes.csv'
ASXLIST_FILE = 'https://www.asx.com.au/asx/research/ASXListedCompanies.csv'
INCOME_ANNUAL_REPORT = 'https://finance.yahoo.com/quote/%s.AX/financials?p=%s.AX'
BALANCE_SHEET_ANNUAL_REPORT = 'https://au.finance.yahoo.com/quote/%s.AX/balance-sheet?p=%s.AX'
CASH_FLOW_ANNUAL_REPORT = 'https://au.finance.yahoo.com/quote/%s.AX/cash-flow?p=%s.AX'
WEEKLY_PRICE ='https://au.finance.yahoo.com/quote/%s.AX/history?period1=%d&period2=%d&interval=1wk&filter=history&frequency=1wk'
PERSHARE_FINANCIAL_INFO ='https://www.investsmart.com.au/shares/asx-%s/%s/financials'
STATISTICS_INFO = 'https://au.finance.yahoo.com/quote/%s.AX/key-statistics?p=%s.AX'

BALANCE_SHEET_FILE = 'data/financial/%s_balance.csv'
REVENUE_FILE = 'data/financial/%s_revenue.csv'
CASHFLOW_FILE = 'data/financial/%s_cashflow.csv'
DELIST_FILE = 'data/ASXDelistcodes.csv'
WEEKLY_PRICE_FILE = 'data/weekly/%s_price.csv'
DAILY_PRICE_FILE = 'data/daily/%s_price.csv'
```



Some people ( like me ) prefer to analyze share market using fundamental financial report, to catch balance sheet,  annual revenue report and cash flow, you need to run these python scripts with [jupyter notebook](http://jupyter.org/).

```
ASXDataScrapBalance.ipynb

ASXDataScrapRevenue.ipynb

ASXDateScrapCashflow.ipynb
```



The mechanism of these scripts are almost the same as `ASXScrapShareDailyPrice`, but much simpler. 



Please note: don't use `threadpool` in downloading data, this can overwhelm the server and you will be given an error code 429 or even IP ban. 



Finally,  you need to [schedule regular tasks](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/) in your own computer or aws to download data for further restful API usage. 



Related topics: 

 - [Mine financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

 - [Get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

 - [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2020/01/12/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

 - [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

 - [build a python running environment in aws EC2 and use putty, winSCP to access your instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

 - [configure crontab in aws to schedule application.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)
