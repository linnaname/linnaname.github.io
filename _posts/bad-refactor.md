

# 从错误的工程实践所能窥见的



### 锅从天上来

今年2月份由于公司把一个**既非常新又非常老**(后面会解释为什么这么说)的产品调整到了我所在的团队，代码、研发、产品





### 错误的工程实践




### 纠正的过程是漫长且痛苦的

- 代码评审
- 自动打包
- 灰度发布流程
- 基础监控、业务监控以及报警
- 集成测试
- 控制需求
- 及时沟通
- 文档


一个好的主管很重要，管理的重要性。
善于利用团队的力量：
- 更多的研发参与进来开发、讨论方案、参与代码评审
- 技术支持参与进来答疑和分担非研发性任务
- SRE参与进来分担运维压力



2个月里问题逐渐暴露经过团队的共同努力把一些紧急的问题修复完之后，终于能腾出来手来。


4月中旬在团队的共同努力下在较短的时间内支持了公司内一款非常重要游戏的上线，并且期间没有出明显的故障。
5月在我们参与度不强的情况下，公司另一款重要的自研游戏上线，上线期间也同样没有明显故障。出现的一些小问题也得到了及时的处理和修复。整个Q2除了一个Q1的遗留故障外，没有出现研发上导致的线上故障。

> 每次上线他们都是采用灰度方式发布，一定要看到正确的 event 出现，要看到问题被 fix 的证据出现，才认为线上服务运行正常，才会慢慢扩大灰度范围。春节过后搞出过很大的动作，但是最近两个月虽然有很多次上线，但是整体还是非常稳定的，这与他们的努力是分不开的。


## 到底谁应该来为这样糟糕的结果负责


这种短期内系统性的线上故障爆发，是研发与管理的共同失误，是团队的整体问题。

### 管理

我无心参与公司的办公室政治（我相信团队内暂时也没有明显的办公室政治），但是的，**我就是在指原团队的Leader在管理水平上的缺失**，毕竟我是直接的受害者，我想我还是有这个权利的。

以下部分信息来自于原小组成员的一些反馈，一些来自于我的观察

- **新人为主**：小组内成员大部分都是新人，对老版本的业务逻辑并不是熟悉
- **研发资源非常紧张**：每一个端Android/iOS/Unity/服务端每一个端都只有一位研发负责，并且他们既需要维护老版本同时也需要重写版本。没有充分发挥团队的力量
- **没有对研发质量进行把控**
- **需求管理和项目管理缺乏**
- **对重写难度的低估**

过于急功近利 
错误的时间节点


### 研发

除了[错误的工程实践](#错误的工程实践)中提到的内容，可能还包括：
- **部分研发人员的工作态度有问题，自驱力不够。** 这是在我负责这个小组一段时间之后体会到的，自己研发质量较差而不自知的同时还因为态度问题与合作方起了比较大的冲突。同时平时沟通中也感觉在挤牙膏，处理线上问题不够积极等等。起初我考虑到可能是刚换了团队大家有情绪造成的，但时间久了之后发现并非如此，而且其他一并合并过来的小伙伴合作都还算顺畅。类似这样的研发人员在我看来应该在团队补充了新鲜血液之后**在适当的时间直接fire掉**。
- 


一个人总能从别人身上找到很多的缺点，宽于律己严于律人是人的天性。没一个工程师不写bug，线上故障总是无法避免的。或许我们在一个没有什么线上故障的团队中也能发现很多上面提到的问题，从而推导出我们不应该在某些方面过于苛责。**但所有的所有，都归咎于连续出了重大的S级线上故障，那么说什么都是错的，效果就是负的。** 

LOL职业圈流传着这样一句话：

> 输的时候，你说什么都像是借口

![loser](https://linnaname.github.io/img/blog/2022-06-20-01.jpeg)

或许这样说过于功利，但现实总是比文字所描述的要现实得多。


于 2022-06-20 01:40 AM