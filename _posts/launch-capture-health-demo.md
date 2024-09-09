元旦回家，看到我妈每天都量血压并且会用一个小本子记下来，和我妈谈到要不要给她买一个可以上传血压记录的血压计，她问是不是很贵，**最后买了一个可以蓝牙连接并上传数据的血压计**。过后脑子就在想是不是可以做一个 Demo 来拍下每次量血压的照片，然后自动识别记录血压、脉搏，这样就不用纸本子手写记录了。

于是元旦期间就把这个 Demo 撸了出来,算是非常有意思的一次编码。 Demo 下载[传送门](https://lambent-dodol-d33311.netlify.app)。

### 需求整理

- 对血压计拍照后能够自动识别出血压、脉搏
- 用户可以修改识别后的血压、脉搏
- 提供日、周维度的血压、脉搏变化曲线
- 可以本地导出血压、脉搏的历史数据(CSV 格式)

### 关键问题

这个 Demo 的关键在于**如何识别照片中的血压**，分别尝试了 OCR、ChatGPT 、 OCR + ChatGPT 以及一众国内的大模型之后，我特意在 V2EX 上[发了个主题](https://v2ex.com/t/1005207),得到了一些非常友善的回复。**猜猜为什么我要这样做，哈哈！**

经过一些小小的尝试之后，发现市面上的 OCR 云服务对这类场景的支持度都还差距不大，只是返回结果非常繁杂不好提取。于是，最终的决定采用： OCR 识别血压图片 + ChatGPT 提取结果的方式。当然不嫌麻烦也可以用正则提取结果替换掉 ChatGPT。

- OCR：用的百度 OCR 服务免费的开发者额度。
- ChatGPT API: OpenAI 官方的价格比较贵，我用的是一个[中转服务](https://www.openai-hk.com/docs/getting-started.html)。比较便宜！

### 编码

#### Android

多年之前撸过《第一行代码：Android》，已经忘的差不多了，基本属于未入门的水平。好在借助强大的 ChatGPT 和 Google 还是能够做做 Demo 的。

除了 Android 自带的常用组件外，以下是一些额外用到的工具：

- OkHttp:网络请求工具
- [Room](https://developer.android.com/training/data-storage/room): 本地数据持久化 [SQLite](https://www.sqlite.org/index.html) ORM, Google 出的
- [mpandroidchart](https://weeklycoding.com/mpandroidchart-documentation/getting-started)：画曲线

由于熟练度的问题，这部分确实花了我两天多的时间 ！！！

#### 后端

需要后端的功能包括：

- 上传图片至 OCR 服务，获取图片识别结果。
- 将图片识别结果 post 给 ChatGPT API，要求其返回血压、脉搏数据，然后返回给客户端。

鉴于功能实在足够简单，我用了 Golang, 并用了 [Echo](https://echo.labstack.com) 作为 Web 框架。代码托管在 Gitlab 上， CI/CD 部署到我在 [Vultr](https://vultr.com) 的 K8S 集群上。后端 API 域名是我开发 side project 经常用的二级子域名。 Gitlab CI/CD 以及 K8S、后端 API 域名这些都是之前的沉淀。

后端的编码、部署一套流程下来花了几个小时也就都搞定了。

### 效果

拍照识别的成功率并不高，但是感觉暂时够用了（暂时没有那么多时间去调试了）。

- 拍照识别 ![ ](https://lambent-dodol-d33311.netlify.app/assets/images/screenshots/IMG_20240106_093454.jpg)

- 分析曲线 ![ ](https://lambent-dodol-d33311.netlify.app/assets/images/screenshots/IMG_20240106_093547.jpg)

- 设置：开启本地持久化储存以及数据导出 ![ ](https://lambent-dodol-d33311.netlify.app/assets/images/screenshots/IMG_20240106_100518.jpg)

### 上架

#### Landing Web Page

介绍页使用了 Github 上开源的一个模版 [Mobile-app-landingpage-template](https://github.com/sandoche/Mobile-app-landingpage-template)，然后将其部署在 [Netlify](http://www.netlify.com) 上。Netlify 会提供一个随机分配的域名以及免费的 Let's Encrypt 证书。非常的棒！

#### ProductHunt

为了体验 ProductHunt 的发布功能，我在 ProductHunt 上做了 post。 [链接](https://www.producthunt.com/posts/capturehealth)。

### 推广

因此还是个玩具暂时没有做推广，等到第二个版本的时候再尝试一下 V2ex 以及小红书。

### 其它

**直接下载安装包**:为了方便在网页上直接下载 apk 包安装，我使用了 [mediafire](mediafire.com) 。免费！这样就可以直接在 [Landing Page](https://lambent-dodol-d33311.netlify.app) 页面上直接点击下载了。

**隐私协议**：在 Web Landing Page 和 Google Play 应用上架的时候都会用到。我使用了 [freeprivacypolicy](https://www.freeprivacypolicy.com) 这个网站工具，只需要做一些选项就可以生成一份协议。比如为 CaptureHealth [生成的](https://www.freeprivacypolicy.com/live/e28e7b8d-90a1-480e-9fc9-243bb6112998)。

## 接下来

这个 Demo 暂时应该暂时不会做大的更新了，但希望之后有时间了可以做的一些事情

- 识别成功不稳定，这是核心功能，继续改进。
- UI 太丑、用户体验太差了，需要改进。
- 增加一些之前减肥过程中[想要的一些功能](https://v2ex.com/t/977697#reply0)。
- 完成 Google Play 上架。

回过头来看，也**不禁感叹海外开发者和国内开发者在 launch 产品的难易程度简直天差地别**。
