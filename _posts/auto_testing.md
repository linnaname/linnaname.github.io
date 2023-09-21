


## 

TDD、BDD


测试驱动开发的编程方式依赖于下面这个 短循环:先编写一个(失败的)测试，编写代码使测试通过，然后进行重构以保 证代码整洁。这个“测试、编码、重构”的循环应该在每个小时内都完成很多次。 这种良好的节奏感可使编程工作以更加高效、有条不紊的方式开展。

大多数程序员如何分配他们的时间，就会发现，他们编写代 码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些 时间花在设计上，但是，花费在调试上的时间是最多的。修复bug 通常是比较快的，但找出bug所在却是一场噩梦。当修复一个bug时，常常会引起 另一个bug，却在很久之后才会注意到它。那时，你又要花上大把时间去定位问题。

测试就是一个强大的bug侦测器，能够大大缩减查找bug所需的时 间。

 确保所有测试都完全自动化，让它们检查自己的测试结果。

 我对测试的积极性更高了。我不再等待每次迭代结尾时再
增加测试，而是只要写好一点功能，就立即添加它们。每天我都会添加一些新功
能，同时也添加相应的测试。这样，我很少花超过几分钟的时间来追查回归错
误。

## 渐进改进


先有第一个自动化测试用例 -> 先有覆盖几个登录、支付核心接口 -> 全面覆盖登录、支付核心接口 -> 覆盖所有核心接口这样的过程，并且我们并不在是更多采用单元测试和采用集成测试上纠结，而是寻求根据实际情况逐步调整的过程。并且最重要的是能够**自动化**。


任何测试都不 能证明一个程序没有bug。确实如此，但这并不影响“测试可以提高编程速度”。

当测试数量达到一定程度之后， 继续增加测试带来的边际效用会递减;如果试图编写太多测试，你也可能因为工 作量太大而气馁，最后什么都写不成。你应该把测试集中在可能出错的地方。观 察代码，看哪儿变得复杂;观察函数，思考哪些地方可能出错。

不要因为测试无法捕捉所有的bug就不写测试，因为测试的确可以捕 捉到大多数bug。

## 改变是很困难的
> Changing the testing culture in organizations  takes time.
