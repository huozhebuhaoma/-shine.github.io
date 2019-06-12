
---
title: hexo搭建教程
date: 2019-06-04 22:41:21
tags: ["Hexo","教程"]
categories: "Hexo"
---
花了几天的时间在`GitHub`的`page`整了个博客，使用了`Hexo`来搭建。搞了那么久发现搭起来容易，想整的好看点，好吧，也很容易，不过步骤和内容有点多，这里就做了个整合当做备忘，也给看到的有缘人一点微不足道的帮助。

因为我用的是 window 其他系统没用过也不知道，就不误人子弟了，以下的内容都是基于 window 来说明的。
### Hexo搭建步骤
1. 安装Git
2. 安装Node.js
3. 安装Hexo
4. GitHub创建个人仓库
5. 生成SSH添加到GitHub
6. 将hexo部署到GitHub
7. 设置个人域名
8. 发布文章
#### 1.安装Git
在 GitHub 上搭建的，Git 肯定是必须的，即使不是在 GitHub 上搭建，Git 也是一个优秀的版本控制系统，用来管理自己的文件也是很好用的。

到git官网上下载 [Download git](https://gitforwindows.org/) 下载后会有一个 Git Bash 的命令行工具，以后就用这个工具来使用 Git，也可以下载 [TortoiseGit](https://tortoisegit.org/download/) 通过Git 客户端来使用 Git。
#### 2.安装Node.js
Hexo是基于nodeJS编写的，所以需要安装一下nodeJs和里面的npm工具。
[下载地址](https://nodejs.org/en/download/)下载后直接安装就好了,安装完后，打开命令，检查是否安装成功。
```
node -v
npm -v
```
#### 3.安装Hexo
可以在你创建`GitHub Pages`的 GitHub 项目下建一个分支方便把 Hexo 的代码也管理起来，之后换电脑后也方便转移。
![](https://raw.githubusercontent.com/windliang/windliang.github.io/hexo/source/_posts/hexo%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B/1.jpg)