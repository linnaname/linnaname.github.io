

工具永远只是解决方案中的一个小小组件，用来链接日益庞杂的软件、人和海量的数据。

实现细节永远只是短暂存在的，但是文档化的设计过程却是无价之宝。


软件工程有的时候和养孩子类似：虽然生育的过程是痛苦和困难的，但是养育孩子成人的过程才是真正需要花费绝大部分精力的地方。

有统计显示，一个软件系统的40%～90% 的花销其实是花在开发建设完成之后不断维护过程中的。

靠性应该是任何产品设计中最基本的概念：任何一个系统如果没有人能够稳定地使用，就没有存在的意义。

但是，SRE并不是无止境地追求完美：当一个系统已经 “足够可靠”的时候，SRE 通常将精力转而投入到研发新的功能和创造新的产品中。



Margaret 曾经说过：“无论对一个软件系统运行原理掌握得多么彻底，也不能阻止人犯意外错误。”  Margaret Hamilton,MIT 教授，参与了阿波罗登月计划的软件开发工作。


不能将碰运气当成战略。


### 系统管理员模式
- 直接成本
- 间接成本


### Google的解决之道：SRE

Google的经验法则是，SRE团队必须将50%的精力花在真实的开发工作上。

只有管理层主动维护每个SRE团队的工作平衡，我们才能保障他们有足够的时间和精力去进行真正有创造性的、自主的研发工作，同时，这也保障了SRE团队有足够的运维经验，从而让他们设计出切实解决问题的系统。

我们可以认为DevOps是SRE核心理念的普适版，可以用于更广范围内的组织结构、管理结构和人员安排。同时，SRE是DevOps模型在Google的具体实践，带有一些特别的扩展。


### SRE 方法论

一般来说，SRE团队要承担以下几类职责：可用性改进，延迟优化，性能优化，效率优化，变更管理，监控，紧急事务处理以及容量规划与管理。

- 确保长期关注研发工作。在实践中，SRE管理人员应该经常度量团队成员的时间分配，如果有必要的话，采取一些暂时性措施将过多的运维压力转移回开发团队处理。只有整个产品部门都认同这个模式，认同50%的安全线的重要性，才会共同努力避免这种情况的发生。

SRE 处理运维工作的一项准则是：在每8～12小时的on-call 轮值期间最多只处理两个紧急事件。这个准则保证了on-call工程师有足够的时间跟进紧急事件，这样SRE可以正确地处理故障、恢复服务，并且要撰写一份事后报告。

所有的产品事故都应该有对应的事后总结，无论有没有触发警报。


- 在保障服务SLO的前提下最大化迭代速度
错误预算”起源于这样一个理念：任何产品都不是，也不应该做到100% 可靠（显然这并不适用于心脏起搏器和防抱死刹车系统等）


- 监控系统
alert
ticket
logging

- 应急事件处理
可靠性是MTTF（平均失败时间）和MTTR（平均恢复时间）的函数（参见文献[Sch15]）
通过事先预案并且将最佳方法记录在“运维手册（playbook）”上通常可以使MTTR 降低3倍以上。初期几个万能的工程师的确可以解决生产问题，但是长久看来一个手持“运维宝典”经过多次演习的on-call工程师才是正确之路。

- 变更管理
RE的经验告诉我们，大概 70% 的生产事故由某种部署的变更而触发。

变更管理的最佳实践是使用自动化来完成以下几个项目：
- 采用渐进式发布机制。
- 迅速而准确地检测到问题的发生。
- 当出现问题时，安全迅速地回退改动。



- 需求预测和容量规划
 必须有一个准确的自然增长需求预测模型，需求预测的时间应该超过资源获取的时间。● 规划中必须有准确的非自然增长的需求来源的统计。● 必须有周期性压力测试，以便准确地将系统原始资源信息与业务容量对应起来。

 - 资源部署

 - 效率与性能


 ## Google 生产环境：SRE视角



 # 指导思想

 监控系统都是运维生产环境必不可少的组件。如果没有针对服务的监控，就无从得知目前服务的状态，如果不知道服务的状态，就无从谈起维护服务的可靠性。

 发布工作是整体系统稳定性的一个关键环节，因为大部分故障都是由于新的变更引起的。在这方面的投入也可以保障每次发布的顺利进行。

 广义软件工程中（不仅仅是运维部分）的一个关键思想是保持简单。



反感那些不顾公司现状一上来就想要做研发效能度量的人，几个人的公司没必要
 长时间对研发效能业务投入
完善研发效能工具链建设
做好研发效能度量

度量有成本，而且不低
当指标变成目标后，它就不再是好的指标
指标最终都会被玩弄
改进不应「唯数字论」





## 事后总结：从失败中学习


### 理念

学习是避免失败最好的办法


发生事故总是难以避免的

随着系统的规范和复杂度的增加，故障可能就会成倍增加。


最重要的：确保实施有效的措施使得未来重现的几率和影响得到降低。

事故故障报告不是一种惩罚措施而是团队学习的一次机会。

什么情况下应该写故障报告
- 用户可见的宕机时间或者服务质量降低成都达到一定标准
- 问题解决耗时超过一定限制
- 用户数据遗失


对事不对人。如果因为某些错误的举动就公开指责或者羞辱某人或团队，那么人们就自然地逃避事后总结。
提供建设性意见。

### 协作和知识共享

- 实时协作：及时通知相关方，事故故障报告的编辑公开。
- 开放的评论系统：所有人都可以评论

报告 review 之后同步给外部。所有的故障报告都需要评审。


### 建立事后总结文化

需要团队管理层的努力

对于积极响应故障的工程师给予激励


### 确保改进措施得到实施