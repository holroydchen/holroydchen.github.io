---
layout:     post
title:      learn from Magic Wallet to implement the exchange between bitUSD and USD(学习鼓鼓钱包实现法币和比特美元兑换)
subtitle:   
date:       2018-12-5
author:     Howard
header-img: img/post_blockchain.jpg
catalog: false
tags:
    - blockchain
    - bitshare
---

As we know, Bitshares is a decentralized cryptocurrency exchange.   It has some gateways to exchange with external market.  Whenever you want to transfer in or out coins with those centralized exchange, you need to navigate to this page:

![](https://steemitimages.com/DQmR2PmYWd2zpEyMdeDVc61GtZ287MBLg5oAzhuerNoJEbE/image.png)

This is the only channel to the outside world of BTS.  We can transfer our steem to BTS wallet via this way.  Scared of high commission fee and concerned of security in those centralized exchange, I once only played in BTS.



I have been playing in Bitshares for a while until one day, I transferred my steem from steemit account to BTS, I  was about to sell these steem for bitUSD, however, I found little liquid.  In order to sell out these steem, I need to put sell price much less than the market price.  Because at that time, the "openledger" shut down its Steem and ETH gateway, I have to use "RuDEX", but I did not aware there were so little liquidity in RuDEX （I cannot trade with steem in other gateways, since when I deposited via a gateway, that gateway only gave me an "IOU"）.  Even in "openledger", the liquidity is still very poor.  Then  I have to sell these steem out with a price much lower than the outside market ( although the price is quite higher with current price ).  After the openledger opened a door for us, I just jumped and escaped from BTS by sell bitUSD for ETH and withdraw ETH to a centralized exchange.  





The most disappointing thing for BTS is not less gateway to external market, but **there is no direct way to exchange bitUSD to fiat currency!!!**   We should learn from China, since although Chinese government has enforced harsh measures to  ICO and cryptocurrency trading,  this cannot stop brave Chinese people's passion on trading cryptocurrencies.   This app is called "Gu Gu  Wallet" or "Magic Wallet". The most critical feature of this app is it solves the problem of transfer between fiat  RMB and bitCny inside BTS system.  How can it solve this?  In this system,  entrepreneurs ( I call them brokers ) who want to do business to help people exchange between bitCny and RMB should deposit at least 50000 RMB ( stored in Bitshares as bitCny ) in the system at the beginning, which is about 10000 AUD.   When somebody has a deal with a broker to exchange for bitCny or RMB, those part of deposit will be locked by the Magic Wallet system in the BTS. After the client transfers money to the broker's account, the broker should transfer equivalent value of bitCny or RMB to the client. If the broker fails to do this,  the deposit in the system will be forfeited and given to the client.  If the client didn't transfer money to the broker, saying after half an hour, the locked bond of the broker will be automatically released by the system, thus the broker's interest is protected as well.



![](https://steemitimages.com/DQmPmH3QvfVAkewhJoyEUUdHczx1fE37yuGi8ryQxtpyEBm/image.png)





e.g.  Mr. Chen is a broker in the Magic Wallet system.  Miss Wang, who is a client of Chen and she wants to purchase 10000 bitCny so that she can  trade in the BTS.  She will find Chen's page and place an order for 10000 bitCny.  Miss Wang will get a code so that she can refer to when she transfers money to Chen. There are various ways to transfer to Chen, she can use Wechat wallet, or instant payment software, or  bank transfer.  When the order is placed, Chen's 10000 bitCny in his BTS account is locked.  



Case one: Miss Wang transfers 10000 RMB to Chen's account, and Chen transfers equivalent bitCny to Wang's BTS account, then Chen's account will be released;



Case two:  Miss Wang just makes a joke, so she doesn't really transfer any money to Chen. Therefore, after half an hour, Chen's account is released automatically.



Case three: Miss Wang transfers 10000 RMB to Chen's account. However, Chen is traveling in Cradle Mountain in Tasmania and he forgets this.  Thus, the locked bitCny will not be released until it is transferred to Wang's account. Here is a problem, a client may wait for a long period before he/she gets the bitCny and it is possible to miss an important opportunity to buy in. 



In current Bitshares, bitUSD cannot be converted to USD straightforward. It is must to transfer it to USD in this way:  bitUSD--->bitcoin or ethereum or other coins acceptable in a centralized exchange ---> withdraw via a gateway to external exchange---> in the centralized exchange, sell out the bitcoin, ethereum, whatever to get fiat currency.



This is why so few people would like to use BTS today!!!! At present, there are 5%~10% price gap between BTS and external market. But people cannot benefit from this, they cannot use their fiat to buy in bitUSD and buy in coins in BTS, then withdraw to sell out in external market. 



If people can convert their fiat directly to bitUSD in 1:1 ratio with a little commission fee,  they would pour into BTS to buy coins which has huge arbitrage margin with external market.   



A decentralized system is in great need so that every people can become a broker to help others exchange bitUSD with fiat currency,  in the meanwhile,  obtain some commissions to help themselves to make a living.  This system should be based on blockchain, so that it is trustless, it should also link to the real world currency system, e.g. paypal, so that brokers can deposit fiat in the first place instead of bitUSD, and paypal interface is programmable so that exchange of fiat can be detectable.



------



众所周知，比特股是一种去中心化的交易所，它有很多网关，如openledger, RuDEX, GDEX能把里面的数字货币（内盘）和外面那些中心化交易所的数字货币（外盘）联通起来，遗憾的是，网关数量太少了，而且在关键时候，会出大问题。上次大跌前，我差点就因为这些技术问题没把主力逃出来。我当时把我的steem转移到了比特股钱包里了，当时没多想，就通过RuDEX存进了比特股钱包，但是要知道RuDEX只是给了我一个“IOU"的欠条，所以RuDEX的steem卖单，只能跟RuDEX的买单去成交。所以流动性极差，即便是openledger，比较外盘，还是流动性太差。那次，由于openledger经不起太大负荷，居然把以太坊和steem的网关给挂了。这样我进去的steem，眼看就要烂在比特股钱包里了。我想把他们先换成bitUSD，但是我的卖单价格比外盘要低许多才可能成交，好吧，我忍。然后等到openledger的以太坊网关一开，我马上把这些bitUSD换成以太坊，然后withdraw到了外面的交易所里，最后换成法币。惊心啊，当时我可是6刀多卖的。从此哥惊吓过度，没敢再碰比特股钱包了。





咱暂且不谈比特股钱包网关太少的 问题，它的一个**致命问题就是它内盘的美元不能和外面的美元直接兑换！**

后来，机会偶然，我认识了”鼓鼓钱包“，就是巨蟹老前辈（虽然他年纪不一定比我大，但是在比特股这块，他是先驱）找人开发的产品，这款产品部分解决了一个重要问题，就是人民币和比特股内盘人民币互换的问题。它的机制是这样的，里面有很多承兑商，承兑商在一开始，就需要抵押价值1万人民币的bitCny在内盘里。如果有客户要兑换人民币或者内盘人民币，系统就会把这部分bitCny锁定，半小时后，客户没有转钱，就解锁，或者客户转钱了，承兑商也把人民币或者内盘人民币转给客户了，那么就解锁。



而在 比特股系统中，比特美元是无法直接兑换成法币的，它要兑换法币，只有一条路，先在内盘买入比特币或以太坊之类能被外盘接受的主流币，然后通过网关转移到外盘，最后在外盘卖掉换法币。这是多么麻烦的事情啊。外盘价格比内盘价格高5%到10%，美元不能换bitUSD，人们根本无法从这么好的套利机会受益，多么可惜。



如果比特美元也有类似鼓鼓系统这种人人可以申请做承销商，并且有抵押系统可以保证客户的安全，内盘外盘的价格差，早被 填平了，比特股钱包内盘交易量会增加许多。现在这情况，外盘数字货币价格那么高，怎么可能会涌到内盘去呢？所以比特美元对外通道被阻断了，它就变得没有意义了。





所以说，比特股钱包非常需要这样一个去中心化系统，每个人都能申请做承销商，帮助他人对法币和内盘美元兑换，这样不但有更多人可以有业务收入，而且能帮助比特股钱包引入更多流动性。



Related topics:


- [learn from Magic Wallet to implement the exchange between bitUSD and USD(学习鼓鼓钱包实现法币和比特美元兑换)
](http://engineerman.club/2018/12/05/learn-from-Magic-Wallet-to-implement-the-exchange-between-bitUSD-and-USD/)

- [Steem ranks second by China Ministry of Industry and Information](http://engineerman.club/2018/12/05/Steem-ranks-second-by-China-Ministry-of-Industry-and-Information/)

- [How to prevent DPOS being abused](http://engineerman.club/2018/12/05/How-to-prevent-DPOS-being-abused/)

- [What can SMTs do to encourage documentation for a company and my questions](http://engineerman.club/2018/10/20/SMTs-do-to-encourage-documentation/)