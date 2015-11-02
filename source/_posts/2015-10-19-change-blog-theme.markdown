---
layout: post
title: "更换一个个性化的主题风格"
date: 2015-10-19 16:14:46 +0800
comments: true
categories: 
---

## 1、准备
兵马未动，粮草先行，万事都是以准备工作开始的。前面我们简单介绍了如何搭建博客、写作和发表博客以及做一些配置上的修改。
不过有没有人跟我有一样的感受：这个Octopress默认的主题简直看不下去了？好吧，这种东西还是不要说出来的好，萝卜白菜，各有所爱。

如果是想和我一样来修改主题的，那么先告诉大家一个好地方咯，如下是一些第三方主题，我们可以从中选出自己满意的：

<!--more-->

`https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes`


## 2、地址

这个不用说太多吧，看中了之后就开始找下载地址了，我选中的主题是：**classic-martinb**

它的整个界面风格如下：

![这里有一幅图，可能加载比较慢而已，稍等！](https://raw.githubusercontent.com/martinbjeldbak/classic-martinb/master/classic-martinb.png)


这个主题的地址，如下：
[**https://github.com/martinbjeldbak/classic-martinb**](https://github.com/martinbjeldbak/classic-martinb)


## 3、安装
差点忘了，我们是要在命令行操作数据的，安装这个工作肯定也是放在命令行来咯。
在主题作者的博客中就有命令行的提示，我们直接抄过来，如下：

```
$ cd octopress
$ git submodule add git://github.com/martinbjeldbak/classic-martinb.git .themes/classic-martinb
$ rake install['classic-martinb']
$ rake generate
```
当我的命令行出现如下的信息，我觉得我应该是已经下载成功，开始安装：

```
Cloning into '.themes/classic-martinb'...
remote: Counting objects: 331, done.
remote: Total 331 (delta 0), reused 0 (delta 0), pack-reused 331
Receiving objects: 100% (331/331), 1.65 MiB | 67.00 KiB/s, done.
Resolving deltas: 100% (104/104), done.
Checking connectivity... done.
```

当我在命令行进行安装命令的时候，出现如下信息：

```
A theme is already installed, proceeding will overwrite existing files. Are you sure? [y/n]
```
我选择了y，也就是yes咯

## 4、预览

预览的命令之前已经介绍过了，为了避免无谓的提交数据到服务器，我们先在本地预览一下：

```
rake preview
```

打开浏览器，输入：**`http://localhost:4000`**，如果与我们预期的情况一致，那么输入如下命令，部署上线吧：

```
rake generate
rake deploy
```

## 5、提交
最后，比忘了提交文件，命令行复习一下：

```
git add .
git commit -m 'Change blog theme.'
git push origin source
```

