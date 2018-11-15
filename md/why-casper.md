# Why Casper?

---

## 分片技术和 Casper 是什么？
   
## 以太坊为何要从 PoW 转向 PoS?

---

## PoW 机制与以太坊性能扩展需求相矛盾

PoW： 工作量证明机制，与比特币一致。

以太坊节点：运行一个钱包账本，一个以太坊虚拟机 (EVM)。

全球计算机：每个节点的账本完全相同，EVM 上运行的程序也完全一样。

性能瓶颈： 当所有的节点都只能同时做一件事的时候，这就意味着整体网络能够处理的任务量是非常有限的。换言之 Transactions Per Second (TPS) 太低，大概不到 20。

Note:

以太坊的定位是一个底层的智能合约开发平台，其去中心化的公有链特性能够为智能合约以及去中心化应用（Dapp）的运行提供可信的执行环境。

--

案例：以太猫导致以太坊网络堵塞。

![](http://ww1.sinaimg.cn/large/d8eb23c4gy1fx93rsw9edj20g0091q66.jpg)

#### Image from: [https://www.cryptokitties.co/](https://www.cryptokitties.co/)


---

## 分片技术

分片技术（Sharding）:是一种基于数据库分片传统概念的扩容技术，是指把一个大的数据库进行水平分区，分成更小、更快、更容易管理的部分，这些小的数据就是大的数据库的片。

将以太坊网络划分成若干能够处理交易的较小组件式网络，不同的验证节点会因为不在同一分片而分别执行不同的任务，因此如果整个网络拥有了100个分片，那么整体的处理性能将会是原来的100倍。

PoW 与 Sharding 相互抵触： PoW 机制下， 较小的片区很容易处在被恶意矿工掌控的危险之中，假设分成 100 个片区，此时攻击者只需要 1% 的 hash 算力就可以完全控制一个分片。

解决方案：从 PoW  转向 PoS 机制。

---

## 如何实施 PoS

PoS 存在的缺陷： 恶意的节点验证者可以在没有任何损失的情况下去把自己的币押在分叉链上推动硬分叉（而 PoW 机制下，矿工分叉需要消耗算力资源）。

解决方案： 以太坊开发者们提出了他们不同于其他 PoS 的 Casper 协议，在这个协议下，系统可以快速惩罚节点的作恶行为。

---

## What is Casper?

Casper的工作机制：

- 验证节点需要在网络上押下一定比例的以太币作为保证金，当他们发现一个可以被添加到链上的区块时，他们将以通过押下赌注来验证它。

- 如果该区块最后被添加到链上，那么验证者们将得到一个跟他们的赌注成比例的奖励。

- 但是，如果某个验证者采用一种恶意的方式行动、试图做“无利害关系”的事，他们将立即遭到惩罚，他们所有的权益都会被砍掉。

---

### Why Casper works?

为什么 Casper 能解决 PoS 的缺陷？

纳什均衡 (Nash equilibrium)：纳什均衡是指博弈中这样的局面，对于每个参与者来说，只要其他人不改变策略，他就无法改善自己的状况。

假设你是一个节点验者将自己持有的 ETH 作为保证金存入网络，以最大化网络利益的方式来行事也有利于自己的利益。

当你知道作恶会使自己损失保证金的时候，你还会那么做吗？

总结一下：Casper 保证个人利益与整个网络的利益一致。

---

## PoW vs PoS

![](http://ww1.sinaimg.cn/large/d8eb23c4ly1fx94da4x13j20vv0cbgo2.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://etherscan.io/stat/miner?range=7&blocktype=blocks](https://etherscan.io/stat/miner?range=7&blocktype=blocks)

Note:

从这张图我们可以看到，目前大部分的以太坊算力基本集中在几个大矿池手中，大的矿工比其他矿工有更大的机会挖到区块获得奖励；而这意味着大矿工可以获得更多钱，进而买的起更好的设备使用更先进的矿场资源。
我们在经济学上有个规模经济的概念，意思是大的企业可以通过提高产量来降低他们单个产品的边际成本；而大矿工可以通过大规模的矿场来分摊固定成本，另外作为一个更大的经营主体，其拥有更强的议价能力。这就意味着，一个大的矿工投资一万元比一个小矿工投资一万元能够获得更多的哈希算力以及挖更多的币，虽然他们投入的资金是等量的。

---

## 防止算力中心化导致矿工作恶


规模经济：意思是大的企业可以通过提高产量来降低他们单个产品的边际成本。

大矿工可以通过大规模的矿场来分摊固定成本，作为一个更大的经营主体，其拥有更强的议价能力。

但是在 PoS 权益证明机制中，每个人投资一份保证金所需要的资金是相同的，规模经济在这里并不会起到太大的作用。

这与我们以往所认知的 PoS 更容易加大贫富差距的观点似乎提供了一个对立面的证据。

归功于 Casper 的保证金机制。

因此为了防止算力中心化导致矿工作恶的潜在风险也是以太坊转 PoS 的一个重要原因。

Note:

从这张图我们可以看到，目前大部分的以太坊算力基本集中在几个大矿池手中，大的矿工比其他矿工有更大的机会挖到区块获得奖励；而这意味着大矿工可以获得更多钱，进而买的起更好的设备使用更先进的矿场资源。
我们在经济学上有个规模经济的概念，意思是大的企业可以通过提高产量来降低他们单个产品的边际成本；而大矿工可以通过大规模的矿场来分摊固定成本，另外作为一个更大的经营主体，其拥有更强的议价能力。这就意味着，一个大的矿工投资一万元比一个小矿工投资一万元能够获得更多的哈希算力以及挖更多的币，虽然他们投入的资金是等量的。

---

## PoW 机制的高能耗

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94idrje3j20xc0m80ts.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

Note:

Rank: 71/233

Twh: 10^12  watt hour

--

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94lgnyfnj20xc0m8gmw.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

--

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94mahjnnj20rv0guq5b.jpg)

#### Image from (Static Date: Nov. 14, 2018) :[ https://digiconomist.net/bitcoin-energy-consumption]( https://digiconomist.net/bitcoin-energy-consumption)

--

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94nvobiyj20rz0e9mz5.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

--

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94ouovmxj20xc0m8gm5.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

--

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94qwx8ztj20xc0m8jry.jpg)

