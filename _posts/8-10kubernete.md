---
layout:     post                            # 使用的布局（不需要改,js里有根据布局做判断）
title:      "Pod和Deployment的不同"           # 标题
subtitle:   "为什么我们要用Deployment而不是Pod"  # 副标题
date:       2019-08-10 12:00:00             # 时间
author:     "BZbyr"                          # 作者
header-img: "img/6223.jpg"       # 这篇文章标题背景图片
catalog: true                               # 是否归档
tags:                                       # 标签，可多个
    - Kubernetes
---

要先了解 kubernetes 的三个 object type, `Pods` `Deployment` `Service`.

- `Pods`-runs one or more closely related containers
- `Deployment`-sets up networking in a Kubernetes cluster
- `Service`-Maintains a set of identical pods, ensuring that they have the correct config and that the right number of them exist.

deployment 有非常关键的一点 Monitors the state of each pod, updating as necessary. 

一个pods虽然能包含多个containers, 但是缺乏pods对containers的监控, 使container保持alive的状态. deployment object 可以监控每个pod的状态, keep the replicas(pods) alive. 

Pods可能被killed, 并且也不能依赖这些Pods的IP地址, 因为这些IP地址不是持久的。这时候我们需要Service Object.

Service object (that is like a grouping object and gives it a so-called virtual IP (cluster IP) for the pods that have a certain label - and those pods are basically the app containers that you deployed with the former deployment object).