---
layout:     post
title:      "5 理性看待serverless"
subtitle:   ""
author:     "锐"
header-img: "img/algorithm/bg.jpg"
header-mask:  0.58
catalog: true
tags:
    - 技术



---

#### 前言

serverless这个概念挺长时间以前就听过，当时不太理解感觉很厉害的样子，这两天再次遇到，于是好好研究了一下。这是个新概念，上网大概搜了一下，抄作的一踏糊涂。但据我了解目前为止它的落地场景还挺少，相对复杂的业务场景也没有最佳实践。本文咱们就来讨论一下，serverless解决了什么问题，serverless的劣势，谁能吃到红利，为什么会火，是否过誉了。

#### 什么是serverless

> **Serverless computing** is a [cloud computing](https://en.wikipedia.org/wiki/Cloud_computing) [execution model](https://en.wikipedia.org/wiki/Execution_model) in which the cloud provider allocates machine resources on demand, taking care of the [servers](https://en.wikipedia.org/wiki/Server_(computing)) on behalf of their customers. "Serverless" is a [misnomer](https://en.wikipedia.org/wiki/Misnomer) in the sense that servers are still used by cloud service providers to execute code for developers. However, developers of serverless applications are not concerned with [capacity planning](https://en.wikipedia.org/wiki/Capacity_planning), configuration, management, maintenance, [fault tolerance](https://en.wikipedia.org/wiki/Fault_tolerance), or scaling of containers, [VMs](https://en.wikipedia.org/wiki/Virtual_machine), or physical servers. Serverless computing does not hold resources in [volatile memory](https://en.wikipedia.org/wiki/Volatile_memory); computing is rather done in short bursts with the results persisted to storage. When an app is not in use, there are no computing resources allocated to the app. Pricing is based on the actual amount of resources consumed by an application.[[1\]](https://en.wikipedia.org/wiki/Serverless_computing#cite_note-techcrunch-lambda-1) It can be a form of [utility computing](https://en.wikipedia.org/wiki/Utility_computing).

serverless看名字很容易理解成不需要server，客户端直接就能操作数据，但这是不可能的，就是个瞎起的名字，serverless强调的是运维细节交给云服务商，让开发者专注业务逻辑。server代码照样还得写。

#### serverless 解决了什么问题

要让我总结的话，可以用一个词概括：**降成本**。白天看了一个作者做serverless PPT，有个比喻很有意思，他把serverless的作用比作水龙头的开关，要用水的时候打开开关，用完了关上。个人觉得很贴切，一般开发大都是买个虚拟机一直开着，流量多了就加带宽，流量少了就减带宽，这就像水龙头一直开着，没人用的时候也在淌水，这就造成了资源的浪费。而serverless，有人访问就开一会儿，没人访问就关掉，因为无状态，多实例解决并发问题也很方便，这就赋予了服务以**弹性**。

#### serverless 劣势

> 软件开发没有银弹。   --[佛瑞德·布鲁克斯](https://zh.wikipedia.org/wiki/佛瑞德·布魯克斯)

引句名言来增加一点可信度，原作者是怎么想的不管了，但是事物具有两面性这是常识。简单聊一下我能想到的问题：

- 各领域的复杂场景缺少落地最佳实践

  过去许多业务场景基本都发展出了一套成熟的解决方案，如今切换到serverless，需要大量时间去做迁移。In the long run, we all die.相信这句话大家也听过吧，除了操盘手，很少人会把钱投在还不成熟的产品上去，领导不肯投钱，自然也就没有创新的动力。

- 工具函数复用困难

  平常咱们写API也经常会共用代码，也经常通过共享内存来实现一些逻辑。转换成云函数后共用代码就变得困难了，改动公用代码需要重新部署相关的全部云函数，而且由于函数各自隔离，共享内存也不可行只能借助第三方存储实现云函数间的通信。而且涉及到关系性数据库的操作感觉非常昂贵， 连接复用不起来。当然这些问题都可以交给云厂商去解决，事实上他们也是这么做的，AWS有Step Functions，Azure有Durable Azure Functions，GCP有GCP Workflows。各平台实现都不一样，使用这种高级服务的后果就是项目跟云服务商绑定了，去到另一个环境就跑不起来，迁移困难，反而失掉了一部分灵活性。

#### 谁能吃到红利

看好多技术小伙伴这么热衷前沿技术，希望从此能追上风口走上人生巅峰，感觉很可笑，历史证明，科技革命的受益者从来不是劳动者自己。从改革开放到现在，生产力提高了数倍，经济迅速发展，但多出来的生产力都被消化掉了，普通人的生活嘛，也就那样，现在年轻人甚至还发展出了躺平文化。

马克思早就说过，**生产力提高，资本家获取的剩余价值变多，劳动者反而被更深的剥削**，毕竟企业不会因为你用了什么新技术，开发快，就多发钱，就算涨钱，也远低于你给他赚的钱。一家企业由于生产力提高获取了超额利润，后面的企业也会逐步跟进，最后大家生产力都差不多，超额收益没了。

个人我觉得倒也有机会，一个是什么概念火就吹什么，自己开个公众号卖课，赚那些头脑发热的人的钱，稳赚不赔。另一个，那就是作为个人开发者，没有选择，要想不被市场淘汰甚至还想获取超额利润，就必须提高自已的生产力。

#### 是否过誉了

先说结论，是。这个概念火起来我认为跟经济下行有很大关系，企业想着降成本，而serverless提供了弹性，控制成本的粒度更小，当然它在某些场景的确能提高生产力，但业务不行，技术再厉害又有什么用呢？







