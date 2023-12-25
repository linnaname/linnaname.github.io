---
layout:     post
title:      2023 年博客数据分析
subtitle:   Google Analytics 与 Google Looker Studio 数据分析实践
date:       2023-12-24
author:     Lnn
header-img: img/home-bg-art.jpg
catalog: 	 true
tags:
    - 数据分析
    - Google Analytics
    - Google Looker Studio
    - 总结
    - 博客
    - 2023
---


**没有目的的数据分析是没有意义的**。过去几年我写博客并没有太多的目的，这也导致很难坚持下来。今年尝试去做一些改变，也是为了能够更好地坚持下去。做博客的数据分析一是好奇与有趣，更重要的是内容、推广方式、受众有一些概念和启发，也可以获得一些动力。


[《2022 年总结》]((https://www.linnana.me/2023/01/02/2022_overview/#%E4%B8%8B%E4%B8%80%E5%B9%B4))中对 2023 年的计划中有一项是“完成至少 6 篇博客”,这一目标完成的还算不错。 7 月份更换了[新的博客主题](https://github.com/qiubaiying/qiubaiying.github.io)后顺便把数据 Google Analytics 加上了。9 月份把 Github Pages 的域名 CNAME 到了之前一直使用的 [linnana.me](https://www.linnana.me),又对博客的访问速度和性能做了简单的[测试](https://www.zhihu.com/pin/1692851049566867456)。10 月份简单学习了如何使用 Google Looker Studio，于是在年底有了如下图的数据报告。

![](https://www.linnana.me/img/blog/summarize/2023-12-24-02.png)


你可以访问[这个链接](https://lookerstudio.google.com/reporting/5b7448fe-252a-46ce-abbb-bd7c16da333a/page/fUdK)（需科学上网）体验上面这份报告。



## 简单分析

虽然 3500+ 的总浏览次数并不多，甚至可能在样本量上太少不一定具备参考性。但看到有总共 833 位用户浏览过自己的博客还是觉得挺欣慰的。将近 4 分钟的用户平均会话时长至少说明内容质量是不错的。

#### 内容

今年的博客内容集中在过去两年自己在 TapTap 作为团队 Tech Lead 推行的工程实践和管理记录，文章列表如下：

- [面向开发者的技术文档如何维护](https://www.linnana.me/2023/09/28/writing-dev-doc)
- [关于远程办公](https://www.linnana.me/2023/09/21/remote_work/)
- [捉住成为团队管理者的机会](https://www.linnana.me/2023/04/20/TeamLead-team_fix)
- [我们是如何做 code review 的](https://www.linnana.me/2023/04/10/tech-codereview/)
- [如何写事故故障报告](https://www.linnana.me/2023/02/20/tech-learn_from_failure)
- [我们是如何进行工程师面试的](https://www.linnana.me/2023/01/20/tech-interview)
- [在 100 天里瘦了 30 斤](https://www.linnana.me/2023/09/20/Life-how_to_lose_wegiht)



流量的陡峰主要来源于知乎上我的一个[回答](https://www.zhihu.com/question/624981182/answer/3240883345)，此后每日的流量基本都是几个或者几十。


表现最好的是【[面向开发者的技术文档如何维护](https://www.linnana.me/2023/09/28/writing-dev-doc)】，可能是关于技术文档如何工程化的内容比较少。About 页的会话数量也符合了工程师的八卦心理。最让我有成就感的还是 【[在 100 天里瘦了 30 斤](https://www.linnana.me/2023/09/20/Life-how_to_lose_wegiht)】，有几位网友还特意在 TA 们的博文中有所提及。



#### 用户

受众的地理位置不仅仅是中国大陆也体现中国的特色（科学上网和肉身翻墙应该都有）。访问设备有 10 % 来自于 mobile 则出乎我的意料，这部分受众我猜测是用移动设备刷 V2EX/知乎的，但一般移动设备用户都不太会点开外部链接的（至少我不太会）。

受众的 Desktop 操作系统 60% 是 Mac 远超出了我的预期，说明工程师变得越来越有钱了。

本来想看看年龄、性别分布，以及其他用户特征，但不知道为什么数据一直出不来，只能作罢了。

#### 来源

**会话的主要来源是 V2EX 和知乎**。[V2EX](v2ex.com) 的来源较多主要是今年特意在一些互链交换帖子上做了一些回复，而知乎的来源是在知乎上我的一个[回答](https://www.zhihu.com/question/624981182/answer/3240883345)。

google 和 baidu 的来源则非常奇怪，或许是爬虫？然后就是几个友链带来的个位数的流量。

#### 搜索

在 Google Search Console 的后台上看几乎没有流量，也没有点击展示、点击方面的任何数据。国内因为没有做域名备案百度等搜索引擎也没办法提交录入。这也与上面的会话来源的数据比较符合。


## 胡思乱想

分析完了有什么结论呢？

#### 内容上
因为我写博客更多是为了自我输出，并不是为了流量所以内容上依然是我想写什么就写什么。哈哈哈！

#### 流量获得
V2EX 作为一个翻墙群体的论坛，流量质量是比较高的，是一个不错的推广地。但是由于论坛的特征主题的流量随着时间会流量下降会非常明显。因此如果想持续获得流量，就得不断发帖或者回复。知乎上回答引流则很困难，只能靠某个大 V 也回答了问题才有可能获得不错的流量。因此 **V2EX 和知乎上的推广可以坚持**。

从上面看搜索上基本没有流量，这也意味着流量变得不可持续！后面可以在搜索上做一些尝试。


#### 访问便利性

上面提到受众的访问地理位置具有中国特色(防火墙)，因此在没有备案的前提下国内用户访问便利性会受到很大的影响，不少用户由于访问速度的问题只是打开了首页但是没有浏览具体内容就离开了（这个开头有提到做过性能测试）。后面可以尝试做备案？或者内容静态化优化。


