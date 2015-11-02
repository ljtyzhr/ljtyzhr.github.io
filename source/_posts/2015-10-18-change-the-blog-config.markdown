---
layout: post
title: "在Octopress中修改我们的博客配置"
date: 2015-10-18 17:14:14 +0800
comments: true
categories: 
---


## 1、准备工作

其实这里谈到的准备工作，十分简洁。我们的每一个命令，都是要进入到命令行（有时候也叫做终端）进行的。因为我们的博客使用了Octopress，所以我们需要在octopress目录下进行操作。

所以，命令行如下：

<!--more-->

```
cd octopress
```

## 2、_config.yml

从名字我们就知道这个是一份配置文件，它到底有一些什么内容呢，抄一部分如下：

```
url: http://yoursite.com  #这里改为你网站的域名
title: My Octopress Blog  #这里改为你想要的网站标题
subtitle: A blogging framework for hackers. #这里改为你的博客副标题
author: Your Name #这里改为博客作者的名字，也就是你的名字
simple_search: https://www.google.com/search #这是默认搜索引擎，可以先不管
description: #网站描述信息
```

如上** # **之后的解释，这里就不再过多的说明了，按照上面的意思进行修改即可。

## 3、链接格式

前面我们发布了两篇博客，不知道大家有没有觉得标题实在是太长了，尤其是日期，看起来感觉怪怪的。

比如，我的一篇文章的博客地址，是像下面这样的：

```
http://ljtyzhr.github.io/blog/2015/10/17/how-to-build-github-blog/
```
这样看起来层级会不会太多了，一般来说，我们的存储方式，只要是“**20151017**”就已经足够了，没有太多必要像这样“**2015/10/17/**”，也就是说，上面的形式，更改为如下方式：

```
http://ljtyzhr.github.io/blog/20151017/how-to-build-github-blog/
```

好的，既然知道如何更改，那么规矩就比较好定义了，还是在上文的配置文件中，我们可以看到如下的一段代码：

```
permalink: /blog/:year/:month/:day/:title/ #文章固定链接
```
简单修改一下，便可以达到我们的目的，如下：

```
permalink: /blog/:year:month:day/:title/
```
实际上也就是把日期之间的 "/" 去掉了而已。


## 4、日期格式

不知道大家有没有发现一个问题，在我们发布的博客左上角部分，有这样的一个日期标签`OCT 17TH, 2015 10:29 PM`，这个是我从自己的博客上抄写过来的。

既然是日期格式，我们在`_config.yml` 继续查找一下 **date** 这个关键字，会找到如下的一行代码：

```
date_format: "ordinal" #默认日期显示方式
```

如果我们想讲上文中的格式，修改成形如“2015 年 10 月 17 日”这样的格式，我们又当如何操作呢？如下，我们只需将`ordinal`修改一下即可：

```
date_format: "%Y 年%-m 月%-d 日" 
```






