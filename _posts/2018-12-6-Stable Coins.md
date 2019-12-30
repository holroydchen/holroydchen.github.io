---
layout:     post
title:      Stable Coins
subtitle:   
date:       2018-12-6
author:     Howard
header-img: img/post_blockchain.jpg
catalog: true
tags:
    - blockchain
    - cryptocurrency
---

I did research on lots of stable coins recently. They can be categorized into three groups: 

1. backed by fiat USD, regulated by escrow or government, e.g. USDT, GUSD, USDC,PAX, TUSD;
2. decentralized token backed by another cryptocurrency assets as collateral such as bitUSD and Dai;
3. no collateral, no USD backed, but dependent on algorithm, such as BASIS.

I didn't do much research on the third group, since it depends on how many people can support it.  Most of all, my understanding is a stable coin must have something tangible to support it.   Now I figure out those popular stable coins in the market.  I realize that most of them are ERC20 tokens in Ethereum, which might due to its excellent ecosystem, but with EOS communities become more mature, more and more stable coins will be established based on EOS smart contract.





**USDT:**  This might be the earliest and most popular stable coin right now. It was issued by Tetter, which is owned by Bitfinex, a famous America crypto exchange.  It claimed that it stores one USD in bank after issuing one USDT, thus it is 1:1 backed by USD.  However, recently after being audited by US regulator, it said the USDT issued was supported by 70% of equivalent USD fiat, anyway, that should be enough considering traditional banks reserve capital if they were telling the truth.  There are two types of USDT we should be aware, one is based on Omni Layer which is the same blockchain running Bitcoin, whose address begins with '1'; anther is ERC20 token based on Ethereum and its address begins with '0x'.



**USDC:**  This is issued by Circle, a starup under Gold Sache, and invested by Bitmain, an ERC20 token.



**TUSD:**  or True USD, issued by some company in USA, but the same mechanism as USDT and USDC, escrowed and not audited or regulated by government, claim 1:1 pegged to USD, an ERC20 token.



**GUSD and PAX:**  There two are ERC20 tokens approved by US government and audited and regulated by US government to ensure 1:1 backed by US dollars!  Yes, centralized, but I prefer them as more reliable for now, an ERC20 token.





**bitUSD:**  a decentralized stable coin,  pegged to 1 USD in bitShare system, which was created mostly by Daniel Larimer (Byte Master).  In order to get bitUSD, you have to collateral your BTS in the system and bitUSD is generated.  When the price of the BTS dropped down in the market, you have to collateral more BTS to hold your position, otherwise, the system will sell out your BTS, which accelerate the slump of BTS price in the market.  If the bitUSD goes above one USD in the market, people would rather sell them to get more BTS or rather collateral BTS to get more bitUSD.  If the price of bitUSD goes down below one USD, bitUSD holders can settle their bitUSD at any time for one USD!  





**Dai:**  Use ETH as a collateral and the makeDAO system called CDP, a smart contract,  will generate Dai, almost similar to  bitUSD, but have some difference.  When the price of Dai goes below one USD in the market,  this encourage people to buy in Dai from the market to pay back their debt to CDP. If the Dai market price goes above one USD, people is more likely to deposit collateral to CDP to get Dai rather than purchase from the market.  Dai holders do not have the right to force settle collateral at any time as bitUSD holders do, which I take a pros.  If the ETH price in the market dropped down,, people need to deposit more ETH to hold their CDPs ( currently 150: 100), otherwise, the system will auction their ETH ( strictly speaking PETH) to keepers ( MKR holders, a token issued by makeDAO) with 3% discount. A cons of Dai compared with bitUSD is when you pay back your CDPs, you need to pay stable fee ( above 10% of your Dai ) or liquidation fee if CDP system need to produce more PETH to support the value of Dai.  Something confuses me is I think PETH is somehow redundant,  maybe it is a temporary solution to make it easier to implement the system. 



**SBD:** or Steem Dollar, which I assume the worst stable coin, it looks more like a greedy indicator. This is something from the white paper:

> Steem Dollars are created by a mechanism similar to convertible notes, The terms of the convertible note allow the holder to convert to the backing token with a minimum notice at the fair market price of the token.

SBD to steem is a  debt-to-ownership and the steem system automatically balance their ratio by conversion each other.  Also the system claims to have reliable price feed and adjust interest to SBD holders to maintain the 1:1 pegged relationship with USD. However, the history proved this is not working at all. Anyway the SBD is a reliable indicator of bullish or bearish of crypto market.