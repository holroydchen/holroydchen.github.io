---
layout:     post
title:      Using smart contract to kick off OTC platform
subtitle:   
date:       2018-12-30
author:     Howard
header-img: img/post_blockchain.jpg
catalog: true
tags:
    - blockchain
    - cryptocurrency
---

There are some OTC cryptocurrency trading platform,  OTCBTC, local coin,  they have the same in common, what is the centralized platform acts as a escrow,  when you want to buy some bitcoins,  you need to place an advertisement, then somebody see your ads, they will take the order and deposit amount of bitcoin to the platform.  After the taker receives fiat  from the buyer and once this is confirmed by the taker, or the time expires, the platform will automatically release bitcoin or get instruction from the taker to release bitcoin to the buyer.



There are several problems in this system,  a fatal problem is whether the platform is worth trusting ?  How to guarantee that the  founder of the platform would not withdraw all your coins and run away? Even if the founders won't do it, their 
employees probably can do this.  Somebody logon on my personal account with password,  fortunately I have set up two step authentication, but this still makes me scary.   It is somehow like a sward over your head.  


Another problem is what about they fail the business, which means all your lose all your money since all your personal information and account are only located in their systems. 



The third problem I am concerned is whenever there is a dispute,  the platform would act as a arbitrator.  I suspect they have so much time to deal with that.  




From my experience,  the usage of OTC is for people to buy or sell cryptocurrency with their own fiat which current crpto exchanges cannot provide enough liquidity.  How about they buy or sell some stable coins such as USDT, USDC then to trade in those coin to coin exchanges such as Binance which has a much higher trading volume. 



With this assumption, the   centralized OTC platform should be substituted by a total blockchain solution.  The  escrow function can be totally replaced by a smart contract,   we need to make it as simple as possible and  thoroughly  audit the contract, even use some audit tools to check making sure it is safe and people can not steal money away.    With this contract,  people can exchange their stable coins with fiat currencies in different countries.   



Existing ways of change USDT or USDC to real USD take lots of time and fees, in addition, it is so annoying with the process and limitation.   With this system, people can get their USDT, USDC, or USD with a small number of fees and instantly.  It works in this way:   people publish their orders to get USDT, USDC or get fiat.  These orders can be taken by people who in demand of fiat or stable coins.    




People who want to exchange for some stable coins can place an order for e.g. 200 to 10000 USDT,    this order is visible to all participants, then if somebody has some USDT and want to change to fiat, they can take this order and contact you via instant chat online,  their USDT will be deposited to the contract, after  it is confirmed they have received payment, their USDT will be released to people who place the order.   



If someone has some USDC and they want to exchange for fiat to spend their life. They can place an order so that everyone can see.   The USDC won't go to contract until someone takes this order.  After the one placing order receives payment via bank debit, paypal, wepay, alipay, or whatever, with the confirmation, the USDC in contract will be released to people who takes the order. All their conversation on line can be kept as evidence of payment for further dispute.



How about somebody is dishonesty?   We need a system something like MKR in MakeDao system, which means we need a group of people to act as arbitrators.  People who act as arbitrators should be rewarded.  We need evidence to support people who issue a complaint.  So the conversation between buyer and seller,  together with transaction receipt provided will be uploaded to a blockchain.  Thinking of how expensive it would be to store data in public chain, it should be a good idea to establish a private chain to store those data.  



People who own stable coins should deposit more than  what is necessary to the contract, e.g. 20%  more, so that once they are found cheat, the extra deposit will be deprived as a penalty.    After each trade, people will give reviews each other,  so people's reputation is very important, which is visible to every one and stored in blockchain. 



Since there are more than USD is supported, people will publish their order in different fiats,  which means they would sometimes over value or under value their stable coins.  But it is your freedom to trade them or not.  




I think people should get efficient and effective, instant chat before they decide which way to trade each other, thus I prefer TAOBAO mode in China instead of ebay mode.   If we use third party chat app, such as wechat, whatapp, or telegram, that would impair people's privacy, so I prefer system itself should provide instant chat between people and these conversations should be strore in block chain as further evidence for dispute.




The most problem I concern is the security and safety of fund.  I once thought we should use the mode what DDEX ( a decentralized exchange dapp over Ethereum ).  In DDEX, clients use private wallet to sign their orders,  the signature and public key are transferred to the back end. It is the back end who interact with the smart contract over Ethereum using these information.   This framework might due to the slow speed of Ethereum, I don't think it is actually a decentralized system.   As far as I am aware,  the back end should do the least thing to make it a real decentralized system, otherwise,  this system can be implemented by a centralized server.  




Apart from above,  the deployed smart contract should be audited in public to guarantee there is no code to make the withdraw of fund by the owner or hacked illegally.