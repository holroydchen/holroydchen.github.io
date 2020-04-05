---
layout:     post
title:      ETH vs EOS
subtitle:   
date:       2020-4-5
author:     Howard
header-img: img/post_blockchain.jpg
catalog: true
tags:
    - blockchain
    - ethereum
    - eos
---


After [my ethereum account in Metamask was hacked](http://engineerman.club/2020/03/31/metamask-account-was-hacked/)，I was always thinking about the root cause，I seldom used this account in metamask and the only two times I can remember is I once used it in debugging my own smart contract in eth testnet; another time is I tried to use it to play with ethereum DAPP，e.g. [some so called ethereum Defi product](http://engineerman.club/2020/03/22/play-with-Defi-borrow-lend-system/)，it is possible that those DAPPs have some bug，which lead to my account hacked？ In ethereum ecosystem，there is almost nothing we can do after this sort of event，even after the hack of DAO eth was hard forked to ethereum and eth classic. This makes me miss EOS, another competitive product of Ethereum.  I once made a comparison of ethereum and eos according to the request of one of my friends who was trying to develop a DAPP for a medical institution. 



|                          | ETHEREUM                                                     | EOS                                                          |
| ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Design principle         | The Ethereum network can almost be described as an application agnostic, that is, it is specifically designed as a platform that is neutral to all potential applications. This is as stated in the design principle document of Ethereum on github: Ethereum "has no specials" and refuses to have built-in "even extremely common high-level use cases as an intrinsic part of the protocol." This basic principle reduces the bloat of applications, but still requires many different applications for code reuse. And if the platform itself can provide more commonly used functions, then the efficiency of application developers can be much more improved. | EOS recognizes that many different applications require a variety of common functions, and seeks to provide these implementation methods, such as encryption and application / blockchain communication tools required by many applications. Based on this concept, EOS will widely introduce the following features: role-based permission admininstration, WEB toolkit for UI development, self-describing interface, self-describing database system, and a declarative licensing scheme. EOS provides these functions to be particularly effective for simplifying user account generation and management, as well as security issues (similar to declaring permissions and account recovery). |
| Consensus and governance | Proof of Work (POW) is currently used in eth. The problem behind it is that it is difficult to deal with destructive applications. For example, DAO encountered fatal bugs, and was attacked.  Thus destructive apps on Ethereum either cause investors to face potential substantial losses or face a hard fork that leads to chaos. | EOS uses a Delegated Prove of Stake (DPOS) mechanism, which includes a mechanism for freezing and handling destructive  applications. For example, if DAO occurs on EOS, it can be frozen, processed, or updated without disturbing other applications. In addition, EOS's DPOS consensus mechanism can avoid the potential for multiple competing chains during a hard fork. The 18 successful hard forks experienced by the Steem network have proven this, and it also runs on graphene. In addition, EOS will include a legally binding constitution that establishes common jurisdiction to resolve user disputes. It also includes a autonomous community based on equity weighting voting. |
| Performance              | At present, the Ethereum network is limited to CPU single-thread performance. Early test networks have achieved 25 transactions per second (under certain optimization conditions), which may be increased to 50 or 100 TPS (transactions per second) through optimization. However, under real application load, the Ethereum network's current transactions may be limited to 10 TPS or lower. | EOS relies on graphene technology that has demonstrated 10,000 to 100,000 transactions per second in stress tests. Secondly, EOS will use parallelization to expand the network, or it will reach millions of transactions per second. If these benchmarks are achieved, EOS will be able to support thousands of commercial-scale DAPPs. The TPS certified on EOS is currently about 1,000. |
| Transaction fee          | For Ethereum, every calculation, storage operation, and bandwidth usage in a transaction requires a GAS fee. And these necessary fees are fluctuating and can be set to very high prices, because miners always prefer to deal with transactions with high fees. In fact, Ethereum uses a leasing model. | EOS adopts the ownership model. Under this model, holding EOS tokens will give users a share of network bandwidth, storage and processing capacity. This means that if someone owns 1% of EOS tokens, he will always have access to 1% of the network bandwidth regardless of the load on the rest of the network. In this way, small startups and developers can purchase relatively small network shares to obtain stable and reliable network bandwidth and computing power that can be expected. When they need to expand their applications, they simply buy more EOS tokens. In addition, since the network has zero transaction fees, there is no other network development cost except for the first purchase of EOS tokens. Of course, if you want, you can also sell these tokens in order to recover the initial investment. |
| DOS                      | The Ethereum network has proved to be vulnerable to this kind of DOS attack. As we all know, in the Ethereum network, miners always preferentially choose high-fee transactions to be packaged into the blockchain. Due to the limited bandwidth and computing power in the network, it is foreseeable that if the network is flooded with high-fee fake spam transactions, this will effectively block many low-fee legal transactions. | EOS should be immune to this. The owners of EOS tokens give users proportional network bandwidth, storage space, and computing power. Therefore, a malicious attacker can only consume a corresponding proportion of network resources according to the proportion of EOS tokens. DOS attacks may be available in a particular application, depending on the design of the application, but these attacks will never disrupt the entire network. Even if many malicious agents try to create junk congestion for several large-scale network applications, they can guarantee the bandwidth reliability and computing power of small-scale startup investment projects on the network. |
| Development community    | The Ethereum mainnet was launched in 2015 and it took a long time, so the development platform and development tools of various smart contracts are highly mature. The main development language on Ethereum is solidity, a language similar to javascript, with such stable and reliable development framework as truffle. | EOS went online relatively late, and the mainnet  was launched at the end of June 2018, thus the development community is relatively immature, but Block.one (the company that develops EOS) and the community are working hard to improve the development community and platform. They launched EOS on coinbase  the smart contract development tutorials and incentives. The main development language of EOS is C ++, but people can also choose other development languages and then compile it into bytecode of web assembly. |
| Future                   | In order to solve its performance problems, Ethereum will gradually upgrade to the beacon of ETH 2.0 from 2019. At that time, it will launch a sharding mechanism, a POS / POW hybrid mechanism, and will accept ETH tokens starting in October To become a future POS miner, you must deposit at least 32 ETH. The transfer of tokens from the old Ethereum chain to the new blockchain will be irreversible, that is, after the old ETH is transferred to the new chain, it will not be able to Turn back. | EOS will upgrade the mainnet to 1.8 on September 23, 2019. This is not only for improving network performance, but also for a major product voice in the future-a social product that will subvert twitter, facebook can be well in EOS Running. EOS will support the expansion of the Bitcoin network, making the current Lightning Network unnecessary. It even has to support IPFS as a decentralized network storage function. |









# Conclusion



The performance of EOS is beyond Ethereum, but its DPOS mechanism has been criticized by many industry insiders, who believe that the degree of decentralization and anti-censorship are not enough, and the current development platform and technical support are not as perfect as Ethereum. If the upgrade of Ethereum is successful, its performance will not be a big problem, but it has been upgraded for several years, and this period of time gives the EOS a chance to catch up with. Nevertheless, since the development of Ethereum, its community and development framework are much more mature than EOS, for now, many people still choose to develop new products on Ethereum and then gradually transplant to EOS.


Related topics:

- [My Ethereum account was compromised](http://engineerman.club/2020/03/31/metamask-account-was-hacked/)

- [Using smart contract to kick off OTC platform](http://engineerman.club/2018/12/30/Using-smart-contract-to-kick-off-OTC-platform/)

- [cryptocurrency exchanges integration trading system](http://engineerman.club/2018/12/06/cryptocurrency-exchanges-integration-trading-system/)

- [Stable Coins](http://engineerman.club/2018/12/06/Stable-Coins/)

- [Decentralized Trading System for people to trade crypto without account](http://engineerman.club/2018/12/06/Decentralized-Trading-System-for-people-to-trade-crypto-without-account/)

- [comparison several crypto exchanges according to my own experience](http://engineerman.club/2017/12/05/comparison-several-crypto-exchanges-according-to-my-own-experience/)

- [Programmatic Trading on dYdX](http://engineerman.club/2020/02/02/Programmatic-Trading-on-dYdX/)


- [In a first, MakerDAO protocol to auction MKR tokens to cover $4M bad debt](http://engineerman.club/2020/03/18/MakerDAO-protocol-to-auction-MKR-tokens-to-cover-$4M-bad-debt/)

