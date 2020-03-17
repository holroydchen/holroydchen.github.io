---
layout:     post
title:      Programmatic Trading on dYdX
subtitle:   
date:       2020-2-2
author:     Howard
header-img: img/post_blockchain.jpg
catalog: false
tags:
    - blockchain
    - cryptocurrency
    - DeFi
---


After introduced by one of my colleagues to this website [https://defipulse.com/income](https://defipulse.com/income) to win money by lease ETH, I digged into why people would like to pay such a high rental. Then I got this article which enlightened me. 



Programmatic trading on decentralized exchanges has historically been complicated and different than what traders are used to on traditional exchanges. At dYdX we’ve made the DEX programmatic trading experience simple and familiar through our easy-to-use clients and trading API. Read on to learn how to build a trading bot on dYdX!



# Trading on dYdX

First we’ll start with a brief overview of how trading on dYdX works, before getting into how to trade programmatically. I’d also encourage you to check out our [product](https://trade.dydx.exchange/), and [help docs](https://help.dydx.exchange/) to get a better sense of how everything works as well.

## Margin Trading

dYdX natively supports margin trading, meaning you can seamlessly borrow assets while trading. Borrows are represented by negative balances on dYdX, i.e. if you are borrowing 100 ETH your ETH balance would be -100. You can always borrow on dYdX provided you have sufficient collateralization (minimum 125%).

Borrowing automatically happens while trading. For example if you start with 200 USDC & 0 ETH in your dYdX account, you could sell 1 ETH for say 150 USDC. When the trade executes you’ll automatically borrow the 1 ETH to sell. After the trade your balances would be 350 USDC & -1 ETH.

## Interest

On dYdX all funds continuously earn interest, and all borrows continuously pay interest. The borrow and supply interest rates are variable, and change based on supply and demand. You can view historical interest rates on [LoanScan](https://loanscan.io/earn/historical).

Interest is continuously reflected in your balances, meaning your balances will constantly be increasing just by keeping funds on the platform.

## Instant Non-Custodial Trading

Trading on dYdX is non-custodial, meaning you remain in full control of your funds at all times. Orders are cryptographically signed by your Ethereum account, and are executed through our smart contracts.

When two orders cross, our matching engine sends a transaction to execute the trade. The trade can be considered effectively final the moment it is sent, meaning you don’t have to wait for block confirmations (or pay gas) to determine the status of your trade.

## Bonus: Participate in Liquidations

Once you have funds in dYdX, you can easily participate in liquidations of undercollateralized dYdX accounts and earn a liquidation fee. Liquidators on dYdX have earned over $1M in the past few months! It’s easy to get started with our [open source liquidator bot](https://github.com/dydxprotocol/liquidator).

# Building a Trading Bot

We’ll be going through an example of how to build a bot that trades on dYdX. We’ll build the bot using dYdX’s [Python client](https://docs.dydx.exchange/#/python), but dYdX also has a [TypeScript client](https://docs.dydx.exchange/#/typescript), [HTTP API](https://docs.dydx.exchange/#/api), and [WebSocket API](https://docs.dydx.exchange/#/websocket).

First, let’s install the dYdX Python client:

```
pip install dydx-python
```

To trade on dYdX you’ll need an Ethereum account, and its private key to sign transactions and messages. You can create an Ethereum account with any wallet that supports exporting its private key.

Now that you have your Ethereum account let’s use it to deposit some funds into your dYdX account. You’ll need to have the funds to deposit in your Ethereum account, as well as a bit of ETH to pay for gas.



On the my_balances variable, you’ll notice that your balances are organized by market ID. Each asset on dYdX has a specific ID: ETH = 0, USDC = 2, DAI = 3. Each balance has two parts: par and wei. wei is the one that represents your actual balance.

Now you’ve deposited funds into your dYdX account, let’s place your first trade! Remember, on dYdX you don’t actually need to have the funds you’re trading away — you’ll automatically borrow them provided you have enough collateral in your account. To illustrate this, let’s buy 10 more ETH for 2000 DAI (more than the 100 DAI you had deposited):


That’s it! Your order will automatically execute if it crosses an existing order on the orderbook, otherwise your will be placed on the orderbook and will wait to be filled by other takers.

After this trade, your dYdX balances are: 20 ETH, -1900 DAI. You’re now leveraged long ETH by borrowing DAI!



[Link](https://medium.com/dydxderivatives/programatic-trading-on-dydx-4c74b8e86d88) to the original article.



Related topics:


- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)

- [Lending and Borrowing in Crypto Market](http://engineerman.club/2020/02/02/NFT-Valuation/)