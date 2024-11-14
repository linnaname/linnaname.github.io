---
layout: post
title: 小小团队的工程基建
subtitle: 平台工程
date: 2024-09-15
author: Lnn
header-img: img/home-bg-art.jpg
catalog: true
tags:
  - 平台工程
  - Istio
  - 工程基建
---

不管是独立开发者还是数人小团队，打造高效试错的环境至关重要。**获取更多的用户、把产品做好永远是第一要务**。因此，我写这些并不是鼓励你在这些工具、平台上尝试，只是记录自己所使用到的一些平台和工具。

## VCS

代码直接托管在 [gitlab](gitlab.com)，免费薅的羊毛包括：

- 基于 Git 的版本控制。
- 基本的 CI/CD。
- 限量的存储和 CI/CD 分钟：免费存储空间和每月 400 分钟的 CI/CD 运行时间。基本够用。
- 协作工具：我们一般都用 issue 来驱动小的需求。
- Container Registry：托管 Docker 容器镜像。
- Project 和 members 不限制数量

如果你们是一个几人团队完全不需要自建，当然也可以用 Github。

## Vercel

[Vercel](https://vercel.com) 把与 [Next.js](https://nextjs.org/) 云函数的融合做得非常好，10 个 endpoint 内是免费的，但是超过了则需要 $20/month，我一般都是不同的账号注册来薅羊毛，写一个非常小的项目时非常方便。也有 redis、postgress 这样的存储可以用在小项目上。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image.png)

但有一点需要注意，**Vercel 的 endpoint 如果超时超过了阈值是需要额外收费的**，如果做 StableDifffusion 这样的 API 对接接口是非常耗时的，不建议放在 Vercel 上。否则可能早上刚起床房子就不是你的了！

我一般使用 [netlify](https://www.netlify.com) 在放静态类型的资源，比如官方教程或者文档这些，然后再 CNAME 到自定义域名上就可以了。

以上两个平台都支持 Gitlab 或者 Github 代码更新了自动触发 CI/CD。

## Cloudflare

这个大部分接触过全球部署或者产品海外发行的工程师应该都知道。而且基础的功能都可以免费薅到羊毛。

以下是我主要使用的两个功能：

- CDN： 免费又好用。
- Workers：你甚至不再需要 Vercel 这种平台，只需要写 JS 就可以了。

## Cloud Provider

如果项目的复杂度大到一定程度了，或许你开始考虑要上云了，那么恭喜你，至少算是“活下来了”。大部分 side project 基本是活不到这一步的。

到这里，你可以选的云厂商很多，包括但不仅限于：AWS/Google Cloud/Microsoft Azure/DigitalOcean 等等，这些厂商同样有各种各样的羊毛可以薅......

我用了 [Vultr](vultr.com),它同样有 Free Tier Program 可以节省一点费用。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_01.png)

## Kubernetes

我直接用了 [Vultr Kubernetes Engine (VKE)](https://docs.vultr.com/vultr-kubernetes-engine)，这样不用自己来维护集群。

Gitlab 可以非常方便的连接 Kubernetes（[参考文档](https://docs.gitlab.com/ee/user/clusters/agent/ci_cd_workflow.html)）

连接成功后，所有项目都可以共用它。
![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_02.png)

## CI/CD

1. Gitlab PR 触发 Gitlab CI/CD,使用 Gitlab shared runner 进行 lint、自动化测试。

2. 在 Gitlab shared runne 上 build Docker 镜像，并 push 到 Gitlab Container Registry。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_04.png)

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_05.png)

3. 通过上述提到的 Kubernetes 连接，集群可以拉取到 Docker 镜像。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_03.png)

大致流程如图

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_03.png)

## Istio

如果一个域名一个服务，那么直接用一个 LB 就可以了，然后你可以把 LB 的流量导到对应的 Kubernetes Headless Service 上。

稍微复杂点，你有多个子域名，多个服务。比如 api.example.com、console..example.com 等等都区分开来，你可以选择：[Nginx Ingress Controller](https://docs.nginx.com/nginx-ingress-controller)，然后用 [cert-manager](https://cert-manager.io/docs) 来管理 HTTPS 证书。

更复杂可能会引入类似 Istio 这样的 Service Mesh 方案，它的好处或者如何使用我这里不再重复介绍，具体可以看[官方的文档](https://istio.io/latest/)。我觉得比较好用的方面：

- Nginx Ingress Controller 的流量入口功能可以用 Istio Gateway 来代替。
- 可以非常方便的实现金丝雀发布，支持基于请求 Header，Cookie 或者其他自定义范围。
- 可以很快的实现服务的 A/B 测试。
- 支持多种负载均衡、outlierDetection、connectionPool 等实现起来也非常简单。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_06.png)

- 非常方便的集成 kiali 控制面板、prometheus、grafana、jaeger 等组件，提高系统的可观察性。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/engineering/image_07.png)

我目前就一直在用 Istio，目前感觉还不错。当然需要承认 sidecar 的方式是会带来一定的性能损失的。
