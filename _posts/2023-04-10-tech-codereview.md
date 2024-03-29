---
layout:     post
title:      我们是如何做 code review 的
subtitle:   从自己开始，从现在开始
date:       2023-04-10
author:     Lnn
header-img: img/home-bg-art.jpg
catalog: 	 true
tags:
    - 代码评审
    - code review
---


关于 code review 在开发中的重要性已经有很多的文章讨论，我这里不想再过多重复。但是作为 Tech Lead 在工程实践上仅能保留一条团队规则的话，那么坚持 code review 是我愿意持续坚持的。

关于 code review 的各种方面，Google 出了一个最佳实践[How to do a code review](https://google.github.io/eng-practices/review/reviewer)。同时还有一本书 [Software Engineering at Google](https://abseil.io/resources/swe-book),在 [ch09](https://abseil.io/resources/swe-book/html/ch09.html) 花了一整章介绍关于它的方方面面。


本文主要介绍自己的一些个人经验和感受，特别是作为 Tech Lead 推进团队 code review 文化的一些思考。

### 从自己开始，从现在开始
一个很残酷的现实是国内工程师因为公司业务压力或者个人经历的原因，很多团队可能都没有实施过 code review, 那么作为 Tech Lead 想要推行严格有效得 code review 是比较困难的。这时候 Tech Lead 可以先从做好自己开始，比如从把自己的代码发给别人 review 开始，分享一些自己案例，当遇到有意思的讨论也可以发出来让更多的人参与进来讨论，实际可见的参与感或者价值是最有说服力的。

### 代码在合并到主干之前进行需要 review
每一行代码合并到主干之前必须进行 code review，代码必须经过**至少一个** reviewer 的 review, Merge Request 才能合并到主干。事后几个人坐在会议室里一起 review 代码的方式可以作为一个互相学习或者改进的机会，但是这种事后的机制我是不太推荐的。这种事后 review 的方式无疑会导致破窗越来越明显。


### 能自动化的尽量自动化
风格规范（缩进、空行等）的检查，这类问题应该尽可能地通过工具完成。接入 Lint 工具也是一件 ROI 比较高的事情 , 推荐本地使用 SonarLint 等类似的工具做一些检查 , 我们的代码仓库放在 GitLab 上因此我们在 CI/CD 流程里集成了 SonarQube 进行代码质量检查。

这些自动化的工具可以让负责 review 的工程师把更多注意力放在更高层面的评审上比如业务逻辑等等，减少工程师的 review 负担。当然，这并不是说人工 review 的时候应该忽略代码风格等细节问题，毕竟 linit 工具的更新可能是不及时的，而且现实实际的编码并不总是 100% 符合 lint 工具的规范。

同时也可以把 review 提交、评论、approved、合并等行为通知到团队使用的 IM 工具上，比如我们团队使用的是 Slack，我们会建立一个专门的频道将相关的同事加入到这频道，Gitlab 可以非常方便的把通知发送到 Slack 里，有上述变更时都会有内容通知到这个频道里。


### 如果是新增功能以及稍大的改动请提前达成设计上的共识
为了避免我们在 code review 的阶段再对设计有调整从而导致返工，在有新增大的功能以及稍大一些的重构改动时应该就设计上的问题先讨论清楚。比如 REST API 的设计、数据库表的新增、新组件的引入、架构的设计等等，都应该提前写好文档做好提前的讨论，在设计上提前达成一致。文档可以选择 Confluence 也可以使用 Gitlab Issue 来记录或者讨论。

这样的方式做的好处在于：
- 可以让负责设计的人提前理清思路
- 在设计上提前达成一致，避免在 code review 阶段返工
- 沉淀文档方便 reviewer 以及后继的同事查看

### 把 code review 作为日常工作的一部分
不管是需要把代码提交给其他同事 review 还是需要作为 reviewer 去 review 其他同事的代码，这个过程都是耗时的。把 code review 作为日常工作的一部分可以让工作更有计划同时也让大家更加从容，使得 code review 制度更容易得到持续执行。

**在这一点上 Tech Lead 应该需要起到决定性的作用，在团队内达成一致，让团队成员放心的花一些时间来做  code review。**


### 每次提交 review 的代码应该尽可能少
开发的时候尽量把大的改动分解成多个小的改动，每完成一个小的改动就提交一次 review。避免出现一个 review 需要看几百行改动代码。基本上一个改动如果出现超过 300 行代码的 MR 阅读起来就会非常困难，也很难让人有心思看。


### 不要期待 reviewer 能够立即回复你
日常工作中大家可能都比较忙，不太可能刚提交了 review 就去 reviwe 你的代码。因此和 reviewer 沟通好发布计划是一个比较好的选项。同时也可以将代码发给多人 review。



### Merge Request 的发起人应该为该 MR 的合并以及后继的发布负责起来
- 如果 review 进度不理想应该主动推进，比如在 Slack 上起一个 thread 快速讨论清楚。
- 代码 Megre 应该由 MR 发起人来操作。
- 谁提交的代码出了问题，则谁来承载主要责任。做例行的人或者后继发布的人不需要为别人的代码 bug 负责。
- 发起人应该主动进行 MR 合并后的数据变更、发布上线等操作。


### 不要在 code review 中带入个人情绪
接触过以一些程序员他们觉得在 code review 提各种意见是对他个人的有意见，我是不太能够理解这样的想法的。代码是团队或者公司的财产，同事 A 写的代码可能在过了一段时间以后可能就由同事 B 来维护，因此很可能你写的代码不久之后就会有 review 你代码的人来维护。

当然也应该杜绝在 code review 的过程带入其他的个人情绪，就事论事的进行代码评审。


### 不要流于形式

根据破窗效应，一旦有流于形式的情况出现则这种情况就会持续蔓延开来。因此作为 Tech Lead 应该禁止“你帮我 approve 一下”这种没有任何 review 只为 approve 的行为出现。


这篇文章也同步发布到了[知乎](https://zhuanlan.zhihu.com/p/629297197)

