

<a name="9nQim"></a>
#### 逻辑结构
![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604972675719-42d2788d-4e2e-44b8-9338-5e47ee72ddc0.png#align=left&display=inline&height=418&margin=%5Bobject%20Object%5D&name=image.png&originHeight=418&originWidth=1129&size=240524&status=done&style=none&width=1129)

<a name="p4ReG"></a>
#### 物理结构
![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604972710080-83474bf4-c7f1-4eeb-87ee-050ebf7f465b.png#align=left&display=inline&height=383&margin=%5Bobject%20Object%5D&name=image.png&originHeight=383&originWidth=915&size=251831&status=done&style=none&width=915)<br />每个文件的大小可以配置


<a name="G0Cnb"></a>
#### 进程结构

![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604972979551-90284713-4632-4c03-a6ce-130a7e4e0537.png#align=left&display=inline&height=186&margin=%5Bobject%20Object%5D&name=image.png&originHeight=186&originWidth=732&size=229576&status=done&style=none&width=732)

各个进程的工作关系<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604973111522-9b273c41-1d10-4620-ae3f-a141f98b1e7c.png#align=left&display=inline&height=542&margin=%5Bobject%20Object%5D&name=image.png&originHeight=542&originWidth=868&size=337847&status=done&style=none&width=868)

<a name="dH9ra"></a>
#### 系统表、系统视图
![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604973460809-cde7d58d-4eeb-47b8-90c2-450d252fa311.png#align=left&display=inline&height=611&margin=%5Bobject%20Object%5D&name=image.png&originHeight=611&originWidth=1138&size=766482&status=done&style=none&width=1138)<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604973694791-389f0220-2eb7-47ec-894f-c898119a91c6.png#align=left&display=inline&height=481&margin=%5Bobject%20Object%5D&name=image.png&originHeight=481&originWidth=926&size=360880&status=done&style=none&width=926)

比如支持的索引存储类型<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604973469851-dcbe0c71-85d7-4add-b8b0-3362bba6a71d.png#align=left&display=inline&height=190&margin=%5Bobject%20Object%5D&name=image.png&originHeight=190&originWidth=391&size=90497&status=done&style=none&width=391)

<a name="rB1Ha"></a>
#### 存储结构
![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974103018-755f5aed-8ad9-4c8f-8d10-0048a21934a4.png#align=left&display=inline&height=368&margin=%5Bobject%20Object%5D&name=image.png&originHeight=368&originWidth=736&size=150498&status=done&style=none&width=736)<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974147878-358d18e1-65e0-4da8-8be3-cc40950ad12a.png#align=left&display=inline&height=564&margin=%5Bobject%20Object%5D&name=image.png&originHeight=564&originWidth=886&size=449468&status=done&style=none&width=886)<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974288293-eae726ea-07c4-44ab-93b8-09b9062b54d8.png#align=left&display=inline&height=551&margin=%5Bobject%20Object%5D&name=image.png&originHeight=551&originWidth=914&size=610216&status=done&style=none&width=914)

<a name="wTEgo"></a>
#### 可靠性

**刷盘机制**<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974475809-e671e532-5a41-4e01-aeb6-9d09ca1094cb.png#align=left&display=inline&height=649&margin=%5Bobject%20Object%5D&name=image.png&originHeight=649&originWidth=884&size=324466&status=done&style=none&width=884)<br />根据业务情况来决定是不是要关闭掉write page，这跟RocketMQ、Kafka这类用了PageCache的中间做法都一样的。

**Checkpoint机制**

![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974701698-a5a7a7a8-75c8-4941-bbe4-ea52e239ffe0.png#align=left&display=inline&height=530&margin=%5Bobject%20Object%5D&name=image.png&originHeight=530&originWidth=902&size=443707&status=done&style=none&width=902)

![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604974787238-9e1979f5-f313-406a-9e1f-240c62016423.png#align=left&display=inline&height=580&margin=%5Bobject%20Object%5D&name=image.png&originHeight=580&originWidth=934&size=489734&status=done&style=none&width=934)<br />注意区分数据一致性和可靠性的区别


<a name="qHde2"></a>
#### 数据类型
只能说真的丰富<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/471305/1604976594236-3010bdc8-1832-4b60-a0a9-fba6a19fa563.png#align=left&display=inline&height=541&margin=%5Bobject%20Object%5D&name=image.png&originHeight=541&originWidth=903&size=247577&status=done&style=none&width=903)
