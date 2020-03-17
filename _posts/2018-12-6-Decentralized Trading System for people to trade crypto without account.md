---
layout:     post
title:      Decentralized Trading System for people to trade crypto without account
subtitle:   
date:       2018-12-6
author:     Howard
header-img: img/post_blockchain.jpg
catalog: false
tags:
    - blockchain
    - cryptocurrency
    - ethereum
---

After I presented the 'crypto exchanges integration' in hackathon in my company,  lots of colleagues asked me how to sign up in any exchanges, how to pick up exchanges, they have no idea how to buy and sell cryptocurrencies.  Some colleagues are  professional at trading in the market, but they feel sucks due to the low liquidity in current cryptocurrency market.  After talking with some brokers, actually none of those traditional brokers are likely to take this system due to unclear regulations.



This triggered my interest to build a decentralized crypto exchanges integration system.  e.g. Alice wants to buy in 10 BTC, however, he doesn't have any accounts in any crypto exchanges.  Jessie has signed up in BTCMarket,  Jerry has signed up in coinbase, Tom has signed up in binance.  Alice wants to buy in with price 9300USD,  she sends 9300X1 USD ( stable coins such as USDT, DAI, TUSD or Libra ) to a smart contract in Ethereum ( or EOS ) and sends his order.  





The system has a price feed to scan market data from many crypto exchanges and this is visible to all people.  Tom sees this order can be partially filled in binance so he takes the order and relay it to binance. 

Jerry relays part of the volume to coinbase and Jessie relays to BTCMarket.  


![](https://cdn.steemitimages.com/DQmTLRqiXP8WpD5paUBfcPyZu8TJmUQco7dkXwkTNpAEyee/image.png)


Once the orders get filled, Tom, Jerry and Jessie will send BTC to Alice's wallet address, once this is confirmed by Alice or the time is up, the smart contract will release stable USD coins to Tom, Jerry and Jessie's accounts.  After deduction of commission fee and transfer fee,  the surplus is returned to Alice's account.  Tom, Jerry and Jessie will be rewarded by smart contract accordingly.



The sell process is somehow like this: Alice wants to sell 10 BTC, so she sends out this order.  To save transfer fee, she can send the order in 'fill or kill' mode so that that order won't be split into small ones, or she can let it be so that order can be taken by different people. Tom will deposit some stable coins to the smart contract and 3 BTC will be sent to Tom's address and then he can either sell his own BTC to binance or wait until Alice's BTC arrives his account then sell it.  Jerry can do the same and sell order to coinbase.  Jessie can sell part of the order to BTCMarket.  On the settlement, Tom, Jerry and Jessie will send message to smart contract on how many volumes have been filled. The smart contract will ask them to return part of the BTC to Tom's account, once this is confirmed or time up, the smart contract will release stable coins to Alice's account based on how many BTC has been traded and return surplus to Tom, Jerry and Jessie after taking commission and transfer fees.  Tom, Jerry and Jessie will be rewarded by smart contract accordingly.

![](https://cdn.steemitimages.com/DQmTdmcL5WGqvjHVBEXcESvzp8MPA8dJs5rdZu4bLF8sJE8/image.png)

The stable coin is very important in this system and  to make things easy, we can use the existing stable coins such as USDT, GUSD, PAX which compliant to ERC20 if this system is running in Ethereum, or other stable coins based on EOS if this system will run on EOS. 



Assumption: convenient way for ordinary people to obtain stable coins by trading with fiat currency, with the Libra issued by Facebook, this is becoming more and more realistic and convenient.



Incentives:

- each time a transaction is completed, people who relay orders will be rewarded with 'DCI';
- 'DCI' is produced in the way only when a transaction happens after the system launches;
- when a transaction is completed,  there will be commission fee debited from users, this fee will be kept in the smart contract and send to 'DCI' holders regularly;
- 'DCI' holders are responsible for the vote for proposals such as proportion rewarded to brokers and how smart contract should work to maintain the community,  what stable coins should be included in the system.




Related topics:


- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)