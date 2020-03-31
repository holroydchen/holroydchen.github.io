---
layout:     post
title:      MetaMask account was hacked
subtitle:   
date:       2020-3-31
author:     Howard
header-img: img/post_blockchain.jpg
catalog: false
tags:
    - cryptocurrency
    - steem
    - ethereum
---

Days ago I wrote an article [How to convert steem to eth](http://engineerman.club/2020/03/26/How-to-convert-steem-to-ETH-from-steemit-to-your-ETH-account/)，I saw the eth flashed in my wallet then disappeared. 



I was so discontented not because of the 16 usd worth of eth, but my confidence in decentralized system was shaken. I decided to make things clear. 


The asset flow was like this: I transferred steem to 'blocktrades', in return, it transferred specified eth to my wallet and charged me some comission. I was using metamask chrome plug in for my eth wallet.  Actually I didn't use that wallet at all, except I used it once for smart contract development, but that's telnet, not in the main net. But they share the same seed and private key. 



In the first place, I suspect 'blocktrades' might overpay eth miner in order to make the deal, so I sent email asking them, they answered: 


Hello,
Here is output hash:
https://etherscan.io/tx/0x1e3365201ccc5d257a5c75923780d77d93d4640a348b377fd47c5a23e9565a90

Best Regards,
Julija



According to that reply, they have no problem in the transaction, they gas fee was 0.01 usd. 



Next step is the clarify Metamask wallet, but that's just a wallet to hold my private key. But I still sent email to ask, their response was quite promp, they asked me to download a log from metamask setting, then I got the answer: 



![image.png](https://images.hive.blog/DQmbsU1FscGhKhmFp1kukTfRB2MAphjSrfqjEbjayetCFXX/image.png)



This clearly shows that my account was hacked. Somebody compromised my eth account then set up a regular transfer system. No wonders there are always output transactions in my account in etherscan!!! It looks this account was hacked long time ago!!

https://etherscan.io/txs?a=0x627306090abab3a6e1400e9345bc60c78a8bef57


This ‘0x627306090abab3a6e1400e9345bc60c78a8bef57’ is my ethereum address and I won't use it anymore.



The lession here is to check your wallet address in etherscan before you receive payments. If it looks like many output payments which were not your action, your account is most likely compromised and you shouldn't use that account any more. 


Related topics:


- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)
