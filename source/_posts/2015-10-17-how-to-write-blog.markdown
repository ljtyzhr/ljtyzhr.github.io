---
layout: post
title: "如何使用Octopress写作和发布博客"
date: 2015-10-17 22:29:42 +0800
comments: true
categories: 
---

## 写博客

写博客，我们首先要建立一个文档，使用的命令如下：

 ```
 rake new_post["this is title"]
 ```
 
文章生成在目录下的`source/_posts`目录下，文章是markdown格式的，不熟悉该语法的同学可以去Google一下，这里不作太详细的解释。

输入如上的命令之后，我们可以在`octopress/source/_posts`目录中找到我们生成的文件。该文件以时间和标题命名，一般格式如：`yyyy-mm-dd-Post-Title.markdown`，当我们打开生成的文件的时候，可以看到文件的内容如下：
```
---
layout: post
title: "this is title"
date: 2015-10-17 21:59
comments: true
external-url:
categories:
---
```

在这里，我们看看上面的每一行都是什么意思：

- `layout` 暂时不要理会；
- `title` 是这篇文章显示在最终网页上的标题；
-  `date` 部分是详细的文件生成时间，如 2014-04-28 03:35:00；`comment` 部分表示是否允许评论，目前显示是允许，如果想关闭评论，请改为 false；
- `categories` 指这篇文章的分类目录，请在后面引号中输入，如果没有该目录，则会自动生成。请不要删除这段信息，在这段信息下面开始你的文章内容。


关于markdown的格式可以参考这篇文章：[http://wowubuntu.com/markdown/](http://wowubuntu.com/markdown/)

<!--more-->

使用Octopress写博客，主要掌握如下几个常用的命令就好：

- `rake new_post[‘article name’]` 生成博文框架，然后修改生成的文件即可
- `rake generate` 生成静态文件
- `rake watch` 检测文件变化，实时生成新内容
- `rake preview` 在本机 4000 端口生成访问内容
- `rake deploy` 发布文件



## 发布博客

发布博客相对来说比较简单，逻辑无非是，将写好的文档添加到git中去，然后使用命令将它推送到服务器，然后加载出来。
嗯，就是这么简单，命令行如下：

```
rake generate
git add .
git commit -am "I write a blog" 
git push origin source
rake deploy
```

发布博客还可以使用另一种命令，它只有一行，如下：

```
rake gen_deploy
```
这实际上就是 `generate` 和 `deploy` 的合体


**注意：**上面的git命令，实际上是将文件推送到服务器！