---
layout: post
title: "使用Octopress在Github上搭建博客系统"
date: 2015-10-17 18:48:56 +0800
comments: true
categories: 
---


## 1、homebrew

```ruby
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

其间会有提示：

```
Press RETURN to continue or any other key to abort
```

所以按 return 键开始进行下载安装；下载成功的提示如下：

```
==> Installation successful!
==> Next steps
Run `brew help` to get started
```

表示安装成功！


## 2、安装ruby

安装ruby的过程相对容易，输入下列命令：

```
brew install rbenv
```
有的教程还有更多的命令，实际上现在已经全部安装完成了，我们并不需要再敲入更多的命令了，可以使用如下命令进行一定的检测，如下：

```
ruby -v
```
我们会在终端看到ruby的版本信息。

<!--more-->

## 3、octopress

### 3.1 克隆项目

执行命令如下：

```
git clone git://github.com/imathis/octopress.git octopress
```

然后进入octopress：

```
cd octopress
```


### 3.2 安装依赖

安装依赖的命令行如下：

```
gem install bundler
rbenv rehash    # If you use rbenv, rehash to be able to run the bundle command
bundle install
```

安装bundler出错，提示信息如下：

```
ERROR:  Could not find a valid gem 'bundler' (>= 0), here is why:
      Unable to download data from https://rubygems.org/ - Errno::ETIMEDOUT: Operation timed out - connect(2) (https://rubygems.org/latest_specs.4.8.gz)
ERROR:  Possible alternatives: bundler
```

这里是因为我们连接不上国外的网站。。。。好吧，幸好国内还有淘宝的镜像地址可以使用：[点击跳转](https://ruby.taobao.org)

使用方式如下：

```
$ gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/
$ gem sources -l
*** CURRENT SOURCES ***

https://ruby.taobao.org
# 请确保只有 ruby.taobao.org
$ gem install rails
```

如果你使用 Gemfile 和 Bundle (例如：Rails 项目)

你可以用 Bundler 的 Gem 源代码镜像命令。

```
$ bundle config mirror.https://rubygems.org https://ruby.taobao.org
```
这样你不用改你的 Gemfile 的 source。

修改 RVM ，改用本站作为下载源， 提高安装速度。如下，是mac上的修改方法：

```
$ sed -i .bak 's!cache.ruby-lang.org/pub/ruby!ruby.taobao.org/mirrors/ruby!' $rvm_path/config/db
```


如果遇到如下的提示信息：
> You don't have write permissions

添加 **sudo** 这样的命令

### 3.3 安装Octopress

安装Octopress应该不是什么大问题，如下：

```
git clone git://github.com/imathis/octopress.git octopress

cd octopress
gem install bundler
rbenv rehash
bundle install
rake install
```


## 4、部署到Github

### 预览
部署前可以在本地预览，输入

```
rake preview
```

之后在浏览器输入`http://localhost:4000/`来访问

### 新建仓库

利用octopress的一个配置rake任务来自动配置上面创建的仓库：可以让我们方便的部署GitHub page。在终端输入如下命令：

rake setup_github_pages
弹出之后输入git@github.com:your_username/your_username.github.com.git不要用提示的io，我的是git@github.com/sgxiang/sgxiang.github.com.git

输入以下命令部署博客

```
rake generate
rake deploy
```

### 提交文件

博客的source需要单独提交，执行如下命令就可以将source提交到仓库的source分支下：
```
git add .
git commit -m 'Initial source commit'
git push origin source
```

## 5、注意

Octopress 其实为你建立了 2 个分支。
> 一个是 master 分支，用于存放生成的最终网页。另一个是 source 分支，用于存放最初的原始 markdown 文件。

> 平时写作和提交都在 source 分支下，当需要发布时，rake deploy 命令会将内容生成到 public 这个目录，然后将这个目录的内容当作 master 分支的内容同步到 github 




