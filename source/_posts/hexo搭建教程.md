
---
title: hexo搭建教程
date: 2019-06-04 22:41:21
tags: ["Hexo","教程"]
categories: "Hexo"
---
花了几天的时间在`GitHub`的`page`整了个博客，使用了`Hexo`来搭建。搞了那么久发现搭起来容易，想整的好看点，好吧，也很容易，不过步骤和内容有点多，这里就做了个整合当做备忘，也给看到的有缘人一点点的帮助。

因为我用的是 window 其他系统没用过也不知道，所以以下的内容都是基于 window 来说明的。
### Hexo搭建步骤
1. GitHub创建个人仓库
2. 安装Git
3. 安装Node.js
4. 安装Hexo
5. 生成SSH添加到GitHub
6. 将hexo部署到GitHub
7. 发布文章

#### 1.GitHub创建个人仓库
首先，你先要有一个[GitHub](https://github.com)账户，去注册一个吧。

注册完登录后，在 GitHub.com 中看到一个`New repository`，新建仓库

创建一个和你用户名相同的仓库，后面加`.github.io`，只有这样，将来要部署到 GitHub page 的时候，才会被识别，也就是`xxx.github.io`，其中`xxx`就是你注册 GitHub 的用户名。

我这里是已经建过了，就是[windliang.github.io](https://windliang.github.io)。
![](https://raw.githubusercontent.com/windliang/windliang.github.io/hexo/source/_posts/hexo%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B/2.jpg)

#### 2.安装Git
在 GitHub 上搭建的，Git 肯定是必须的，即使不是在 GitHub 上搭建，Git 也是一个优秀的版本控制系统，用来管理自己的文件也是很好用的。

到git官网上下载 [Download git](https://gitforwindows.org/) 下载后会有一个 Git Bash 的命令行工具，以后就用这个工具来使用 Git，也可以下载 [TortoiseGit](https://tortoisegit.org/download/) 通过Git 客户端来使用 Git。
#### 3.安装Node.js
Hexo是基于nodeJS编写的，所以需要安装一下nodeJs和里面的npm工具。
[下载地址](https://nodejs.org/en/download/)下载后直接安装就好了,安装完后，打开命令，检查是否安装成功。
```
node -v
npm -v
```
#### 4.安装Hexo
可以在你创建`GitHub Pages`的 GitHub 项目下建一个分支方便把 Hexo 的代码也管理起来，之后换电脑后也方便转移。
下图创建了`hexo`分支来管理 Hexo 的源码，`master` 原来就有的，这个先不管，是后面运行起Hexo后保存编译后的代码的，是Hexo自动上传的。
![](https://raw.githubusercontent.com/windliang/windliang.github.io/hexo/source/_posts/hexo%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B/1.jpg)

把`hexo`分支导出到电脑，在这个文件夹下直接右键`git bash`打开,运行命令行，进行安装 Hexo。

```
npm install -g hexo-cli
```
运行命令行查看版本,至此就全部安装完了。
```
hexo -v
```
接下来初始化一下hexo。
```
hexo init
npm install
```
如果运行的是`hexo init xxx`就会在当前文件夹下创建一个名为`xxx`的文件夹。

新建完成后，指定文件夹目录下有：
* node_modules: 依赖包
* public：存放生成的页面
* scaffolds：生成文章的一些模板
* source：用来存放你的文章
* themes：主题
* ** _config.yml: 博客的配置文件**

输入
```
hexo g
hexo server
```
打开hexo的服务，在浏览器输入`localhost:4000`就可以看到你生成的博客了。
使用ctrl+c可以把服务关掉。
#### 5. 生成SSH添加到GitHub
回到`git bash`中，
```
git config --global user.name "windliang"
git config --global user.email "windliang@xx.com"
```
这里的`windliang`是我的 GitHub 用户名，windliang@xx.com输入登录 GitHub 的邮箱。这样 GitHub 才能知道你是不是对应它的账户。

可以用以下两条，检查一下你有没有输对
```
git config user.name
git config user.email
```
然后创建 SSH,一路回车
```
ssh-keygen -t rsa -C "windliang@xx.com"
```
这个时候它会告诉你已经生成了.ssh的文件夹。在你的电脑中找到这个文件夹，`C:\Users\你的电脑名\.ssh`。注意这是个隐藏的文件夹，需要在设置打开显示隐藏文件才能看到。

ssh，简单来讲，就是一个秘钥，其中，id_rsa 是你这台电脑的私人秘钥，不能给别人看的，id_rsa.pub 是公共秘钥，可以随便给别人看。把这个公钥放在 GitHub 上，这样当你链接 GitHub 自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过 git 上传你的文件到 GitHub 上。

而后在 GitHub 的 setting 中，找到 SSH keys 的设置选项，点击`New SSH key`把你的`id_rsa.pub`里面的信息复制进去。
![](https://raw.githubusercontent.com/windliang/windliang.github.io/hexo/source/_posts/hexo%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B/3.jpg)

在`git bash`中，查看是否成功。
```
ssh -T git@github.com
```
#### 6. 将hexo部署到GitHub
打开站点配置文件`_config.yml`，翻到最后，修改为
```
deploy:
type: git
repo: https://github.com/windliang/windliang.github.io.git
branch: master
```
接着安装`deploy-git` ，也就是部署的命令,这样才能用命令部署到 GitHub。
```
npm install hexo-deployer-git --save
```
然后使用下面 3 个命令，以后修改文章后也是运行这几个命令
```
hexo clean
hexo generate
hexo deploy
```
其中 `hexo clean`清除了你之前生成的东西，也可以不加。
`hexo generate`顾名思义，生成静态文章，可以用 `hexo g`缩写。
`hexo deploy`部署文章，可以用`hexo d`缩写。

然后就可以在`http://windliang.github.io`这个网站看到你的博客了！！
#### 7. 发布文章
使用下面的命令生成新的文章
```
hexo new newpapername
```
然后在`source/_post`中打开生成的`markdown`文件，就可以开始编辑了。当你写完的时候，再
```
hexo clean
hexo g
hexo d
```
刷新就可以看到文章了，有时候看不到可以清下缓存再刷新。