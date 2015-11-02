---
layout: post
title: "自己动手DIY一下Octopress的风格"
date: 2015-10-21 19:32:51 +0800
comments: true
categories: 
---


## 1、首页显示摘要

当我写了三四篇文章，并发布在博客上之后，我发现了一个问题，就是这些文章会很坑爹，它让我感到很不爽的一点就是我要找到一篇文章会很困难，在首页上，他会显示出我的整个文章，而不是显示摘要！！！

### 摘要

不能忍，看到很多博客上都会显示摘要，然后一个 **`更多`** 这样的按钮，点击之后跳转到博客的详情页面上去，那么我该怎么做呢？
<!--more-->
好吧，其实也很简单，就是在我们所写好的文章中，添加一个标签，这个标签前面的内容，会显示在首页上，标签后面的内容就不会再显示出来，而是被**`更多`**或者**`Read On`**所替代。标签如下：

> <!–- more -–>

注意一个问题，这个只是一个摘要标识符，可以在`_config.yml`中通过`excerpt_separator`参数指定。由于使用了HTML的注释的写法，在博客正文中不会出现摘要标识符，标识符前的内容会在博客正文中显示。

### 汉化

如果我们想要显示中文的提示**`更多`**而不是英文的**`Read On`**，那么我们可以修改`_config.yml`文件中的`excerpt_link`信息，如下：

```
excerpt_link: "Read on &rarr;" 
excerpt_link: "更多 &rarr;" 
```

## 2、右侧导航

### About

在目录`_include/custom/asides/`中创建一个文件，命名为`about.html`，内容如下：

```
<section>
  <p>This is my blogs.</a>!</p>
  <p>如果想了解关于我<a href="/about/">更多</a> 界面. 我的 Github 地址是 <a href="https://github.com/ljtyzhr">这里</a>.</p>
</section>
```

修改配置文件`_config.yml`，找到其中的`default_asides`，修改为：

```
default_asides: [asides/about.html, asides/recent_posts.html]
```

## 分类

我们看到首页的右手边，有两个 **Posts** 项目，这里，我们可以找到“index.html”文件进行查找，删除其中对post文件的引用即可，如下：

```
include asides/recent_posts.html
```

删除这一句之后，我们预览一下就可以看到，右手边的导航，只剩下一个最近目录。
