---
layout:     post
title:      Build a restful API service with flask,gunicorn and nginx
subtitle:   
date:       2020-1-12
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: false
tags:
    - aws
    - restful
    - flask
    - python
---

In the [previous post](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/), we talked about [a substitute for yahoo finance API](http://engineerman.club/2018/01/20/Way-to-get-existing-data-and-organize-in-your-own-use/)  which was offline years ago.  I have described [how to scrape data from such web pages as yahoo finance](http://engineerman.club/2018/01/22/get-historical-data-with-python/). 



In this post, I would like to explain how to make use of those downloaded data to provide restful API service.  I will explain the codes as well as how to make it work with the existing python script. All codes are here in github for educational purpose:

https://github.com/chenlocus/aushare



The framework I used is python flask, which is a micro service framework and very efficient in building restful API service. I once thought of doing this with aws API which can provide elastic scalability, however, the application will be tightly relying on aws in that way.  I would keep my application independent and portable, so I only used the EC2 (Elastic Computer) service.  



Prior to running the script, we need to install some modules: flask, flask_limiter, flask_monitoringdashboard, gevent using pip:

```
pip install flask

pip install flask_limiter

pip install flask_monitoringdashboard

pip install gevent
```



These modules are imported for rest API service:



`from flask import Flask, request, g`
`from flask import render_template,jsonify`



Some people just want to download the .csv files, in order to provide that function, we need to import this module in flask:

`from flask import send_file`



I don't want my server being flooded, so I imported these modules to control the request limit:



`from flask_limiter import Limiter`
`from flask_limiter.util import get_ipaddr`



I use `get_ipaddr`  here to obtain the real IP address of the request to avoid overwhelming request, a request will pass through many agents in the route, this function can withdraw the initial IP address of the request.  This is how to make use of `get_ipaddr`:

```
app = Flask(__name__)
dashboard.config.init_from(file='dashboard.cfg')
dashboard.bind(app)
limiter = Limiter(
    app,
    key_func=get_ipaddr,
    #default_limits=["300 per day","2 per minute", "1 per second"],
    default_limits=["200 per day"],
)
```



flask does not support asynchronous request, so I import gevent for this purpose:

`from gevent import monkey`
`from gevent.pywsgi import WSGIServer`
`monkey.patch_all()`



To have a record of the API performance, we need to import this:

`import flask_monitoringdashboard as dashboard`



In another fold 'stock', I processed all the things with basic request and location of .csv files and web links on market data,  we need to import these modules as well:



`import aushare.stock.fundamental as td`
`from aushare.stock import cons as ct`



I used a lot of `pandas` to read data from .csv I have obtained and converted them to to the json format I need for private trading system.  I organized basic function call such as `getAllASXListCode, getASXListName, getRevenue, getWeeklyPrice, getMeanPriceDiffPercentage,getBalanceSheet , getHisWeeklyPrice` in stock.fundamental.py.  In these functions, I will firstly try to withdraw data from the downloaded file,  if not we will try to scrape from the website, e.g.

This is to get historic weekly price on a certain date range, firstly I tried to read from the downloaded file using date format specified in '_parser' function, then reset the index of the dataframe without creating a duplicated one by the parameter 'inplace = True'.  The 'df = df[operation]' is a very typical operation of pandas dataframe and is very useful in my data process.



```
def getHisWeeklyPrice(code='APT',datefrom='18/05/2018', dateto='18/09/2018'):
    file_name = ct.WEEKLY_PRICE_FILE%code
    if os.path.isfile(file_name):
            df = pd.read_csv(file_name,header=0, index_col =0,date_parser=_parser,skipfooter =1,engine='python')
            
            df.reset_index(inplace =True) 
            datefrom = datetime.strptime(datefrom,'%d/%m/%Y')
            dateto = datetime.strptime(dateto,'%d/%m/%Y')
            df = df[(df['Date'] > datefrom) & (df['Date'] <= dateto)]
            return df

​```
try:
    urlbase = ct.WEEKLY_PRICE
    s = datefrom
    period1= int(time.mktime(datetime.strptime(s, "%d/%m/%Y").timetuple()))
    s = dateto
    period2= int(time.mktime(datetime.strptime(s, "%d/%m/%Y").timetuple()))
    code = code
    url = urlbase%(code,period1,period2)
    print(url)
    response = urllib.request.urlopen(url).read().decode('utf-8')
    soup = BeautifulSoup(response, "lxml")
    tb = soup.find("table",attrs = {"data-test":"historical-prices"})
    na_values = ['NaN', 'N/A', '-']
    df1 = pd.read_html(str(tb),header=0,index_col=0,na_values=na_values)
    return df1[0]
except:
    print('No weekly price found for the code ')
    return None
​```

def _parser(date):
    try:  
        return pd.datetime.strptime(date, '%d %b %Y')
    except:  
        try:
            return pd.datetime.strptime(date, '%d/%m/%Y')
        except:
            return pd.datetime.strptime(date, '%d %b. %Y')
```



Now we are entering the main part of the scripts, we can recognize how powerful the dataframe provided by pandas is. It can return data in any format including json, it can also re-organize the column with rename, the most appealing feature is filter data I want.   



```
app.config.update(DEBUG=True)

@app.route('/', methods=['GET', 'POST'])
@limiter.limit("200 per day")
def homepage():
    # if flask.request.method == 'GET':
    #     result = {}
    #     return render_template("homepage.html", result=result)
    # elif flask.request.method == 'POST'and flask.request.form.get('query', None) == "查询":
    #     stock_no = flask.request.form['storkcode']
    #     code = stock_check(stock_no)
    #     if code != 0:
    #         result = result_parse(get_stock(code))
    #         return render_template("homepage.html", result=result)
    #     else:
    #         return render_template("homepage.html", warning="XXXXXXXX")

​```
return render_template("index.html")
​```

@app.route('/api/v1/asx/snapshot/', methods=['GET'])
@shared_limiter
def getRealtimePrice():
    print("There is a request for realtime market snapshot.")
    print(request.args)
    print(get_ipaddr())
    my_ip_set.add(get_ipaddr())
    symbol = request.args['symbol']
    symbolist = symbol.split(',')
    

​```
symbollen = min(len(symbolist), MAX_SYMBOLS)
print(symbollen)
symbolist = symbolist[:symbollen]
print(symbolist)

dflist = []

for symbol in symbolist:
    url = "https://www.asx.com.au/asx/1/share/%s"%symbol
    print(url)
    df = pd.read_json(url,orient='columns',typ='series')
    df = df[['code','bid_price','offer_price','open_price','last_price','change_in_percent',
              'change_price','day_high_price','day_low_price','average_daily_volume','volume',
               'previous_close_price','previous_day_percentage_change','eps','pe','annual_dividend_yield',
               'market_cap','number_of_shares','year_change_in_percentage','year_change_price','year_high_date',
              'year_high_price','year_low_date','year_low_price','year_open_date','year_open_price']]
    df_T = pd.DataFrame(df).transpose()
    dflist.append(df_T)
result = pd.concat(dflist)
result.set_index(['code'],inplace =True)

print(result)
return result.to_json(orient='index'),200
​```

@app.route('/api/v1/asx/history/year/', methods=['GET'])
@shared_limiter
def getHistroyYearlyPrice():
    print("There is a request for histroical price yearly price.")
    print(request.args)
    my_ip_set.add(get_ipaddr())
    symbol = request.args['symbol']
    frequency = request.args['frequency']
    year = request.args['year']
    if frequency =='weekly':
        df = td.getWeeklyPrice(symbol,year).set_index('Date')
        df.rename(columns={"Close*": "Close", "Adj. close**": "Adjust Close"},inplace=True)
        try:
            df = df[df.Open.str.contains("Dividend") == False]
        except:
            print('this is not downloaded file')
        df.index = df.index.strftime('%Y-%m-%d')
        return (df.to_json(orient='index',date_format='iso',date_unit='s')),200

​```
return 'false request'


​```


```

Having talk so far, it's time to focus on how to make it run.



https://github.com/chenlocus/aushare/haoserver.py is the python script you need to run. 



Actually, flask is not a professional web server, so we can use gunicorn to run this server. 



1) install gunicorn:

