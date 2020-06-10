---
layout:     post
title:      Decentralized Alipay or Paypal
subtitle:   Idea
date:       2020-6-10
author:     土猪
header-img: img/post_smart_contract.jpg
catalog: true
tags:
    - blockchain
    - smartcontract
---



I made a smart contract on the test network of Ethereum to replace the current OTC market last year. People who need cryptocurrency send a buy order, and meanwhile, stable coins as USDT and DAI will be deposited into the contract to be locked. Then sellers on the market can pick up the order and transfer the cryptocurrency to the buyer's wallet. After the buyer confirms, the smart contract will be notified to send the corresponding amount of stable currency to the seller's wallet. Vice versa for sell orders.  The excerpt is quite simple, for the detailed process please see [this post](https://hive.blog/blockchain/@chenlocus/implement-smart-contract-to-replace-otc-market). It seems that this can be adapted to the role of Alipay or paypal with a slight modification, but things are not so simple, as I said the soul of the blockchain system is community that support the specific blockchain. A smart contract that simply acts as an intermediary for buy and sell would never attract people to use without the soul. It does not solve the most important function of Alipay or paypal ----- the handling of disputes between buyers and sellers. 







![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Alipay_logo.svg/1200px-Alipay_logo.svg.png)





I have been exploring how to implement such a decentralized Alipay or Paypal. First of all, I always presume such cryptocurrencies as Bitcoin, Ethereum, EOS or Hive, steem are not suitable for routine payment functions, the reason is quite simple, that is, their market prices are too volatile, and only stable coins such as USDT, USDC, DAI can be fit for the job. The smart contract for decentralized Alipay must be able to accept all kinds of stability based on Ethereum.  Technically,  this can be done after a little bit modification of my code; secondly, it must be able to attract a community to do arbitration. This is a problem that I have always got a headache, since this cannot be simply solved with a smart contract.  In order to figure out  a slightly reliable solution, let's go through the specific process of Alipay.

![image.png](https://images.hive.blog/DQmbWdcwf51bCLsLESYoEXoiAvsNR8GYMRNm1dndDycMwWZ/image.png)





Alipay is a by-product of Taobao, the most famous C2C platform in China. If  there was no Alipay then no one would dare to use Taobao. Alipay acts as a payment intermediate between  sellers and purchasers. When a person buys a product from Taobao, she deposited the money to Alipay and the money will be locked there for a period of time. If there is no dispute, the money will be automatically transferred from Alipay to the seller's account (can be Alipay or bank account). Since some products have a long delivery cycle, the time money locked in Alipay can be negotiated between the seller and the buyer, thus if the product delivery time is delayed, buyer can apply to extend the payment time, but once the money reaches the seller's account, whether it is an Alipay account or a bank account, the buyer cannot redeem it. If there is a dispute about the product, such as the buyer did not receive the product purchased within the specified time, or the product has quality issues, the buyer needs to communicate with the seller firstly. If the communication doesn't work, then the buyer needs to provide proof of payment and the product description it to Taobao. 



Taobao, as a C2C platform like ebay, will assign the dispute to one of its employees, we call them 'waiter', the waiter will act as an arbitrator, and with sufficient evidence, the waiter can refund the buyer. This is vice versa for sellers. After the goods have apparently delivered with good quality, if the buyer refuses to admit it and negotiates with the buyer proves to be  in vain. Then the seller needs to provide enough proof for the delivery to the waiter before Alipay’s money can be transferred to the seller’s account. The reason why Alipay can provides a refund service with shopping in Taobao because it is a product of Taobao, but if you use Alipay to buy things on other platforms, such as buying bitcoins on the OTC platform (over-the-counter trading), unfortunately, even if you have been cheated, there is no place to complain, except taking legal actions. But I doubt mainland China may not think that it is  legal to trade Bitcoins.  As Alipay is used more and more, it gradually becomes a payment method instead of intermediary function.  





Alipay account is an account in the Taobao system, and does not necessarily have to be linked to your bank account, so many sellers on the OTC platform would rather use Alipay account to receive money rather than bank account. They would rather be charged by Alipay, since once they are found trading cryptocurrencies, only Alipay account will be  frozen, and his bank account will be safe because there is no link.  Since Alipay provides this intermediary function, of course, there is a fee, but only the sellers are charged, and sellers will be  charged when the money is transferred to the their account. 





Paypal is a payment platform backed by ebay, so only on the ebay platform, it has a refund functionality. This is the same as Taobao’s Alipay. Its workflow is similar to Alipay. As it is widely used, it is also changed to  a pure payment method, instead of a payment intermediary. When I am shopping online out of China, Paypal is always my first choice since it is more safe than bank card. I used to be naively assuming  I can get my money back with Paypal on other shopping platforms. My kid accidentally bought a game in Apple's APP Store with my Paypal, and was charged monthly.  I realized it after six months, so I went to Paypal to complain, saying that this is not my authorized payment. However, this is useless, Paypal asked me to complain to Apple store. I requested  to cancel the regular payment. Paypal  said it cannot. I had to change the password of my account. Then the app on Apple sent me several emails saying payment failure. It can be seen that Paypal can only play an intermediary function on the eBay platform. The regular payment is an agreement between the buyer and the seller. The seller regularly transfers the buyer's money to his account through the interface provided by Paypal. Paypal is also free for buyers and charges for sellers. 



![](https://www.rahs.org.au/wp-content/uploads/2017/08/PayPal.jpg)





In the world of decentralization, when people buy or sell products or trade digital currencies, they need a reliable payment intermediary. A decentralized payment intermediary must provide the function of handling disputes between sellers and buyers. It takes humans to play the role of arbitrators, and Alipay can only play an intermediary role on the Taobao platform, because it has waiters in Taobao who receives salaries to handle it. If this decentralized payment system is applied to a centralized platform, such as a shopping website like Taobao, the website can of course designate some roles similar to Taobao waiters to handle the disputes, so this decentralized payment system also needs to provide an important interface: **appoint an arbitrator to handle disputes**. Even this seemingly simple interface takes many considerations, e.g.  who is qualified to appoint an arbitrator? How to reward the arbitrator? There are two ways for the shopping platform to access this decentralized payment system. One is to fork the smart contract and do some modifications, such as adding "`modifier onlyOwner()`" to restrict the qualification of the contract owner, only he has the right to appoint an arbitrator. There is another situation that should account for the majority. The shopping platform connects to existing smart contracts. That is to say, this smart contract needs to serve various shopping websites, whether it is a centralized or decentralized shopping platform.

![image.png](https://images.hive.blog/DQmWHzRSa37YEtbzeGBkxedH1K2MwoWciQEY93RGpV2Ao8j/image.png)





For a smart contract that provides decentralized Alipay services for multiple shopping platforms, there are two scenarios to consider. One is that the shopping platform is a third-party platform like Taobao. If a dispute occurs, buyers or sellers can submit the platform to resolve it. Decentralized Alipay needs to provide an interface for the arbitrator to refund the buyer, as well as an interface to transfer the money to the seller. This situation is basically similar to the fork contract of the previous shopping platform and is easy to handle.



![image.png](https://images.hive.blog/DQmQrmkrKwVEoho642NycncAfiYcqcZZwK4rm5Dox4BF3Z5/image.png)



Another scenario is more complicated, which needs to widely support the trading between strangers in a decentralized world.  For example, the shopping platform is a website built by the seller, or something like  **OpenBazaar**  which claimed to be a decentralized Taobao system. These sorts of shopping platform are unable to provide a arbitrator to mediate disputes.  In this situation, we needed economic stimulus and punishment mechanisms to solve this problem. In the cryptocurrency world, are there many ways to solve this problem.  Because it is "decentralized",  we need to count in the evil nature of human being, no one will take the initiative to be the arbitrator. Benefit is necessary to attract people to take the role and punishment is also a must to stop people from being corrupted . These requirements reminds me of ETH 2.0 reward and punishment mechanism for POS deposit.



![image.png](https://images.hive.blog/DQmccKdqkjrduRmzgAo845cR4bQJbv591pG13m3JMExi3rr/image.png)



Assuming that the decentralized Alipay system has a token, when someone in the community see a dispute, he or she can take initiatives to apply for an arbitrator, or they are just passively selected as an arbitrator, which is acknowledged by both the buyer and seller. The arbitrator needs to hold token, depositing the value of the equivalent dispute in the decentralized payment system for a period of time (this "a period of time" is a problem in the Ethereum system, the default is not to support the message of timeout, but in EOS This is supported), this approach is mainly to prevent collusion between the arbitrator and the seller or buyer. The deposited token will be returned to the arbitrator a few days after the dispute is resolved, and an additional token will be issued to the arbitrator as a reward. If the buyer or seller strongly opposes it, the community will be required to vote on the case, or even use secular laws to resolve it. If the arbitrator proves to be cheating, all the tokens he/she mortgaged will be confiscated by the system. If the arbitrator is proven to be Misjudged, then the mortgaged token may be partially confiscated.

<img src="https://images.hive.blog/DQmb1v7raoTALE4oa5cooJDcf7UZ7BRBTzRHoAty37QZugw/image.png" alt="image.png" style="zoom:150%;" />



The basic value of this token is that you can share the revenue generated by this system. It should be known that Alipay system or Paypal charges sellers and is free to buyers, so of course this decentralized Alipay will do the same. Moreover, we must know that many large companies rely on the profit of a product to feed a bunch of employees, including ceo, cto, cfo, various middle-level and ordinary employees, as well as dividends to shareholders, the rest are then corrupted or wasted. Even one product can feed other departments which don't make money.  In the contrast,  this decentralized Alipay system can make the charges very low. The fees collected only need to be shared with all token holders, eliminating various unnecessary loss.

<img src="https://images.hive.blog/DQmV7HtwMPQo9qRoyDjpdEWQhBVnXVti74ynehtaenNyydx/image.png" alt="image.png" style="zoom:150%;" />

The community is the soul of the blockchain system. It is composed of all the people who hold the token of this decentralized payment system. The rights and obligations of all the holders are complementary. Many systems are like this, such as the famous one on Ethereum. defi system MakerDAO. In addition to the obligation to go to arbitration and to vote on the results of the arbitration, token holders also need to vote on various parameters of the system, such as the percentage of fees charged on sellers.

<img src="https://images.hive.blog/DQmcqFu3ihPQhqGFNoHb5xapKSgB2FReovMXjspQUBMBQsq/image.png" alt="image.png" style="zoom:200%;" />



In addition, I think the arbitration process should be handled off-chain, and the transfer of funds and the collateral of tokens, rewards, and punishments are handled on-chain. The smart contract should provide clear and enough interfaces as well as guarantee fund security, so that it does not depend on any DAPP.



I hope this article can attract more insightful people to participate in the discussion or to achieve it together. In the decentralized world of blockchain, I believe that the power of the community is the most important. A dream, as long as there are a bunch of people discussing, can become true out of these discussion and efforts.

![image.png](https://images.hive.blog/DQmYsWCn5HYougoJnXbW31b2utg6Y91MwwVWqRmzQpagRAN/image.png)








- Related topics:
  - [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)
  - [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)
  - [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)
  - [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)
  - [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)




