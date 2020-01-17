---
layout:     post
title:      Implement Smart Contract to replace OTC market
subtitle:   
date:       2020-1-9
author:     Howard Chen
header-img: img/post_smart_contract.jpg
catalog: true
tags:
    - blockchain
---

Diving into the blockchain technology for a long time, in my opinion, the most attractive and powerful aspect of the blockchain is the smart contract which can overthrow traditional centralized system.  I always imagine smart contract as a trustless and reliable agent which can be a substitute of most agents in the real world.  I once had a picture in my mind that we can use smart contract as an intermediate to exchange cryptocurrencies among buyers and sellers, which is something like Paypal and Alipay. In my mind, a purchaser sends out an order to buy some cryptocurrencies, this order will be taken by some sellers. The purchasers's stable coins will be deposited into the smart contract and they will be released to the sellers when purchaser confirms cryptocurrencies to buy have been received.  In case a person wants to sell cryptocurrencies, he/she sends out an sell order. When a buyer want to take this order, his/her stable coins will be deposited to the smart contract. After the buyer confirms she/he has received the amount of cryptocurrencies, the stable coins will be released to the seller's eth account.




This was such an interesting system that I feel so obsessed so I tried to implement. I designed, developed, debugged and tested this system and put to [my personal github](https://github.com/chenlocus/decentralize_centralized_exchanges).  With time lapse, I almost forgot it so I prfer to replicate all the process in a whole new computer and record this funny procedure to share with people who have the same kink in this area.  I take this as a similiar process likewise people in youtube teach how to [DIY fence](http://livinginau.life/2020/01/06/%E7%BB%88%E4%BA%8E%E9%80%A0%E5%A5%BD%E4%BA%86fence/) or cook. 





In order to save money, Ｉplayed this in testnet. I needed to deploy two smart contracts to the testnet, one is for agent contract which acts as a escrow, another is a stable coin contract.  I don't like develop all wheels from scratch and like to find existing one which is more mature and reliable. [openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts) has existing smart contract codes for stable coins which have been widely used, tested and reliable.  I imported the ERC20 token code which is the contract standard for most main stream stable coins runnning on Ethereum such as USDT, USDC, DAI. It defines the token name, token code, decimal (because EVM doesn't support float calculation, so the contract needs to deal with this), token transfer standard, how to approve other accounts to use how much of the tokens, etc. I put this mimic stable coin contract [here](https://github.com/chenlocus/usdc_mock/blob/master/contracts/Stabletoken.sol), something imperfect here is I set decimal to 18 which is over-accurate. Actually 6 decimals are enough for most stable coin contracts. [Here](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7#readContract) we can see the USDT contract in Ethereum.  I feel sorry for myself of being over engineering. I like two kinds of stable coins, one is backed by traditional bank, such as USDC, another is somehow decentralized such as DAI in makeDAO because they are either regulated or dependent on blockchain. 




As for the agent contract, I have to build it from scratch since I cannot find one which meet my need. I even had a dream about how this system is working. Most important of all, I met a cheater over Telegram who claimed himself as Daniel Larimer and gave me great encouragement on this system. So I really wanted to make it out.  I imported IERC20.sol, which is the interface contract of ERC20. I used this since I want all stable coins based on ERC20 can be used in this system. In addition, I imported Ownable.sol since I want to destroy the contract if it proves to be useless so that it won't waste blockchain resources.  On reflection, this is a fatal weakness of almost all DAPPs which are claimed to be 'decentralized' but actually their owners can do almost everything. 





The key part of this agent contract is to manipulate the stable coin contract. In order to implement this, we need to set the stable coin contract address as one of the args. When a buyer sends a buy order to the agent contract, it is needed to call the 'approve' function of the stable coin contract, so that the agent contract can be authenrized to call the stable coin contract's transfer function to send stable coin to itself for deposit and transfer coin out on settlement. 




Buyers need to call the function 'buyOrderSent' in the agent contract，a certain amount of stable coins will be deposited in the contract, meanwhile it is needed to take down buyers' deposit information in `_deposit[msg.sender]` in the contract code, otherwise, this contract is easy to be hacked and money gets lost. I will discuss about ways how to hack a contrac and how to prevent it. 



After the buyer confirms he or she has received the cryptocurrency, 'buyOrderConfirmed' will be called so that the agent contract can transfer stable coins to the sellers. Meanwhile the variable `_deposit[msg.sender]` will be updated. BTW, someone said USDT is free to use, but actuallly not, it can charge you a little bit in the contract. It is the same mechanism in the sellers' orders treatment. You will feel I am too annoying if I repeat it. 



I have completed those headache theories, now we are going to do it step by step. We need to start from installations from scratch (start with a computer with only OS, mine is windows ) in order to compile, deploy and verify this smart contract. 




Step 1: we need to install [nodejs](https://nodejs.org/en/)，since all the compilation, debug and deployment, even test depend on [Truffle Framework](https://www.trufflesuite.com/docs)，and the Truffle Framework relies on nodejs.



Step 2: install truffle framework, npm install -g truffle.


Step 3: install [ganache](https://www.trufflesuite.com/ganache)，which is a simulator of Ethereum blockchain. After installation，it will allocate 10 accounts with enough eth for you to play with. You can also deploy to EtH mainnet of testnet via MetaMask，but the mainnet is slow and cost you money and the testnet gives you too little eth to play. Then press “quick start”，and you will be given 10 accounts with 100 eth in each. 



Off course, you can select not to use ganache, Truffle framework has a native Ethereum mock called 'Truffle Develop'.



Step 4: install openzeppelin， it has changed somehow especially to windows. I didn't come across this several months ago. Now you need to go to [github的openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts)，download and unzip openzeppelin-solidity， then you need to create a fold called 'node_modules' and put the unzipped openzeppelin there, then add the fold's directory to windows path environment variables.



Step 5: compile these two smart contracts, go to the root of both stable coin contract and agent contract, then execute:

​    `truffle compile`

This is to convert .sol file to byte code and ABI (Application Binary Interface), the version of the compiler can be configurable in truffle-config.js.


After compilation, we need to deploy the contract to a blockchain which is determinied by truffle-config.js, I deployed to ganache.


For the sake of visualization, we can go to ganache and set truffle-config.js of both contracts to its workspace: 
![](https://cdn.steemitimages.com/DQmckCpSZnwbJhXRe12L4iGUvwVYjBr3mjm6L8VzBXLYk3s/image.png)


run this command to deploy:

`truffle migrate`





Take note of 'contract address' of stable coin contract after deployment, we need to use it afterwards. It is '0x0018204bBFf3A1477a79023757B0175D5ad8f4A5' for this stable coin contract in ganache.

![](https://cdn.steemitimages.com/DQmQdsG9ZJhx26zJF3c6mLA734u4dUwn9e5Bkbwxz2toVru/image.png)


We can see the stable coin contract has been successfully deployed in ganache:
![](https://cdn.steemitimages.com/DQmcGHVR9tnnJ4Emri37btqaJ2uC3V8KcGsU7tBA1StGu2o/image.png)



Step 5: I was wondering how to validate this agent contract. It will be troublesome to write a UI and I am not good at UI. I was thinking of ask one of my friends to do this for me but he is too busy. So I have to do it myself. Fortunately, Truffle has a test framework similar to Mocha. I would use this framework to test my contract.



Test is very important to the software development process, to guarantee the quality. The idea of test goes throught all the SDLC ( Software Development Lifecycle), which is the core difference between traditional waterfall and nowadays agile, also the key to distinguish the role of test engineer and quality assurance engineer. When I was developing this contract, I was thinking how to test it as clients, we need to 'put myself in your shoes', or 'compassion'. 


I designed three ethereum accounts, one is for sending orders, another two are for taking orders. In addition, we need to consider carefully how to hack this contract if we were a hacker. I will talk about this in another post. One of the most important thing in public blockchain is how to prevent being hacked especially your contract is about money.



The testing process is rather simple compared with writing the script, amending two places about the stable coin contract addresses in the test script like this: 

var USDC_ADDRESS = '0x0018204bBFf3A1477a79023757B0175D5ad8f4A5';


Then run:

`truffle test`

![](https://cdn.steemitimages.com/DQmPCeWY2WoNSxcda8G7LKYHhFvuUAEUR5g1Bk71DWKXvJ3/image.png)


The test cases passed. It looks simple, right? But it wasn't so as I debugged during the test process. Truffle framework provides very good debug tool, the only annoying thing is to find a suitable transaction hash, so it is better to set a breakpoint, so you won't be dizzy with too many transactions.



Related topics:


- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)





