---
layout:     post
title:      重读代码大全
subtitle:   每位工程师都应该读的书
date:       2022-07-10
author:     Lnn
header-img: img/home-bg-art.jpg
catalog: 	 true
tags:
    - 代码大全
    - 读书笔记
---

如果把这本书比喻成一只狗，那么它将用鼻子轻擦创建活动，尾巴扫过设计与测试，而同时向其它开发活动汪汪叫。

## 欢迎进入 Software Construction 世界

> 在正规性与随意性之间达到平衡是非常困难的。


![01-01](https://linnaname.github.io/img/reading/code-complete/01-01.png)

> Software Construction 主要包括编码和调试
> - Software Construction 是总体设计和系统测试之间承上启下的工作。

> - Software Construction 是唯一一项必不可少的工作，是开发软件的重要组成部分，是软件开发的核心工作。
> - 源代码，往往是软件的唯一精确描述，因为它总是最新的
> - 把主要精力集中于 Software Construction，可以极大地提高程序员的生产效率


<br>

## 利用隐喻对编程进行更深刻的理解

> 重大发现往往是从类比中产生的。通过把一个你所陌生的事物与你所熟知的事物比较，你会对它有进一步的认识，从而形成你对它的独到的深刻理解这种隐喻方法被称之为“模型化”。在科学发展史上，充满了利用类比而产生的发现。

> 科学史并不是由一系列从“错误”模型到“正确”模型开关组成的，而是逐渐由“坏的”模型变为“较好”的模型，从包含面较窄到包含面较宽，从覆盖领域较少到覆盖领域较多。


> 启发是一种帮助你寻求答案的技术。它的结果往往和运气有关，因为它只告诉你如何去找，而并未告诉你应该找到些什么。


> 如果有一套指令告诉你该如何解决程序中的问题，这当然会使编程变得很容易，而且结果也可以预测了。但是编程科学目前还没有那样发达，也许永远也不会。**编程中最富于挑战性的问题便是将问题概念化**，编程中许多错误往往都是概念性错误，因为每个程序在概念上都是独特的，所以创立一套可以指导每一个问题的规则是非常困难，甚至是不可能的。这样，从总体上知道该如何解决问题，便几乎和知道某一特定问题的答案一样重要了。

**note**: 这也是为什么我认为一个优秀的工程师并不总是那些仅仅技术厉害的程序员的原因，确定性总是能通过更多的人力去解决的，而不决定性往往决定事情的成败以及问题能否被顺利解决。


> 几乎有 50 ％的软件开发工作量是在软件最初发行之后才进行的（Lientz 和 Swanson，1980）。

> 一个优秀的工匠知道用什么样的工具干哪一样工作，而且知道该如何使用它们。程序员也是如此，关于编程你理解得越深入，你的工具箱里的工具也就越多，何时何地该如何运用它们的知识也就越多。

> 不要把最新的“面向对象设计技术”当作上帝赐予的法宝，它不过是一件在某些场合下有用，而在某些场合下又无用的技术。如果你拥有的唯一工具就是一把锤子，那么你就会把整个世界都当作一个钉子。

**note**: 这也提醒我们不要写入原教旨主义里，事情能得到推进在我看来是更重要的。


## Software Construction 的先决条件

###  先决条件重要性 
> A common denominator of programmers who build high-quality software is their use of high-quality practices. Such practices emphasize quality at the beginning, middle, and end of a project.

> 如果你只在一个计划即将结束时强调质量，那你注重的只是测试。当某些人一谈起软件质量时，他们首先想到的便是测试。然而，事实上测试只是全部质量控制策略的一部分。而且并不是最重要的部分。测试既不能消除在正确方向上的错误工作，也不能消除在错误方向上的正确工作的错误，这种错误必须在测试开始之前就清除掉，甚至在创建工作开始之前就要努力清除掉它们。

> The overarching goal of preparation is risk reduction: a good project planner clears major risks out of the way as early as possible so that the bulk of the project can proceed as smoothly as possible. By far the most common project risks in software development are poor requirements and poor project planning, thus preparation tends to focus on improving requirements and project plans


> - 一些程序员并不作准备工作，因为他们抵制不了立刻开始进行编码工作的渴望
> - 程序员不重视准备工作的另一个原因是管理人员往往不理解那些在创建先决条件上花费时
间的程序员

> 你可以另找一份工作。优秀的程序员是非常短缺的。可以找到更好的工作，干吗非要呆在一个很不开明的程序店里徒损生命呢？


### 需求分析先决条件 

> 充分进行需求分析是一个项目成功的关键，很可能比使用有效的创建技术还重要



在创建阶段如何对付需求变化 :
- 让每个人都知道由于变化需求所付出的代价
- 建立一套更改控制过程
- 用开发的方法来容纳变动
- 放弃项目


### 结构设计先决条件 
> 结构设计应该清晰地描述系统应付变动的策略。结构设计应该表明：设计中已经考虑到了可能的功能增强变动，而且，应该使最可能的变动同时也是最容易实现的变动。

> 数据守恒定律：每一个进入的数据都应该出去，或者与其它数据一道出去，如果它不出去，那它就没有必要进来。

**note**: 这个说法倒是第一次进入我的视野


**如果想开发一个高质量的软件，必须自始至终重视质量问题。在开始阶段强调质量往往比在最后强调质量更为有效。**

**note**: 必要的架构设计和设计评审、讨论是必要的

<br>

## 建立子程序的步骤

> 从程序设计语言（PDL）到编码的转换过程，几乎没有哪些程序员充分利用了这一过程所带来的方便。

**note**: 可能因为工作经历接触到的软件系统没有足够复杂，并没有做过这一步的设计。


## 高质量子程序特点

> 除了计算机本身之外，子程序可以说是计算机科学最重大的发明。子程序使得程序非常好读而且也非常容易理解，编程语言中的任何特性都不能和这一点相比。

> 子程序也是节省空间和提高性能的最好手段

### 生成子程序的原因

- 降低复杂性 使用子程序的最首要原因是为了降低程序的复杂性，可以使用子程序来隐含信息，从而使你不必再考虑这些信息。
- 限制了改动带来的影响。要把最可能改动的区域设计成最容易改动的区域。
- 隐含顺序。
- 改进性能。
- 进行集中控制
- 隐含数据结构
- 隐含全局变量
- 隐含指针操作
- 提高部分代码的可读性
- 提高可移植性
- 简化复杂的布尔测试
- 是出于模块化的考虑吗？绝不是

**note:** 最后这一点有点出乎我的意料...


### 子程序名称恰当 

- 对于过程的名字，可以用一个较强的动词带目标的形式
- 对于函数名字，可以使用返回值的描述
- 避免无意义或者模棱两可的动词
- 名字的长度要符合需要。研究表明，变量名称的最佳长度是 9 到 15 个字母，子程序往往比变量要复杂，因而其名字也要长些

###  强内聚性 

强调强相关性的目的是，每一个子程序只需作好一项工作，而不必过分考虑其它任务。

**可取的内聚性**
- 功能内聚性。功能内聚性是最强也是最好的一种内聚，当程序执行一项并且仅仅是一项工作时，就是这种内聚性。
- 顺序内聚性
- 通讯内聚性
- 临时内聚性

**不可取的内聚性**

如果一个子程序具有不良的内聚性，那最好重新创建一个较好的子程序，而
不要去试图修补它。


### 松散耦合性

**可接受的数据结构耦合的例子**：一个程序向另一个子程序传递变量 EmpRec，EmpRec 是一个结构化的变量，包括姓名、住址、生日等等五个方面的数据，而被调用的子程序则全部使用这五个域。

**不可取的数据结构耦合举例**：一个程序向另一个子程序传递同样的变量 EmpRec，但是，如果被调用的子程序只使用其中两个域，比如电话号码和生日。这虽然还是数据结构耦合，但却不是个很好的应用，如果把生日和电话号码作为简单变量来传递的话，将使联系更加灵活，而且会使它们之间的两个特定域真正联系的可见性更好。

**有问题的数据结构耦合的例子**：一个程序向另一个子程序传递变量 OfficeRec。OfficeRec 有 27 个域，而被调用的子程序使用其中 16 个，这也是数据结构耦合，但是，它是一个好的数据结构耦合吗？决不是。传递 OfficeRec 使得联系是大规模的，这个事实非常明显，而传递 16 个单独参数，则又再次非常拙劣地表明了这一点，如果被调用子程序仅使用其中的 6 到 7 个域，那么单个地传递它们是个好主意。这种情况下，可以进一步对 OfficeRec 进行结构化，以使得在被调用程序中用得到的 16 个域包含在一个或两个亚结构中。

![松耦合](https://linnaname.github.io/img/reading/code-complete/05-04.jpeg)

### 子程序的长度
![子程序长度](https://linnaname.github.io/img/reading/code-complete/05-05.jpeg)


### 防御性编程
![防御性编程](https://linnaname.github.io/img/reading/code-complete/05-06.jpeg)


- 使用断言
- 输入垃圾不一定输出垃圾
- 异常情况处理
- 预计改动
- 检查函数返回值


**对防错性编程提高警惕**

> 过多的防错性编程会带来它自身的问题，如果你对每一种可以察觉的参数传递，在每一个可以察觉的地方都进行检查，那么程序将变得臃肿而笨拙。考虑好需要在哪里预防错误，然后再使用防错性编程。

note: 假设我们有一个供外部调用的 `methodA`, 其内部有两个私有的 `methodB` 和 `methodC`，假设这两个私有函数的入参和共有函数是相同的，我们有必要在 `methodA` 的入参做好防御性编程，而在 `methodB` 和 `methodC` 做防御性编程的必要性却没那么高。


### 子程序参数

> 子程序间的接口往往是一个程序中最容易出错的部分

- 确保实际参数与形式参数匹配。（主要指变量类型）
- 按照输入一修改一输出的顺序排列参数
![列参数](https://linnaname.github.io/img/reading/code-complete/05-07.jpeg)
- 如果几个子程序今使用了相似的参数，应按照不变的顺序排到这些参数。
- 使用所有的参数 , 不使用就删掉它
- 把状态和“错误”变量放在最后
- 不要把子程序中的参教当作工作变量。如果你需要为全局计算的最后把最终值赋给全局变量，而不要把中间值赋给它。

![说明](https://linnaname.github.io/img/reading/code-complete/05-08.jpeg)

- 应该把一个子程序中的参数个数限制在 7 个左右


### 使用函数 

- 什么时侯使用函数，什么时侯使用过程
- 由函数带来的独特危险。使用函数产生了可能不恰当值的危险，这常常是函数有几条可能的路径，而其中一条路径又没有返回一个值时产生的。在建立一个函数时，应该在心中执行每一条路径，以确认函数在所有情况下都可以返回一个值。

note: 不要陷入教条主义



## 模块化设计

> 子程序是具有一定功能的，可以调用的函数或过程。 而模块则是指数据及作用于数据的子程序的集合。模块也可能是指，可以提供一系列互相联系功能的子程序集合，而这些子程序之间不一定有公共的数据。

> 模块化给维护性带来的好处要比给结构带来的好处多得多，它是提高维护性的最重要因素。


### 模块化：内聚性与耦合性

> 模块化设计的目标是使每个子程序都成为一个“黑盒子”，你知道进入盒子和从盒子里出来的是什么，却不知道里边发生什么。它的接口非常简单，功能明确，对任何一个特定的输入你都可以精确地预测它相应的输出结果。

> 一个模块应该提供一组相互联系的服务

> 降低子程序之间耦合性的重要措施之一，就是尽可能减少使用全局变量


### 信息隐蔽 

> 信息隐蔽是为数不多的几个在实践中无可辩驳地证明了自己价值的理论之一。研究发现，应用信息隐蔽进行设计的大型程序容易更改指数要比没采用这一技术的高 4 倍。同时，信息隐蔽也是结构化设计和面向对象设什的基础之一。在结构化设计中，黑盒子思
想便来源于信息隐蔽。在面向对象设计中，也是信息隐蔽引发了抽象化和封装化的设计思想。

> 与设计的其它方面一样，设计模块的接口也是一个逐渐的过程，如果接口在第一次是不正确的，可以再试几次直到它稳定下来；如果它稳定不下来，那么就需要重新设计它。


在你所从事的项目中，你可能与不计其数需要隐含的信息打交道，但是，其中只有几种是你要反复遇到的：
- 容易被改动的区域 : 对硬件有依赖的地方、输入输出、非标准语言特性、难以设计和实现的地方、状态变量、商业规则。
- 复杂的数据
- 复杂的逻辑
- 在编程语言层次上的操作


状态变量 :
- 不要使用逻辑型变量作为状态变量，应使用枚举型变量。赋予状态变量一种新状态是非常常见的，给枚举型变量赋一个新的类型只需要重新编译一次，而对于逻辑型变量则需要重新编写每行检查状态变量的代码，谁难谁易是很明显的。
- 使用存取子程序检查变量，而不要对其直接检查，通过检查存取子程序而不是状态变量，可以进行更复杂的状态测试。例如，如果想检查一个错误状态变量和一个当前函数状态变量，那么把测试隐含在子程序中来进行，要比用充斥着程序的复杂代码进行测试容易得多。

> 一般来说，在设计一组在程序语言语句层次上操作数据的子程序时，应该把对数据操作隐含在子程序组中，这样程序的其余部分就可能在比较抽象的层次上处理问题了

> 一个不易察觉的信息隐蔽障碍是交叉依赖。比如模块 A 中的某一部分调用了模块 B 中的一个子程序，而模块 B 中又有一部分调用了模块 A 中的子程序。应避免这种交叉依赖现象。因为只有在两者都已准备好的情况下，你才能测试其中的一个。当程序被覆盖时，必须使 A 和 B 同时驻留在内存中，才能避免系统失败


**误认为会损失性能**

信息隐蔽的最后一个障碍是在结构设计和编码两个层次上，都试图避免性能损失。事实上，在两个层次上你都不必担心这一点。在结构设计层次上，这种担心之所以不必要是因为，以信息隐蔽为目标进行结构设计，与以性能为目标进行结构设计是不矛盾的，只要你同时考虑到这两点，那么就可以同时达到这两个目标。更常见的担心是在编码层次上，这种担心主要是认为间接而不是直接地存取数据结构会带来运行时间上的损失，因为这样做附加了调用层次。当测试了系统的性能并在瓶颈问题上有所突破时，这种担心是不成熟的。为提高软件性能做准备的最好手段之一就是模块化设计，这样，在发现了更好的方案之后，不必改变系统其余部分，就可以对个别子程序进行优化。


### 建立模块的理由

以下是一些适合使用模块的域：
- 用户接口
- 对硬件有依赖的区域
- 输入与输出
- 操作系统依赖部分
- 数据管理
- 真实目标与抽象数据类型
- 可再使用的代码
- 互相联系的操作
- 可能发生变动的相互联系的操作


> 可以在任何语言中进行模块设计。如果所采用的语言不直接支持模块，可以用编程约定对其加以扩展，以达到某种程度的模块化。


## 高级结构设计 

### 软件设计引论

> “软件设计”一词的意思是指，把一个计算机程序的定义转变成可以运行程序的设计方法。设计是联系要求定义和编码与调试的活动的桥梁。 它是一个启发的过程而不是一个确定的过程，需要创造性和深刻的理解力。设计活动的绝大部分活动都是针对当前某特定项目进行的。

划分成子系统  -> 划分成模块 -> 划分成子程序 -> 子程序内部的设计 

### 结构化设计 

- 自顶向下分解
- 自底向上合成

这两种方法并不是互相矛盾的。设计是一个启发的过程，就是说没有一种百试不爽的设计方法，它总是一个尝试的过程。因此，在找到好方法之前，尽可以大胆尝试，可以用自顶向下工作一会儿，再用自底向上工作一会儿。设计也是一个逐次迭代逼近的过程。因此，你在第 n 次用自底向上方法学到的东西，将在第 n ＋ l 次用自顶向下方法设计时起到很大帮助作用。

note: 这样的结论非常接地气，在分析方式上不要陷入原教旨主义里。



### 面向对象 

- 抽象
- 封装：封装是对抽象不存在地方的补充。如果抽象对你说“你应该在较高层次上看一个对象”，而封装则会说“你只能在这个层次上看一个对象”。
- 层次结构和继承性（inheritance）
- 模块化
- 对象与类


伴随着某些设计方法的第三个要素，即强调应该只使用一种方法的思想，是非常有害的。没有一种方法囊括了设计系统所需的全部创造力和洞察力。强调使用一种方法将破坏设计中的思维过程。但是，设计方法的选择往往会成为一种宗教似的问题——你去参加了一个宗教复兴会议，听一些结构化设计的先知讲道，然后你回到自己的圣地在石碑上写下一些神圣的程序，从此以后，你不再允许自己进入非基督教的领域。你应该知道，软件工程不是宗教，不应该引入宗教的狂想性。


### 往返设计 
- 设计是一个复杂的过程 
- 设计是一个“险恶”的过程 
- 设计是一个启发的过程

> 要把任何设计方法都只当成一种工具。一种工具只对一种工作或者一种工作的某一部分才有效，其余的工具适合其它的工作，没有一种工具是万能的。因此，你往往要同时使用几种工具。

> 最重要的设计原则之一是不要死抱着一种方法不放


## 生成数据

 程序语言所赋予你的阐明自己对程序理解的最强有力的工具之一便是程序员定义的变量类型。它们可以使程序更容易阅读。

当引入数组或字符串时，最好定义一个命名常量来表示数组或字符串的长度，然后在类型定义中使用这个命名常量。


### 自建数据类型的准则
- 建立具有面向功能名称的类型
- 要避免使用含有已定义变量类型的名称。比如像 BigInteger 和 LongString 等指的是计算机数据而不是客观世界中实体的名称就应避免使用。建立自己的类型其最大优点是，可以在程序及其实现语言之间建立一个绝缘层，而指向程序语言类型的名称则会破坏这个绝缘层，使用已定义的类型不会带来任何优点。面向问题的名称可以增加易改进性，并且使数据说明成为自注释的。
- 不要对已定义类型重新定义


### 初始化数据的准则 

在编程中，最大的错误原因之一便是对数据不恰当的初始化。开发有效地避免初始化错误的技术，可以节约大量的调试时间。不恰当初始化产生的问题，是由某一变量带有你没有预料的初值引起的

如何避免初始化错误的一些准则：
- 检查输入参数的有效性
- 在使用变量的位置附近对其进行初始化
- 要特别注意计数器和累加器
- 查找需要重新进行初始化的地方
- 对命名常量只初始化一次，用可执行代码初始化变量
- 利用编译程序的警告信息
- 设置编译程序使其自动初始化所有变量
- 使用内存存取检查程序来查找无效的指针
- 在程序开始初始化工作内存



## 命名

- 命名时要考虑的最重要问题
- 面向问题 
- 最佳名称长度
- 变量名的作用域 

较长的名字适于较常使用的变量或全局变量。而较短的名字则适于局部变量或循环变量（1980）。但短名字会产生许多问题，有些程序员把避免使用它们作为防错性编程的准则。

许多程序中含有带有计算值的变量：totals，averages，maximums 等等。如果你用限定词诸如（Ttl，Sum，Avg 等）来改动变量，那要把它们放在最后。

一致性可以改善可读性并简化了维护

往往用 Count 来表示总数，而用 Index 来表示下标

应恰当使用反义词。使用关于反义词的命名约定可以帮助保持连续性，同时也可以提高可读性。像 first/last 这样一组反义词是很容易理解的，但 first/end 就有些让人摸不着头脑了


### 特定数据类型命名

- 循环变量命名：使循环体变长的一个常见原因是嵌套。因此，对于一个有多重嵌套的循环，最好给循环控
制变量以较长的名字以便改善其可读性。大多数有经验的程序员都避免用 i、j、k 这类的名字。
- 状态变量命名：用比 flag 更好的名称来命名变量，最好不用 flag 作为状态变量的名字。之所以要避免使用 flag 作为标志名称，是因为它不能告诉你关于这个标志的任何信息。
- 要警惕“临时”变量。通常，暂时保留某些值是完全必要的。但如果在你的程序中出现很
多临时变量的话，则说明你对它们在程序中作用和使用它们的目的还不清楚。
- 记住一些典型的逻辑变量名：Done/Error/Found/Success。。如果可能的话，可以用比 Success 更准确更具有表达力的名称来代替它，用这个新名称应可以精确地表达出到底是什么已成功地完成了。为清楚起见，最好用 Error 或 Status_OK 等来代替 Status；用 SourceFileAvailable 或 SourceFileFound 来代替 Source。
- 当使用枚举型变量时，可以通过使用相同的前缀或后缀表示某一类型的元素都是属于同一组的


### 匈牙利命名约定 

匈牙利命名主要包括三个部分：基本类型、一个或更多的前缀、一个限定词


### 短名称 