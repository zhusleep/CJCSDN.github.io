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
站点配置文件：hexo博客文件夹目录下`_config.yml`。
主题配置文件：Next主题文件夹目录下`_config.yml`。

## 一、Next下载安装、启用主题、验证主题等
Next下载安装、启用主题、启用主题。[Next官网](http://theme-next.iissnan.com/getting-started.html)的文档有很清楚的操作步骤，可以直接看官网下载并安装。

## 二、HEXO站点配置文件`_config.yml`等
HEXO站点配置文件`_config.yml`的修改[HEXO官网](https://hexo.io/zh-cn/docs/configuration.html)配置一项中也有很清楚的说明。

## 三、本站修改详情
大部分配置都能在hexo和Next官网文档中找到，如需更多配置请查看官方文档，以下仅作为本站修改记录。
**注意：配置文件要符合英文标点符号使用规范: 冒号后必须空格，否则会编译错误。**

### 1、选择布局外观 Scheme 
打开主题配置文件搜索 `scheme` 关键字。启用的 `scheme` 前面注释 `#` 去除即可。 
```yml
scheme: Mist
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
打开主题配置文件，并按如下对应项修改：
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

### 4、设置头像
编辑主题配置文件， 搜索`avatar`并修改字段设置头像：
```yml
avatar: /uploads/Head_portrait.png
```

### 5、设置网站的图标Favicon
编辑主题配置文件， 搜索`favicon`并修改字段设置网站的图标：
```yml
favicon:
  small: /uploads/favicon-16x16.png
  medium: /uploads/favicon-32x32.png
  apple_touch_icon: /uploads/apple-touch-icon.png
  safari_pinned_tab: /uploads/logo.svg
```

### 6、设置网站关键词
编辑主题配置文件， 搜索`keywords`添加关键词：
```yml
keywords: "CJ, CJCSDN, Hexo, NexT"
```

### 7、添加RSS
7-1、在博客文件夹（CJCSDN.github.io）目录下鼠标右键选择`Git Bash Here`执行：
```bash
$ npm install --save hexo-generator-feed
```
7-2、这个插件会放在`node_modules`这个文件夹里，安装完成后打开站点配置文件搜索`plugins`添加如下：
```yml
#添加RSS插件
plugins: hexo-generate-feed
```
7-3、打开主题配置文件搜索`rss`并修改为如下：
```yml
rss: /atom.xml
```
`$ hexo clean `清除缓存后`$ hexo generate`生成静态文件，在文件夹(public)下看到 `atom.xml` 文件。

### 8、设置侧边栏社交小图标
打开主题配置文件搜索`social`,把`#`去掉就可以启用，如需新增在[图标库](https://fontawesome.com/icons)找自己喜欢的小图标，并将名字复制按`social`格式修改即可：
```yml
#添加社交链接
social:
  GitHub: https://github.com/CJCSDN || github

#设置
social_icons:
  enable: true       #是否启用图标
  icons_only: false  #是否启只显示图标显示文字
  transition: false  
```

### 9、增加友情链接
打开主题配置文件搜索 `links` 并按如下对应项修改：
```yml
# 设置
links_icon: link         #图标
links_title: 友情链接     #标题
links_layout: inline     #布局

#友情链接
links:
  百度搜索: https://www.baidu.com/
  hexo: https://hexo.io/
  theme-next: http://theme-next.iissnan.com/
  我的网址: https://cjcsdn.github.io/
```
### 10、自定义网站底部
9-1、打开主题配置文件搜索 `footer` 并按如下对应项修改：
```yml
footer:
  since: 2017     #指定建站时间，如果没有定义，则使用当年。
  icon: heart     #修改底部心型图形
  powered: false  #关闭默认数据驱动支持

  #关闭主题名称和版本号
  theme:
    enable: false
    version: false
```
9-2、底部添加访客数和总访问量
根据Next官网介绍操作，打开主题配置文件搜索 `busuanzi_count` 并修改配置项：
```yml
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  #本站访客数
  site_uv: true
  site_uv_header: <i class="fa fa-user"></i> 本站访客数
  site_uv_footer: 人次

  #本站总访问量
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i> 本站总访问量
  site_pv_footer: 次

  #文章的本文总阅读量
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i> 本文总阅读量
  page_pv_footer: 次
```

### 11、添加顶部加载条
打开主题配置文件搜索 `pace` 并按如下对应项修改：
```yml
#顶部加载条 默认false
pace: true
pace_theme: pace-theme-minimal
```
在文章底部附上全部自定义样式代码.styl。

### 12、自定义头部logo字体谷歌样式
按照目录路径 `themes\next\layout\_layout.swig` 打开 `_layout.swig` 文件在 `<head></head>` 标签内添加谷歌字体链接：
```html
  <!-- {#谷歌字体#} -->
  <link href='//fonts.googleapis.com/css?family=Kaushan+Script' rel='stylesheet' type='text/css'>
```
如需更换按如下修改步骤：
1、打开[谷歌字体库中文版](http://www.googlefonts.cn/)。
2、选择一个你喜欢的字体样式加入字体库-预览-生成代码，例如选择：`Kaushan Script` 字体。
3、在生成代码页面中，复制 `link` 代码将加入到你的页面（HTTPS请手动修改）:
```html
  <link href='http://fonts.font.im/css?family=Kaushan+Script' rel='stylesheet' type='text/css'>
  <!-- 将 http://fonts.font.im 更换为 //fonts.googleapis.com 然后加入到你的代码中，否则不显示。-->
  <link href='//fonts.googleapis.com/css?family=Kaushan+Script' rel='stylesheet' type='text/css'>
```
4、在CSS样式用使用相应字体,例如:
```css
font-family: 'Kaushan Script', cursive;
```
在文章底部附上全部自定义样式代码.styl。
[如何使用 Google Web Fonts](https://www.zhihu.com/question/19578734)

### 13、在右上角添加fork me on github
点击[1、这里](https://github.com/blog/273-github-ribbons)或者[2、这里](http://tholman.com/github-corners/)挑选自己喜欢的样式，并复制代码。然后把刚才复制的代码粘贴到 `themes\next\layout\_layout.swig` 文件中(放在 `<div class="headband"></div>` 的下面)，并把href改为你的github地址。
我的代码：
```html
    <!-- {#在头部右上角实现fork me on github#} -->
    <a href="https://github.com/CJCSDN" class="github-corner" aria-label="View source on Github" target="_blank"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#151513; color:#fff; position: absolute; top: 0; border: 0; right: 0;" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path></svg></a><style>.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}</style>
```

### 14、文章添加阴影效果

在文章底部附上全部自定义样式代码.styl。