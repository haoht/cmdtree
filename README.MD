# 沉默的大树（cmdtree）

[![Build Status](https://www.travis-ci.org/rhatyang/cmdtree.svg?branch=master)](https://www.travis-ci.org/rhatyang/cmdtree)

个人博客&&静态博客生成器

这是一个基于Node.js的Markdown静态博客生成器。

## 使用方法

### 一、克隆我这个仓库

```
git clone https://github.com/rhatyang/cmdtree.git
```

### 二、修改信息

全局配置文件为`config.json`，在里面替换为你的相关信息，如站点信息，分类信息等

### 三、替换文件

可在`config.json`中自定义相关目录，如我将文章放在`source/post`下，页面放在`source/page`下，替换为你自己的即可，将图片放置于`pics`目录中，生成的静态资源位于`public`目录下。

### 四、主题

本博客系统使用[art-template](https://github.com/aui/art-template)模板系统解析，可使用传统模板语法`{{ }}`或者高级语法`<%- %>`（类似EJS）编写主题，具体变量可参考`lib/template/data.js`文件，自己写一款主题相当方便！

### 五、部署

生成为静态文件后，随便你部署在哪都行。

最省钱也是推荐的方法是部署在Github Pages。[使用Travis CI自动部署Github Pages - 沉默的大树](https://cmdtree.com/blog/2018/01/travis-ci-auto-deploy-github-pages.html)
