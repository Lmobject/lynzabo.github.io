---
approvers:
- bgrant0607
- thockin
title: Kubernetes文档
---

Kubernetes文档可以帮助你系统的了解怎么使用Kubernetes编排你的应用程序。文档适用对象包括初学者/高级研究者。如果你还不清楚Kubernetes是什么，怎么工作，可以阅读"[What is Kubernetes](/docs/concepts/overview/what-is-kubernetes/)"。

## 互动教程

[Kubernetes互动教程](/docs/tutorials/kubernetes-basics/)提供了一个虚拟终端，通过这个虚拟终端你可以直接在浏览器上可以远程操作Kubernetes。学习完这章后，你会明白如何在Kubernetes系统中部署应用、暴露服务、做服务弹性伸缩、回滚一个容器应用等知识。

## 安装Kubernetes

[选择适合你的方法](/docs/setup/pick-right-solution/)提供了很多方式来安装运行Kubernetes集群，包括本地开发环境，第三方云提供商，你自己的私有集群。

## 概念，任务，教程

我们文档提供了大量资源让你学会使用Kubernetes，精通Kubernetes。

* [概念](/docs/concepts/) 深入讲解了Kubernetes各个组件、服务工作原理。
* [任务](/docs/tasks/) 讲解了从入门到深入的使用Kubernetes提供的各个对象。
* [教程](/docs/tutorials/) 详细讲解了Kubernetes工作流程。

## API和Command参考

[参考](/docs/reference/)部分提供了完善的，如何使用Kubernetes提供的API、SDK，如何使用`kubectl`命令行工具。

## 工具

[工具](/docs/tools/)部分罗列了很多Kubernetes相关的工具，包括Kubernets工具链配套工具和第三方工具Kubernetes相关的工具。

## 故障排除

[故障排除](/docs/tasks/debug-application-cluster/troubleshooting)罗列了大量常见故障处理办法，方便查找错误。

## Kubernetes版本介绍

Kubernetes使用`_X.Y.Z_`版本方式，_X_是大版本号，_Y_是小版本号，_Z_是补丁版本号。Kubernetes一次支持三个小版本，这包括当前的发行版本和两个以前的版本。上Github可以查看[Kubernetes Release](https://github.com/kubernetes/kubernetes/releases) 最新的版本信息。

### 有关小版本注意

Kubernetes master节点，node节点，kubectl客户端之间允许有一定的版本偏差。node节点上组建的版本号最多滞后两个小版本号，但不会超过主版本号。客户端版本号可能会滞后一个小版本，并可能超过一个小版本。

例如，Kubernetes master节点v1.8版本，与node节点v1.6，v1.7，v1.8兼容。与客户端可以v1.7，v1.8，v1.9兼容。

### 补丁版本号Patch Versions

补丁版本号上包含一些严重bug的fixed，建议你使用最高的布丁版本号，或者直接使用下一个小版本号release。