```
pip install gunicorn
```



2) run the server with gunicorn, '&' is to keep it a demo running in background, 'nohup' keeps the application running even if you exit the terminal. 

`nohup gunicorn  -b 127.0.0.1: 12345 haoserver:app &`



For the above command, it is mostly used in intranet or semi-product environment. In product environment, clients need to visit from extranet on port 8000 by default, and we need to process concurrent request, load balance. There is a powerful kit we can use which is Nginx, written by a Russian engineer.  

Go to this file in EC2 instance using putty:

`/etc/nginx/site-available/default`



	server {
	
		listen 80 default_server;
	
		listen [::]:80 default_server;
	
	# SSL configuration
	#
	# listen 443 ssl default_server;
	# listen [::]:443 ssl default_server;
	#
	# Note: You should disable gzip for SSL traffic.
	# See: https://bugs.debian.org/773332
	#
	# Read up on ssl_ciphers to ensure a secure configuration.
	# See: https://bugs.debian.org/765782
	#
	# Self signed certs generated by the ssl-cert package
	# Don't use them in a production server!
	#
	# include snippets/snakeoil.conf;
	
	root /var/www/html;
	
	# Add index.php to the list if you are using PHP
	index index.html index.htm index.nginx-debian.html;
	
	server_name _;
	
	location / {
		proxy_pass http://127.0.0.1:12345;
		proxy_set_header Host $host;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		#try_files $uri $uri/ =404;
	}


Then reload the setting to nginx, all done. 

`nginx -s reload`







Related topics: 

 - [Mine financial data from yahoo finance including historical price, balance sheet, income and cash report, and how to keep this up to date.](http://engineerman.club/2018/01/22/get-historical-data-with-python/)

 - [Get delayed real time price directly from ASX.](http://engineerman.club/2018/01/22/get-delayed-price-directly-from-ASX/)

 - [Build a restful API service with flask,gunicorn and nginx.](http://engineerman.club/2020/01/12/build-a-rest-API-service-to-provide-market-data-for-yourself/) 

 - [Create an instance in aws for free.](http://engineerman.club/2018/11/16/create-an-instance-in-aws-for-free/)

 - [build a python running environment in aws EC2 and use putty, winSCP to access your instance.](http://engineerman.club/2018/11/16/How-to-access-the-EC2-instance-in-AWS/)

 - [configure crontab in aws to schedule application.](http://engineerman.club/2018/11/16/Schedule-regular-tasks-in-AWS/)
