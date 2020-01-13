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




Buyers need to call the function 'buyOrderSent' in the agent contract，a certain amount of stable coins will be deposited in the contract, meanwhile it is needed to take down buyers' deposit information in `_deposit[msg.sender]` in the contract code, otherwise, 这个合约很容易被别人一分钱不花就黑掉，这个我将在下文介绍如何黑它的几个途径，我又如何防范。 当买单被确认收到货物（或数字货币）后，'buyOrderConfirmed'被调用，中介合约把钱转给卖家，同时更新_deposit变量，题外话一下，很多人说usdt是免费的，其实不然，它会偷偷给你收费的。 关于卖单处理，也是大同小异，再说就嫌烦了，比如我们部分有个人，我就不敢问他问题，他说起来滔滔不绝，最低消费半小时，听到我想吐，是真的想吐，于是理解了‘大话西游’里唐僧的感受。 





有些费脑筋的原理部分介绍完了，简单不？ 接下来就落入俗套的分步进行式了。 要编译，部署和测试这个智能合约，我们从一个仅带操作系统的机器开始安装。




第一步，要安装[nodejs](https://nodejs.org/en/)，因为整个编译，调试和部署，甚至测试平台基于[Truffle框架](https://www.trufflesuite.com/docs)，而truffle框架安装需要nodejs；



第二步，安装truffle框架，npm install -g truffle；



第三步，安装[ganache](https://www.trufflesuite.com/ganache)，这就是一个以太坊区块链模拟器，安装后，上面会自动给你分配十个账号，有足够多钱供你玩，当然，你也可以通过MetaMask发布到以太坊主网或者测试网去，那不是速度慢吗，主网不是要烧钱吗？测试网给的银子也少。 按下“quick start”，一键到位，它会给你创建10个账号，每个账号100个以太坊，够你玩的了吧。



当然，你也可以不安装ganache，Truffle框架自带了一个叫做’Truffle Develop‘的以太坊区块链模拟器。






第四步，安装openzeppelin模块， 这个有些讲究，特别在windows系统，几个月前是不需要如此操心的，现在不同了，具体如下，到[github的openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts)上去，下载并解压openzeppelin-solidity， 然后新建一个叫做'node_modules'的目录，把这个目录名放到windows的path环境变量里去；





第五步，编译和部署两个智能合约，分别到稳定币合约和中介合约的根目录下，执行： truffle compile 的编译过程，这是把.sol的文件转化成字节码和生成ABI(Application Binary Interface)的工具，这个编译器的版本可以在truffle-config.js中配置。 



编译之后就是部署(deploy)智能合约到区块链上，具体部署到哪条链上，这个是由truffle-config.js配置，我是部署到ganache上去。


到ganache上把两个合约配置文件都放到workspace中，这样看起来更直观：
![](https://cdn.steemitimages.com/DQmckCpSZnwbJhXRe12L4iGUvwVYjBr3mjm6L8VzBXLYk3s/image.png)


分别运行每个合约的 truffle migrate 就可以了。记住稳定币的'contract address' 是'0x0018204bBFf3A1477a79023757B0175D5ad8f4A5'，这个在接下来的测试时候需要用到。

![](https://cdn.steemitimages.com/DQmQdsG9ZJhx26zJF3c6mLA734u4dUwn9e5Bkbwxz2toVru/image.png)


在模拟区块链上看到已经部署了稳定币了。
![](https://cdn.steemitimages.com/DQmcGHVR9tnnJ4Emri37btqaJ2uC3V8KcGsU7tBA1StGu2o/image.png)




第五步，怎么证明这个合约好使呢，写个界面来证实它？ 那多麻烦啊，写界面可不是我的擅长，我本来还想找我一个同事帮着写，可惜他最近太忙了，我们就要谈谈最


尽管如此，我还是要谈谈测试的事情，其实测试是非常重要的东西，测试的思想贯穿于整个开发过程中，这就是传统瀑布式开发和现在流行的agile模式的本质区别，也是test engineer 和Quality Assurance Engineer的本质区别。 在做这个智能合约的时候，就要想到以后应该如何测试，用户会如何使用，我觉得有个说法很有道理'put myself in your shoes'，或者叫'同理心'。 



测试设计了三个以太账户，一个账户发出买单或者卖单，另外两个用户去take orders，并且把数字货币（或者实物）给发出订单的用户并且得到确认。 然后在设计的时候，需要认真考虑到如何hack这个合约。 我想另外发一篇文章来结合这个项目谈谈我的看法。 公链上智能合约的一个最大问题就是如何防止被黑。 

测试文件写好后，测试过程很简单， 把'TestAgent'文件里买卖两个地方的稳定币地址改掉：
var USDC_ADDRESS = '0x0018204bBFf3A1477a79023757B0175D5ad8f4A5';


然后运行测试： truffle test
![](https://cdn.steemitimages.com/DQmPCeWY2WoNSxcda8G7LKYHhFvuUAEUR5g1Bk71DWKXvJ3/image.png)


我们可以看到测试通过。 其实在做的时候并没有这么简单，测试过程需要跟调试过程反复进行，truffle framework提供非常好的调试工具，调试最大的麻烦在于transaction hash的寻找，所以最好设个断点，这样不会产生太多transaction让人头晕目眩。 





更多区块链文章：

- [智能合约代替OTC市场](http://livinginau.life/2019/12/10/%E6%99%BA%E8%83%BD%E5%90%88%E7%BA%A6%E4%BB%A3%E6%9B%BFotc%E5%B8%82%E5%9C%BA/)

- 
  [makeDAO 的 PETH](http://livinginau.life/2019/11/16/makeDAO_peth/)


- 
  [对比特比共识机制的一些看法（my opinions on the consensus mechanism of Bitcoin )](http://livinginau.life/2019/03/05/%E5%AF%B9%E6%AF%94%E7%89%B9%E6%AF%94%E5%85%B1%E8%AF%86%E6%9C%BA%E5%88%B6%E7%9A%84%E4%B8%80%E4%BA%9B%E7%9C%8B%E6%B3%95/)

- 
  [怎么样才能当上steem的矿工](http://livinginau.life/2018/10/20/%E6%80%8E%E4%B9%88%E6%A0%B7%E6%89%8D%E8%83%BD%E5%BD%93%E4%B8%8Asteem%E7%9A%84%E7%9F%BF%E5%B7%A5/)

- 
  [steem做档案存储](http://livinginau.life/2018/10/20/steem-%E5%81%9A%E6%A1%A3%E6%A1%88%E5%AD%98%E5%82%A8/)

- 
  [看yoyow白皮书随感](http://livinginau.life/2018/01/16/%E7%9C%8Byoyow%E7%99%BD%E7%9A%AE%E4%B9%A6%E9%9A%8F%E6%84%9F/)

- 
  [SMTs 白皮书读后感之一统天下](http://livinginau.life/2017/12/06/SMTs-%E7%99%BD%E7%9A%AE%E4%B9%A6%E8%AF%BB%E5%90%8E%E6%84%9F%E4%B9%8B%E4%B8%80%E7%BB%9F%E5%A4%A9%E4%B8%8B/)

- 
  [非对称加密解密的理解](http://livinginau.life/2017/12/05/%E9%9D%9E%E5%AF%B9%E7%A7%B0%E5%8A%A0%E5%AF%86%E8%A7%A3%E5%AF%86%E7%9A%84%E7%90%86%E8%A7%A3/)

- 
  [How to prevent DPOS being abused (如何防止DPOS 机制被滥用)](http://livinginau.life/2017/12/05/%E5%A6%82%E4%BD%95%E9%98%B2%E6%AD%A2DPOS-%E6%9C%BA%E5%88%B6%E8%A2%AB%E6%BB%A5%E7%94%A8/)

- 
  [在以太坊下搭建了私有链](http://livinginau.life/2017/12/05/%E5%9C%A8%E4%BB%A5%E5%A4%AA%E5%9D%8A%E4%B8%8B%E6%90%AD%E5%BB%BA%E4%BA%86%E7%A7%81%E6%9C%89%E9%93%BE/)

- 
  [Ethereum 和 Ethereum Classic](http://livinginau.life/2017/12/05/Ethereum-%E5%92%8C-Ethereum-Classic/)

- 
  [BTS初用感受](http://livinginau.life/2017/12/05/BTS%E5%88%9D%E7%94%A8%E6%84%9F%E5%8F%97/)

- [SBD如何锚定美元](http://livinginau.life/2017/10/05/sbd-peg-to-usd/)




