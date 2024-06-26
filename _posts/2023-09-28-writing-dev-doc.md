---
layout:     post
title:      面向开发者的技术文档如何维护
subtitle:   技术文档工程化
date:       2023-09-28
author:     Lnn
header-img: img/home-bg-art.jpg
catalog: 	 true
tags:
    - 技术文档
    - 团队规范
    - 文档
    - 技术建设
    - 规范
    - 指南
---

## 前言

文档即产品门户。在一个商业化的项目中，如何用**工程化**的思维和实践更好的持续迭代文档是一件非常值得思考的问题。


平常工作中我们接触到的文档主要包括两类：
- 类似 API 设计、架构设计、技术改动设计、逻辑设计等等
- 面向用户比如开发者，更专注于教程和概念的文档。


在《[我们是如何做 code review](https://www.linnana.me/2023/04/10/tech-codereview/#%E5%A6%82%E6%9E%9C%E6%98%AF%E6%96%B0%E5%A2%9E%E5%8A%9F%E8%83%BD%E4%BB%A5%E5%8F%8A%E7%A8%8D%E5%A4%A7%E7%9A%84%E6%94%B9%E5%8A%A8%E8%AF%B7%E6%8F%90%E5%89%8D%E8%BE%BE%E6%88%90%E8%AE%BE%E8%AE%A1%E4%B8%8A%E7%9A%84%E5%85%B1%E8%AF%86)》中提到如果是新增功能以及稍大的改动请提前达成设计上的共识。这类前后端、客户端、后端之间达成设计一致的文档属于第一类。这类文档结构化程度没有那么明显，我们主要放在 Confluence 和 Gitlab Wiki 里。平时工作中，工程师接触可能更多的是第一类。


但这里主要谈第二类，这一类文档内容复杂，工程化的 ROI 更高，同时又因为其用户是开发者或者用户。内容往往会涉及到研发工程师、技术支持工程师、产品经理等等角色，工程化带来的业务价值也更明显。


## 内容是首要的

**文档通常是为了产品用户的利益而创建的**。它的主要目的通常是帮助用户完成产品的某些任务，因此在制作不同类型的技术文档时，应始终考虑到最终用户。而**文档的内容是评判文档好坏的最好的标准。** 

- **信息传达**：文档的首要目标是传达信息。无论是教程、指南、手册还是说明书，文档需要提供详尽、明确和准确的信息，以满足读者的需求。良好的内容能够帮助读者理解和掌握所描述对象的知识和操作。
- **解决问题**：开发者查阅文档的常见原因是为了解决问题。好的文档内容能够回答读者可能提出的问题，并提供解决方案和示例。它可以帮助开发者快速定位问题，并给予正确的指导，提高效率和准确性。
- **提供指导**：文档内容应提供明确的指导，帮助开发者完成特定任务或实现特定目标。良好的内容能够清晰地解释步骤、操作和概念，并提供示例和提示，使开发者能够顺利地应用所述对象。
- **用户体验**：内容直接影响开发者的体验。清晰、准确、易于理解的内容可以提升开发者对文档的满意度，并增强开发者对所述对象的理解和操作能力。相反，混乱、模糊或错误的内容会导致开发者困惑和不满。

脱离好的内容，再好的工程化都是没有意义的，不要因噎废食。

## 文档由谁来写，谁来审核


#### 谁来写
**谁更熟悉就谁来写**。

我们的服务是面向开发者的，部分功能下游的产品经理或者运营也会接触到。

最熟悉的人当然是工程师，因此文档主要由开发此功能的工程师来写，当然也有部分文档由技术支持来写，极少部分由产品经理来写。之所有由技术支持、产品经理来写也是因为他们是最熟悉这部分功能的人。

而不熟悉这个功能的人则不应该参与文档编写。有部分公司觉得文档工作不重要就交给一个新人来写，我不太能接受这种做法。一个不熟悉业务的人正更需要帮助，却让 TA 来写文档，这多少有些荒谬。

#### 谁审核

面向开发者的文档我们一般有至少一位技术支持工程师来做 review，技术支持工程师作为接触开发者和处理工单的第一经手人，他们更能从开发者角度来审视文档是否从开发者角度出来了。同时也可以增加之前有较多 review 经验的工程师来一起参与 review。



## 版本控制

上面提到我们的开发者文档编写者主要包括：完成该功能的研发工程师、技术支持、产品经理以及相应的审核人，而且往往我们会有多个功能需要同时写文档。因此使用版本控制系统可以尽可能的保证内容的更新得到合理的控制，冲突问题也更容易解决。

文档一般我们都会托管在 Gitlab 上，更新文档需要通过 Merge Request 或者 Pull Request 这样的机制来发起。不允许直接更新 master 分支。文档的修改必须要经过至少一位技术支持的 review 才能合并到 master 分支。

至于国际化多语言是采用一个 repo 多个模块还是多个 repo，取决于各自的实际情况。我们团队维护的文档目前只包括中文和英文，采用了两个 repo。



## 能自动化尽量自动化


#### CI/CD 自动化

因此在 MR / PR 被创建之后，CI/CD 会自动执行一次预发布，将文档部署到一个预发布环境中。同样 在 MR / PR  被合并到 master 分支之后同样也会执行一次预发布，打 tag 之后会自动更新预发布环境和正式环境。这用 Gitlab CI/CD 可以很方便的做到，如果你在使用 Github 则可以使用 Github Action 来达到同样的效果。

#### 方便的脚本

为了减少 reviewer 的负担，同时提高  Merge Request 或者 Pull Request 的质量，我们通常会提供一些脚本方便发起者本地使用。
比如江宏大佬提供的 [add-space-between-latin-and-cjk](https://github.com/hjiang/scripts/blob/master/add-space-between-latin-and-cjk) 可以非常方便地添加英文和中文词之间的空格。这些脚本会同样也会放在仓库中进行维护，比如当前博客的目录下就有一个 [add-space-between-latin-and-cjk](https://github.com/linnaname/linnaname.github.io/blob/master/add-space-between-latin-and-cjk) 脚本，每次新增或更新文档我都会实现一遍这个脚本。


## 尽可能保持一致的风格

让很多人措施行文风格一致是非常困难的，甚至不可能做到。文案风格的形成可能是在细节上，但更多在于文案作者本身的文学经验等等。

因此还是需要一些技术性的规范来提高行文风格一致的可能性。

#### 规范或指南

在技术性的细节上我们团队主要遵守如下两个规范：
- [《中文文案排版指北》](https://github.com/sparanoid/chinese-copywriting-guidelines)
- [《英文文档风格指南》](https://github.com/kodecocodes/english-style-guide)


#### 审核人或者团队尽可能固定
审核人或则审核团队对于保持文档长期的风格一致性是至关重要的。

软件工程历史可能是最典型的例子是 Linux Kernel（好的与坏的），同样的
[Linux Kernel Docs](https://www.kernel.org/doc/html/v6.1/) 中也充满了 Linus Torvalds 以及内核核心团队的个人印记。或许也正是因为 Linus Torvalds 的坚持，在长年累月无数开发者不断地代码共享后，Linux Kernel Docs 仍然可以将文档和 Code as Document 理念贯彻到底。

因此在选择审核人时尽可能在某个模块地审核任务提交给一个到两个固定的审核人，这样有利于保持风格的一致性。


## 预发布

事实上在技术文档，尤其是面向开发者的技术文档的发布过程中，预发布发布是很重要的。

如果一个 PR 包含了在 Review 的时候未发现的事实错误和样式渲染错误，因为没有提前再次确认一遍。导致开发者因为这些错误，严重误解了某个功能（比如我们团队负责了支付业务），乃至进一步造成了严重的线上事故，这是不可接受的。同时没有预览环境也会导致工程师疑虑重重，不敢于发布，久而久之就会衍生出团队内对更新文档和发布的恐惧。

因此在 MR / PR 被创建之后，Gitlab CI/CD 会自动执行一次预发布，将文档部署到一个**预发布环境**中。我们的预发布环境提供了一个特有的共享 preview 域名，内部所有人都可以同时访问，这样让多人协作和审核变得更简单方便。在 MR / PR  被合并到 master 分支之后同样也会执行一次预发布。这样一些样式错误、渲染错误、内容出错等等问题可以更早的被大家发现。

只有从 master 打出 tag 之后文档才会自动部署到正式环境。


## 用了哪些工具

工欲善其事必先利其器，以下是我们在用的一些工具：
- [Docusaurus](https://docusaurus.io): 支持 Markdown、全文搜索、自定义主题等等功能。帮助开发者快速创建具有优雅外观和良好用户体验的文档网站。因为 Markdown 的易用性，不管是工程师还是技术支持、产品经理都可以很容易的参与进来。
- Gitlab CI/CD: MR / PR 被创建之后，CI/CD 会自动执行一次预发布，将文档部署到一个预发布环境中。在 MR / PR  被合并到 master 分支之后同样也会执行一次预发布。我们用 Tag 进行发布管理，因此打 Tag 会自动执行一次预发布，并自动进行正式环境发布。如果代码托管在 Github 上也可以使用 Github Action 来完成。
- [LeanEngine](https://developer.taptap.cn/docs/sdk/engine/overview/): 文档仓库放在 LeanEngine 上是因为它是我们自己的产品，它提供了预发和正式环境。同时提供了一个用于预发环境的共享子域名，命令行工具也非常方便。如果有需要也可以选择 Github Pages 和 Cloudflare Pages 的静态页面产品。
- 常用 scripts: 上面自动化章节里提到的类似 `add-space-between-latin-and-cjk` 的脚本，放在文档代码仓库中，在代码提交之前应该在本地做检查和执行。


## 如何让团队内写技术文档的氛围更好

团队成员可能会更重视项目业务代码仓库的建设，团队 leader 可能更关注业务带来的正面价值。而技术文档由于没有直观的业务价值，其长期建设的优先级往往被降级。那怎么让团队内写技术文档的氛围更好呢？


首先任何工程实践的实施都要以对现状的理解为基础 , 比如说对新工具的接受度、具体的业务特征、技术成熟度等。脱离具体的上下文，照搬“普适”的框架，会带来巨大的适配成本。我向来反对不尊重现状和团队需要的工程实践，因此 Team Leader 在推行工程实践时，更应该结合实际做**渐进式**地改善。

以下是我的一些思考和经验：

#### 好的榜样
团队里的核心骨干或者 Team Leader 应该在这方面起到榜样的作用。TL 应该做到从自己开始，逐步地引导大家，也可以带头把一些自动化工具做好。当你能够以一个比较高的标准去持续输出文档的时候，身边的其他人多多少少也会被你感染，潜移默化地和你保持一致的标准。

**在一个开放透明的团队里，好的习惯和理念是很容易被传播的。**


#### 直接的参与感
让团队内每个人都有参与的机会，而不是把写文档的机会或者任务把控在一到两个人的手上，同时也不要出现只有某个新人比较闲于是把写文档的任务交给 TA 的情况。直接的参与感不管是对于新人还是老同事都是最直接的。作为 TL 我一般会就一些有争议的话题咨询大家的意见，这样大家就会有参与进来的契机。


#### 不要过早追求可度量化

**过分地追求可度量化**很容易导致指标倾向滑坡，比如追求工程师的 PR 数就很可能导致多了很多毫无意义的 PR。开发者类的文档可能我们会使用 TTFHW(Time to first hello world) 这类可度量的指标，但早期还是应该更注重团队内文档文化的形成。PR 数 & Issue 数、美观性再逐步去改善。



## 一些不错的参考和实践
 - [Software Engineering at Google](https://abseil.io/resources/swe-book/html/toc.html) 的 [ch10](https://abseil.io/resources/swe-book/html/ch10.html)
 - [Google Technical Writing Courses](https://developers.google.com/tech-writing)
 - [MicroSoft Writing Style Guidelines](https://microsoft.github.io/code-with-engineering-playbook/code-reviews/recipes/markdown/#writing-style-guidelines)
 - [Best Practices When Documenting Your Code for Software Engineers](https://betterprogramming.pub/best-practices-when-documenting-your-code-for-software-engineers-941f0897aa0)
 - [Google Developer Documentation Style Guide](https://developers.google.com/style)
- [文档工程体验设计：重塑开发者体验](https://zhuanlan.zhihu.com/p/421575340)

