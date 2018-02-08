---
title: HEXO搭配Next主题修改博客
date: 2017-12-16 16:55:50
tags: 
    - Next
    - HEXO
categories: Next
---
>前面说完了hexo+Github搭建博客，但是默认的主题样式不是我喜欢的，所以想改掉。看了很多的hexo的主题，还是Next主题符合我的要求简洁明了。

**这里注意区分两个配置文件：**
站点配置文件：hexo文件夹下`_config.yml`。
主题配置文件：Next文件夹下`_config.yml`。

## 一、Next下载安装、启用主题、验证主题等
Next下载安装、启用主题、启用主题。[Next官网](http://theme-next.iissnan.com/getting-started.html)的文档有很清楚的操作步骤，可以直接看官网下载并安装。

## 二、HEXO站点配置文件`_config.yml`等
HEXO站点配置文件`_config.yml`的修改[HEXO官网](https://hexo.io/zh-cn/docs/configuration.html)配置一项中也有很清楚的说明。

## 三、本站修改详情
大部分配置都能在hexo和Next官网文档中找到，如需更多配置请查看官方文档，以下仅作为本站修改记录。
**注意：配置文件要符合英文标点符号使用规范: 冒号后必须空格，否则会编译错误。**

### 1、选择布局外观 Scheme 
布局外观 Scheme 的切换通过更改主题配置文件，打开主题配置文件搜索 `scheme` 关键字。 你会看到有四行 `scheme` 的配置，将你需用启用的 `scheme` 前面注释 `#` 去除即可。 
```yml
# Schemes
#scheme: Muse
scheme: Mist  #本站使用
#scheme: Pisces
#scheme: Gemini
```
### 2、设置网站标题、作者、语言
打开站点配置文件，修改这些值：
```yml
# Site
title: CJ'S BLOG
subtitle: CJ的博客小站
description: 欢迎来到CJ的技术分享站~
author: CJ
language: zh-Hans
timezone:
```
### 3、设置菜单
打开主题配置文件，修改以下内容：
```yml
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
```
选择简体中文，所以对应的翻译文件 `languages/zh-Hans.yml`，在 `menu` 字段下：
```yml
menu:
  home: 首页
  archives: 归档
  categories: 分类
  tags: 标签
  about: 关于我们
```