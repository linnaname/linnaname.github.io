---
layout: post
title: 也写点前端
subtitle: 哪个程序员没写过几行 JS 呢
date: 2024-09-11
author: Lnn
header-img: img/home-bg-art.jpg
catalog: true
tags:
  - 前端
  - React
  - JavaScript
---

## 前言

在前司，出于前端工程师的紧缺，为了加快需求的推进，往往我自己也会承担一小部分在管理后台的前端开发工作。阿里“毕业”的后端工程师，应该都多多少少接触过类似 [ice](https://v3.ice.work) 这样的框架，并在无数个被前端拒绝的后台类需求里挣扎在前端代码里面。而平常的 side project 一般也都是自己来动手写前端。这里总结一下最近一年来写前端的一些乱七八糟的东西。

## 工具

### TypeScript

[TypeScript](https://www.typescriptlang.org) 可以说是**让前端开发更能让人接受了**，或者说是重新创造了一遍 JavaScript。 Structural type system，支持泛型、类型检查等无疑给工程实践和维护上带来了巨大的益处。而且 TypeScript 的入门成本可以说非低，即使你只有一点点 JavaScript 基础也很容易上手。

### React

Library 方面则使用选择了 [React](https://react.dev)。React 的学习成本真的非常低，除了 JSX，其它都是原生的 ES 的概念。而 VUE 谈不上难，却也是引入一些有别于 ES 的新概念。比如渲染列表，React 中只需要纯粹的 ES 方法 map，而 VUE 则需要理解 v-for 的新概念。当你使用 map 的时候它非常**符合直觉**，比如很多其他的编程语言都支持类似的操作，而当你看到 v-for 的时候并不符合直觉, 甚至你会想为什么不是 a-for/vfor 偏偏是 v-for 呢？

并且 React 对于我这类偶尔写前端的一个好处:**需要记住的东西非常少**。除了少数几个 hook 以及 API 基本上都**不需要记**，只需要写 TypeScript 就可以了。

提到 hook， 2019 年 React 正式引入了 hook 功能。使得 function 组件也像 class 组件一样能维护状态，并且所有的组件都可以写成函数的形式，比起原有的以 class 的多个方法来维护组件生命周期的方式，简化了代码，你看又少记几个生命周期方法。不过有了 hook 之后 function 也可以有状态了，如果不仔细了解实现机制的话，很容易导致一些奇怪的 bug。State Management 我选择了 [zustand](https://github.com/pmndrs/zustand)，它真的非常符合官方的描述：**small, fast and scalable bearbones state-management solution**。

### react-bootstrap

组件库我选了 [react-bootstrap](https://react-bootstrap.github.io/),对于小型项目可以说非常方便了。

## 复用

**不管是前端还是后端，为了提高维护性，我觉得有一点是不变：组件化**。单一职责原则、高内聚，低耦合这些在后端非常基本的概念，用在前端也是一样的。提高可维护性的同时，每个组件也可以单独测试，确保其功能正确。

我把可复用的放在了 component 目录，pages 则是具体的页面。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_01.png)

当然我并不是一个专业的前端工程师，欢迎大家的建议！

为了更方便地在项目里 axios 我还对它进行了一点小小的封装。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_05.png)

## 测试

测试可以使用 [JEST](https://jestjs.io)。为了更快地生成测试用例，我使用了 [Jest Test Gen](https://marketplace.visualstudio.com/items?itemName=com-egm0121.vs-jest-test-gen) 这个插件。

vscode-jest 和 Jest Runner 等可以非常方便在编辑器内运行这些测试。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_01.png)

当然 `npm test` 也非常方便。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image.png)

## 部署

使用 Docker 通过 Gitlab CI/CD 部署到 Kubernetes 也非常方便

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_02.png)

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/fontend/image_03.png)

## 前端的快速发展

> 一分钟之内会发生什么事情？Netflix 观看时间增长 70,000 小时；Snapchat 上有三百万视频被观看；Google 新增两百四十万次搜索；一个 JS 新框架被发明 （这条不是真的!)

这是我以前看到的一则关于前端快速发展的”笑话“,虽有点讥讽的意思，但是也从侧面看出来前端发展之快。

2014 年左右我第一次接触 JavaScript,当时还是 jQuery 大行其道的时候。当时我用 HTML5 的新特性 Canvas 做了一个 Doodle 网站，用户可以在上面自由的画一些有趣的东西，并增加各种各样类似于现在相机里的滤镜效果。当时写前端还是一件比较”痛苦“的事情，也是我后来放弃走前端方向的原因之一。不过有趣的是，凭着那时候做的 Doodle 网站，次年我在腾讯的实习招聘二面中把这个网站现场打开给面试官看，然后大部分面试时间都在和面试官聊这个网站具体的实现细节，最后顺利拿到了实习机会。

但 2024 年的今天，前端已经发展到和 10 年前大一样了！类型系统、工程化等等，甚至似乎真的每天都有新的东西冒出来，让人目不暇接。
