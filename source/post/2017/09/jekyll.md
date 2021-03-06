---
date: 2017-09-12 02:25:17
title: "Jekyll最全使用指南"
category: 使用笔记
---

这是一篇Jekyll的入门教程，怎么定义入门我也不知道，反正就是想到什么就写什么吧

## 安装Jekyll

我觉得无论是在任何平台安装Jekyll都是非常简单的。安装好ruby和gem就可以使用gem安装jekyll了

[本站搭建笔记(一)安装本地环境](http://fanzhiyang.com/blog/this-site-building-notes-01.html)

**失败原因总结:**

1.Ubuntu系列需要安装`ruby-dev`

2.必须安装有编译工具（make，gcc，g++等）或者安装`ruby-build`(windows不需要)

3.在安装前安装先安装`bundle`

4.某些Linux平台（fedora、arch）：可以先使用系统包管理命令安装jekyll（如fedora中的rubygem-jekyll、arch中的ruby-jekyll）这样安装的不是最新版本，然后再使用`gem update`升级到最新版本即可！

### Gem 源问题

如果在`bundle install`中提示包含HTTP或者`SSL_connect`的字眼的错误时，请安装OpenSSL并修改源为http的源。

修改方法：[更改RubyGems源](http://fanzhiyang.com/blog/ruby-gem-change.html)

## 配置Jekyll


Jekyll的全局配置文件在`_config.yml`.

例如：

```yml
title: 樊志阳博客
description: 这里是樊志阳的个人博客
url: "http://www.fanzhiyang.com"
permalink: /p/:year/:month/:title.html
markdown: kramdown
plugins:
  - jekyll-sitemap
  - jekyll-feed
# 从3.5.2开始，以前对于插件的配置是使用gem字段现在改成了plugins
```


这是一份简单的配置文件，这里**每个值都不是必须的**，也就是说，你删掉这个文件也能运行Jekyll，你可以简单理解这里只是**定义了一些全局变量**，当你需要重复引用某个部分时，你就可以自己添加一个变量。

比如`title`，你肯定不只一次的需要输出它，但是记住，这并不代表`_config.yml`中的`title`就是必须的，但是为了修改方便，我们都会在`_config.yml`中预先设定好这些**规则**，同样的站点描述`description`，我嫌她太长了，我可以把他改成

```yml
desc: 这里是樊志阳的个人博客
```

只要在引用的时候使用`{{ site.desc }}`，每一个在`_config.yml`中定义的变量都是这样使用。

```
{{ site.valueName }}
```

`{{ }}`双大括号的作用就是输出里面变量的值，而`{% %}`大括号里用双引号就是进行逻辑运算。使用模板引擎语法时就要使用`{% %}`。


## 模板引擎

Jekyll使用Liquid模板引擎，这个模板引擎非常简单，中文文档在

[Liquid 模板语言中文文档](http://liquid.bootcss.com/)

### 路径问题

一般情况下，我推荐：

- 在配置文件中设置好文章固定链接：[永久链接](http://jekyll.com.cn/docs/permalinks/)

- 尽量使用域名根目录作为站点根目录，如果非得要用域名/目录的形式，可以将`index.md`文件放到你想要显示主页的目录中。

- 图片资源，我建议在配置文件中定义好图片路径，如：

```yml
images_url: "http://images.fanzhiyang.com"
```
然后这样引用图片

```
![]({{ site.images_url }}/path/pic.png)
```

这样的好处是，你在想换图床的时候改一下链接就好了

## 部署

如果你使用Coding pages或者Github pages，直接将未生成的源码push上去就好了，他们会自动生成并部署。

如果你使用虚拟主机，你可以使用sync同步工具或者git-ftp来进行同步生成好的源码。

如果你使用服务器或者VPS，你可以将网站生成好再同步上去，或者直接在服务器搭建好jekyll环境，使用nginx或者ruby的web服务都可以。

## 相关文章：

[jekyll 的一些函数和技巧](http://fanzhiyang.com/blog/jekyll-more.html)

[Jekyll error：tag was never closed](http://fanzhiyang.com/blog/jekyll-tag-was-never-closed.html)

[使用jekyll在Github上搭建博客](http://fanzhiyang.com/blog/use-jekyll-build-blog-on-github.html)

[为 jekyll 博客添加静态搜索](http://fanzhiyang.com/blog/jekyll-static-search.html)

[定制Google自定义搜索页](http://fanzhiyang.com/blog/use-google-customize-search.html)

[Github Pages绑定域名添加http（Cloudflare](http://fanzhiyang.com/blog/github-pages-cloudflare-ssl.html)