#### Image from (Static Date: Nov. 14, 2018) : [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

Note:

虽然比特币和以太坊的挖矿机制保障了这两个世界上最大的区块链能够这么多年稳定运行，其自然是非常具有价值的；但是我们仍然需要考虑，如此日益增长的高成本挖矿会不会有更好的方式去避免；而以太坊的Casper有可能会成为替代高耗能挖矿的一种解决方案。


---

## 以太坊Casper与分片技术最新进展

![](http://ww1.sinaimg.cn/mw690/d8eb23c4ly1fx94sgnstsj20sm0g37su.jpg)

时间：2018.6.3

地点：北京

演讲人： Vitalik Buterin

---

- 分片技术：[https://en.wikipedia.org/wiki/Shard_(database_architecture)](https://en.wikipedia.org/wiki/Shard_(database_architecture)

- 以太猫导致以太坊网络堵塞：[ https://www.coindesk.com/loveable-digital-kittens-clogging-ethereums-blockchain]( https://www.coindesk.com/loveable-digital-kittens-clogging-ethereums-blockchain)

- 硬分叉：[https://www.investopedia.com/terms/h/hard-fork.asp](https://www.investopedia.com/terms/h/hard-fork.asp)

- 纳什均衡：[https://en.wikipedia.org/wiki/Nash_equilibrium](https://en.wikipedia.org/wiki/Nash_equilibrium)

- Casper 起源系列：[https://medium.com/@Vlad_Zamfir/the-history-of-casper-chapter-3-70fefb1182fc](https://medium.com/@Vlad_Zamfir/the-history-of-casper-chapter-3-70fefb1182fc)

- 规模经济： [https://en.wikipedia.org/wiki/Economies_of_scale](https://en.wikipedia.org/wiki/Economies_of_scale)

- Ethereum energy consumption: [https://digiconomist.net/ethereum-energy-consumption](https://digiconomist.net/ethereum-energy-consumption)

- 以太坊Casper与分片技术最新进展：[ https://www.youtube.com/watch?v=VqOlOMAqC08]( https://www.youtube.com/watch?v=VqOlOMAqC08)

---

# Thank you
















