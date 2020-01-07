---
layout:     post
title:      Market Data to integrate cryptocurrency exchanges
subtitle:   
date:       2018-11-16
author:     Howard
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - engineer
    - python
    - data
    - restful
---

There are too many cryptocurrency  exchanges these days, they are running separately, so the price for the same cryptocurrency may be very different from one to another.  As I know, vast amount of investors are finding chance to make use of these differential prices  to arbitrage.  This website is to fulfill these purpose.  In [biglion.com.au](http://www.biglion.com.au/), there are currently 20 crypto tokens with best bid and ask, last traded price in more than five exchanges denoted with USDT asset, assuming USDT is equivalent to one USD. If a token price is not presented in USDT, I will get BTC price in USD, then multiply with the token's price in BTC.   This is a unique design to integrate those crypto exchanges, so far I have not seen the same product and this is also very meaningful according to my experience in stock market trading system.   The data will update every 10 seconds for now. 



In the future, there will be more and more cryptocurrencies and exchanges included.  The new release is currently under performance test  with tens exchanges.  There will be a team of more than 3 people to support this project.


[biglion.com.au](http://www.biglion.com.au/)
![](https://cdn.steemitimages.com/DQmdiu6oUA2AjsXWLLKHJ31UksBAj5pE2ChB3Y6Xmp1jA8E/image.png)





Furthermore, I was thinking to provide some approaches for people to automatically trade against certain exchange with best price.  However, after doing many investigations and together with my own experience in crypto trading, I don't think it is safe to use ANY centralized trading system. The reason is you have to use your private key to sign the message and send out your public key, your original message and your signature altogether to the exchange.  A system asking you to set your private key is unreliably.  Imaging what will happen if your private key is stolen by somebody else, although exchanges won't allow such actions as transfer, you still under the risk of getting lost if others use your private key to sell out your positions. 


![](https://cdn.steemitimages.com/DQmUbHyNCPzdna4J8DaRxk9NbdHKJq7CwjgYG9WJuJdM4r7/image.png)


One of the safer solution is to ask people to sign on their message in the first place, then send the signature to the trading system, however, this is a quite technical action, I don't think most people can adapt to that.   If a centralized system provides a tool for clients to do that, that's still risky, how do you know if your private key will be betrayed by that tool? 





The final solution and the most reliable one is to host the cryptocurrency trading system in a traditional stock trading broker,  so that we need to re-design the crypto trading system so that the brokers have the willing to host the system with their authority.  In the new trading system, a broker would register with different crypto exchanges, they have one business account with each exchange.  Then clients will register with broker just in the transitional approach.  A broker has numerous accounts associated with each client. Brokers provide market data depth to clients, if a client wants to trade, it is not required to jump to an exchange's website and takes efforts to register and authenticate, he/she just trades on the broker's site while broker sends this request to the exchange with its account. There are settlement system on a broker's system and clients need to deposit funds to the broker's on settlement day.  I think brokers can re-use their current settlement system with trading of crypto currencies since this process is almost the same as traditional equity trading.  





With that model, we put too much risks on the broker. A broker needs to deposit  a large amount of funds to variety of  crypto exchanges to make the system running.   How about the exchanges disappear and take away their money?  Thus the brokers must buy some sorts of insurance to mitigate this risk. As such, it is fair for the brokers to request for commissions.  With current situation in crypto currency trading,  would any brokers like to take this risk?  I don't think so.





In summary, for a cryptocurrency exchanges integrated trading system, none is better than any solutions. 



BTW, during the process of building up this exchanges market data integration system, I found STEEM is not listed in most exchanges:(



Related topics:


- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)