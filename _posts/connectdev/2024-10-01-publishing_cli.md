---
layout: post
title: 如何发布一个命令行工具
subtitle: 自动化
date: 2024-10-01
author: Lnn
header-img: img/home-bg-art.jpg
catalog: true
tags:
  - CLI
  - 命令行
  - Command Line Tool
  - 自动化
  - Github Action
---

之前开发了命令行工具,这里总结一下如何发布一个命令行工具。

## 技术栈

这次命令行工具开发使用的 Python 技术栈，回头来看或许使用 go 是个更好的选择，但**人生苦短，我用 Python**。

我使用 [Typer](https://typer.tiangolo.com) 来提高开发命令行工具的效率，引入 [pytest](https://docs.pytest.org/en/stable/#) 做单元测试。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_02.png)

另外如果你的团队在考虑引入集成测试， pytest 将会是一个不错的选择，之前我在 XDSDK 团队的服务端大量引入了 pytest，使得登录、内购支付系统的稳定性有了不小的提升。
![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_01.png)

## 支持多种安装方式

#### PyPI

为了让用户可以通过 `pip install xxx` 轻松的安装，可以把工具发布到 PyPI。具体的操作流程参考官方的文档 [Python Packaging User Guide](https://packaging.python.org/en/latest/tutorials/packaging-projects)。大致流程是：

- 注册 PyPI 账号（分别有[测试环境](https://test.pypi.org)和[正式环境](https://pypi.org)的）
- 完善 setup.py
- `python setup.py sdist bdist_wheel` 本地打包
- 安装 twine 以及 twine upload 包到测试环境或者正式环境

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_03.png)

这种方式是不需要使用 PyInstaller 打包的。

#### 多平台支持

使用 [PyInstaller](https://pyinstaller.org/en/v6.11.1/index.html) 来打二进制包，使得用户可以不安装 Python 即可安装使用该命令行工具。

大体流程是：

- `pip install pyinstaller`
- 完善 xxx.spec 文件
- `pyinstaller xxx.spec`

本地执行会在 dist 目录生成命令行工具，可以先进行本地测试。

为了兼容各个架构平台，是需要在不同的操作系统上分别构建进行交叉编译的，我把这个过程放在了 Github Action 中，具体可以看 `自动化` 一节。

#### Homebrew

在 Mac 下最好还是能够支持通过 Homebrew 安装，大致流程是：

- 创建一个新的 GitHub 仓库 homebrew-tap
- 在该仓库中创建 Formula 目录
- 在 Formula 目录下创建 xxx.rb 文件，内容具体可以参考 [Taps (Third-Party Repositories)](https://docs.brew.sh/Taps)，这里会需要用到自动化流程打出来的 release 包。
- 当然这里还可以更进一步，把 release 包地址的更新过程也放在 Github Actions 内完成。

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_04.png)

之后用户就可以通过：

- `brew tap yourusername/xxx`
- `brew install xxx`

来完成安装了。

## 自动化

单元测试、构建、打包、上传等动作，除了自己动手之外，也可以用 [Github Actions](https://docs.github.com/en/actions) 来完成，**提高工作和摸鱼效率**。

设置交叉编译

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_05.png)

把发布到 PyPI 的流程也自动化掉

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_06.png)

大致流程是：

- 创建 release 以及打标签
- 设置 Python 环境
- 缓存依赖项（pip 包和 pytest 缓存）
- 安装依赖
- 运行测试
- 使用 PyInstaller 构建可执行文件
- 生成校验和（SHA256）
- 打包文件（Windows 用 zip，其他用 tar.gz）
- 上传构建产物,校验和文件到 release,自动发布到 PyPI

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_08.png)

release 是手动先创建的，Github Actions 内会把创建的包更新到当前创建的 release 上。
![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image_09.png)

## Github Action 本地调试

调试 Github Action 是一个比较麻烦的事情，有时候需要反复的 PR commit 去试试，为了提高**一点点** 效率。可以考虑使用 [nektos/act](https://github.com/nektos/act),如果用的是 Gitlab 则可以尝试在本地安装 gitlab-runner 或者 gitlab-ci-local 来进行简单的测试。

Mac 下 `brew install act` 即可安装；Linux 下，则可以在命令行中输入 `curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash`。 act 是基于 Docker 的，使用之前必须安装 Docker。

`act` 主要适合测试基本的构建和测试流程，但不适合完整测试跨平台构建，完整的跨平台测试还是需要依赖 GitHub Actions。但也算是部分的提高效率了!

`act` 有两个重要的选项：

- -n：Dry run，用于校验语法，查看基本运行逻辑；
- -j：直接指定触发 Job；

![alt text](https://linnaname.github.io/img/blog/tech/connectdev/cli/image.png)

## 最后

至此，你可以把命令行工具的发布过程自动化了！

## Reference

- [Github Actions](https://docs.github.com/en/actions)
- [act Documentation](https://nektosact.com)
- [Taps (Third-Party Repositories)](https://docs.brew.sh/Taps)
