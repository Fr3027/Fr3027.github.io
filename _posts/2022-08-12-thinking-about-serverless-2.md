---
layout:     post
title:      "7 理性看待serverless（二）"
subtitle:   ""
author:     "锐"
header-img: "img/algorithm/bg.jpg"
header-mask:  0.58
catalog: true
tags:
    - 技术




---

#### 前言

看serverless有点迷糊， 这篇文整理了一些我的疑惑以及在对应的解答。

1. 应用场景有哪些（associated with "on-demand" functionality）

   - data processing (e.g., [batch processing](https://en.wikipedia.org/wiki/Batch_processing), [stream processing](https://en.wikipedia.org/wiki/Stream_processing), [extract-transform-load](https://en.wikipedia.org/wiki/Extract,_transform,_load) (ETL))

   - [Internet of things](https://en.wikipedia.org/wiki/Internet_of_things) (IoT) services for [Internet](https://en.wikipedia.org/wiki/Internet)-connected devices,

   - [web applications](https://en.wikipedia.org/wiki/Web_application)

   - creating [APIs](https://en.wikipedia.org/wiki/API) for already built applications without breaking down or modifying the current or existing functionality of the application.

2. 去github上找最佳实践的项目

3. 这么多云厂商，该如何选择？

4. 如何用该模式跑通一个完整的标准的项目

5. serverless 与 faas 有何区别和联系 ✅

   - faas 是实现serverless 理念的一种途径而已

6. Comparsion with PaaS application hosting services✅

   - [Platform as a service](https://en.wikipedia.org/wiki/Platform_as_a_service) (PaaS) application hosting services is similar to FaaS in that they also hide "servers" from developers. However, such hosting services typically always have at least one server process running that receives external requests. Scaling is achieved by booting up more server processes, which the developer is typically charged directly for. Consequently, scalability remains visible to the developer.[[5\]](https://en.wikipedia.org/wiki/Function_as_a_service#cite_note-5)

   - By contrast, FaaS does not require any server process constantly being run. While an initial request may take longer to be handled than an application hosting platform (up to several seconds[[6\]](https://en.wikipedia.org/wiki/Function_as_a_service#cite_note-6)), caching may enable subsequent requests to be handled within milliseconds. As developers only pay for function execution time (and no process idle time), lower costs at higher scalability can be achieved (at the cost of latency).

7. serverless framework 跟云厂商提供的云函数服务和宣称的serverless有什么关系？ ✅

   - serverless是一种理念，而serverless framework可以看做是一个脚手架工具，有了他，可以方便地在本地开发，然后一键部署到云平台上。二者不属于同一个组织。

1. spring cloud function 与 faas有什么关系，是否有最佳实践