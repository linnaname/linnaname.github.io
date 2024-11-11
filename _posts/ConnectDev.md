## 简要

ShowMaker 是一个 Serverless 后端程序托管平台，开发者可以将 Web 应用（例如一个网站），或者 Node.js、Python、Go 等语言的后端程序（例如一个 RESTful API 服务器）部署到 ShowMaker 上面，ShowMaker 会自动从源代码构建出可运行的「版本」，然后将它运行在独立的容器。

如果说要找一个国外的参考，是希望做类似 [modal](https://modal.com) 的平台，给开发者(特别是 AI 领域的开发者)在 web endpoint, batch jobs, job queues 提供好用的平台。

而在 ShowMaker 关闭之日，web endpoint 得到了支持，job queues 正在开发中。

## 后端

`engine` 基于 Docker 从源代码构建出可运行的镜像，然后将它运行在独立的容器中，子域名分配、日志管理，支持 Python、Golang 多种 Runtime。Node.js 技术栈。

[OpenResty](https://openresty.org) 自动给用户分配一个「二级域名」，后继也可以增加自定义域名绑定。

`client` 负责登录、账号、鉴权、应用管理等。
Golang 技术栈

- [Gin Web Framework](https://gin-gonic.com/)
- [XORM](https://xorm.io/zh/)

为了尽快上线，接入了 [Auth0](https://auth0.com) 支持 `Github`、`Google` 登录。

`engine` 选择 `Node.js` 更多是负责开发 `engine` 的合作伙伴更熟悉它，而且 `engine` 本身主要是负责构建、部署等功能，性能并不敏感。
`client` 由我负责开发，因此选择了 `Golang`。

#### 域名和证书管理

前端 Nginx Ingress Controller 作为 [流量入口](https://docs.vultr.com/how-to-set-up-nginx-ingress-controller-with-ssl-on-vke)，使用 Ingress Controller 管理多个域名和子域名到后端、前端服务的映射以及 SSL 证书(Let’s Encrypt Certificates)。

比如：
llm.fun 产品主域名
api.llm.fun 后端接口正式域名
apitest.llm.fun 后端接口测试域名
console.llm.fun 控制台域名
主域名(llm.fun) CDN 加速使用 [Cloudflare](https://www.cloudflare.com)

doc.llm.fun 作为开发者**文档**域名， 单独部署在[Netlify](https://www.netlify.com)上，这样可以省下一些流量，而且 Netlify 对静态文件的加速比自己部署要更快。

#### CI CD

Gitlab

比如 console-fontend

test -> build -> deploy

test 阶段主要是 lint、type-check、unit test

build 阶段依赖 deployments/build-image，在 gitlab 的公共 builder 上，build 打标后 负责 docker login 和 push 到 gitlab 专属的镜像库上。

deploy 阶段依赖 deployments/deploy-kubernetes 将镜像部署到 kubernetes 集群上。

## 前端

#### 技术栈

TypeScript
[React](https://react.dev)  
NPM 工程依赖、构建管理
组件库 [React Bootstrap](https://react-bootstrap.github.io) 基本能满足中小型前端项目的需求。
单元测试 [jest](https://github.com/testing-library/jest-dom)

#### 核心目录

common 为常量定义、共用模型
component 为公用组件，比如 Footer(页尾)、Header（页头）、Page（分页器），这部分组件可以充分的复用在不同的页面。
config 环境（测试、正式）配置
pages 为具体的页面，比如 Login（登录）、Logout(登出)、ApplicationList（应用列表）等。
routes 路由配置，使用 [React-Router](https://reactrouter.com/en/main) 进行路由管理
services 后端接口封装，网络请求使用 [Axios](https://axios-http.com)
stores 状态管理、本地存储 状态管理使用 [zustand](https://github.com/pmndrs/zustand)
utils 比如网络请求工具二次封装

#### 如何部署

代码全部在 Gitlab 上

test -> build -> deploy

test 阶段主要是 lint、type-check、unit test

build 阶段依赖 deployments/build-image，在 gitlab 的公共 builder 上，build 打标后 负责 docker login 和 push 到 gitlab 专属的镜像库上。

deploy 阶段依赖 deployments/deploy-kubernetes 将镜像部署到 kubernetes 集群上。

#### 静态加速

CDN 加速使用 [Cloudflare](https://www.cloudflare.com)

之前在带 XDSDK 团队时，团队内只有一位全职的前端同事，TA 的精力也主要集中在支付、登录的 web 化上 以及部分核心管理后台功能上。一些零散的后台需求只能后端同事自己动手，带 XDSDK 团队这两年又把大学时学的那点前端又捡了起来。不得不说，几年过去之后前端不管是在语言特性还是工程化上都有了非常大的变化和进步。

## 文档

文档单独一个 repo ，单独部署在[Netlify](https://www.netlify.com)上自定义域名映射到 `doc.llm.fun`，这样可以省下一些流量，而且 Netlify 对静态文件的加速比自己部署要更快。

文档的工程管理使用 [Docusaurus](https://docusaurus.io)，只需要写 MarkDown 就可以。只有英文版本的。

关于技术文档工程化可以参考我之前写的 [《面向开发者的技术文档如何维护:技术文档工程化》](https://www.linnana.me/2023/09/28/writing-dev-doc)。

## showmaker-cli

[showmaker-cli](https://github.com/ishowmaker/showmaker-cli) 命令行工具是用来部署应用和进行其他管理操作的客户端工具。

编程语言上在 Python 和 Golang 上做了一些纠结，在构建 CLI application 上都是不错的选择。这两者平常工作中也都有使用，当然 Python 我们主要用于写集成测试，LeanCloud 的 RTM （即时通信、消息推送） 相关的集成测试都是用的 Python。

[Typer](https://typer.tiangolo.com) 它让构建 CLI applications 更加简单，

[pytest](https://docs.pytest.org/en/stable) 和 [pytest-mock](https://pytest-mock.readthedocs.io/en/latest/index.html) 这两个平时工作中就用来写集成测试，上手非常容易。

[PyInstaller](https://pyinstaller.org/en/stable)

利用 Github Action 进行自动单元测试、并用 PyInstaller 打出 Windows、MacOS、Linux 的适配可执行包，发布到 Github release。

当时选择了 Python，**但回过头来看，可能 Golang 或许是更好的选择。**

## 基础设施

#### 代码托管和部署

开发者直接使用 CLI 维护在 Github 之外，代码都托管在 [Gitlab](https://gitlab.com) 上。

使用 Gitlab 的公共 builder 机器，构建之后把镜像推送到 [Gitlab container registry](https://docs.gitlab.com/ee/user/packages/container_registry/#:~:text=You%20can%20use%20the%20integrated%20container%20registry%20to%20store%20container#:~:text=You%20can%20use%20the%20integrated%20container%20registry%20to%20store%20container)

通过在 K8S 上安装 [agent](https://docs.gitlab.com/ee/user/clusters/agent/install/),可以直接把镜像部署到 Kubernetes 集群上。

#### Kubernetes

Kubernetes 集群部署在 [Vultr](https://vultr.com)

#### Redis

部署在 Docker 内

#### MySQL

部署在 Docker 内

#### Prometheus

metrics 收集

## 技术总结

技术上杂但并不乱，开发上尽可能保持可复用、组件化。

从商业变现上看，毫无疑问这段时间的投入是**失败的**。如果硬要从中谈一点收获，就是前端、后端、运维等等都摸了一遍，小到一个 icon 的制作都需要自己动手，大到如何变现。既有的技术选型、技术能力也不是产品迭代的瓶颈，而是产品的类型决定的。

回过头来看，**自己去尝试商业变现或者说创业的过程其实是过去能力积累的体现**，而技术上的能力并不是瓶颈，缺乏的是从 0 到 1 的能力。
