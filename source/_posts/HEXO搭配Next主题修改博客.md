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
点击 [1、这里](https://github.com/blog/273-github-ribbons) 或者 [2、这里](http://tholman.com/github-corners/) 挑选自己喜欢的样式，并复制代码。然后把刚才复制的代码粘贴到 `themes\next\layout\_layout.swig` 文件中(放在 `<div class="headband"></div>` 的下面)，并把href改为你的github地址。
我的代码：
```html
    <!-- {#在头部右上角实现fork me on github#} -->
    <a href="https://github.com/CJCSDN" class="github-corner" aria-label="View source on Github" target="_blank"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#151513; color:#fff; position: absolute; top: 0; border: 0; right: 0;" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path></svg></a><style>.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}</style>
```
在文章底部附上全部自定义样式代码.styl。

### 14、文章添加阴影效果
Next文件夹路径`source\css\_custom\custom.styl`文件内自定义样式`html.mist{}`括号内加入文章阴影效果代码：
```styl
html.mist{
  //文章添加阴影效果
  .post{
    margin-top:60px;
    .post-block {
      padding: 35px 30px;
      background: #fff;
      box-shadow: 0 2px 2px 0 rgba(0,0,0,0.12), 0 3px 1px -2px rgba(0,0,0,0.06), 0 1px 5px 0 rgba(0,0,0,0.12);
      border-radius: initial;
    }
  }
}
```
### 15、自定义文章结束标记样式
Next文件夹路径 `next\layout\_macro` 下新建文件 `passage-end-tag.swig` 并添加以下内容：
```swig
{% if not is_index %}
  <div class="article_TheEnd">-----本文结束<i class="fa fa-paw"></i>感谢您的阅读-----</div>
{% endif %}
```
接着打开 `next\layout\_macro\post.swig` 文件，在 `post-body` 结尾后面加上如下代码：
```swig
    {# 文章末尾结束标记 start #}
    {% if not is_index %}
      {% include 'passage-end-tag.swig' %}
    {% endif %}
    {# 文章末尾结束标记 END #}
```

### 16、自定义文章底部版权
打开主题配置文件搜索 `post_copyright` 并按如下对应项修改：
```yml
post_copyright:
  enable: true
  license: CC BY-NC-ND 4.0
  license_url: https://creativecommons.org/licenses/by-nc-nd/4.0/deed.zh
```
然后在打开 `next\layout\_macro\post-copyright.swig` 文件，按如下修改：
```html
<script src="https://cdn.bootcss.com/jquery/2.0.0/jquery.min.js"></script>
<script src="//cdn.bootcss.com/clipboard.js/1.5.10/clipboard.min.js"></script>
<script src="https://unpkg.com/sweetalert/dist/sweetalert.min.js"></script>
<ul class="post-copyright">
  <li class="post-copyright-title">
    <strong>{{ __('post.copyright.title') + __('symbol.colon') }}</strong>
    {{ post.title | default(config.title) }}
  </li>
  <li class="post-copyright-author">
    <strong>{{ __('post.copyright.author') + __('symbol.colon') }}</strong>
    {{ post.author | default(config.author) }}
  </li>
  <li class="post-copyright-created_at">
    <strong>{{ __('post.copyright.created_at') + __('symbol.colon') }}</strong>
    {{ date(post.date, config.date_format) }}
  </li>
  <li class="post-copyright-updated_at">
    <strong>{{ __('post.copyright.updated_at') + __('symbol.colon') }}</strong>
    {{ date(post.updated, config.date_format) }}
  </li>
  <li class="post-copyright-link">
    <strong>{{ __('post.copyright.link') + __('symbol.colon') }}</strong>
    <a href="{{ post.url | default(post.permalink) }}" title="{{ post.title }}">{{ post.url | default(post.permalink) }}</a>
    <span class="copy-path"  title="点击复制文章链接"><i class="fa fa-clipboard" data-clipboard-text="{{ page.permalink }}"  aria-label="复制成功！"></i></span>
  </li>
  <li class="post-copyright-license">
    <strong>{{ __('post.copyright.license_title') + __('symbol.colon') }} </strong>
    {{ __('post.copyright.license_content', theme.post_copyright.license_url, theme.post_copyright.license) }}
  </li>
</ul>
<script> 
    var clipboard = new Clipboard('.fa-clipboard');
    $(".fa-clipboard").click(function(){
      clipboard.on('success', function(){
        swal({
          title: "",
          text: '复制文章链接成功',
          icon: "success",
          showConfirmButton: true
          });
	    });
    });  
</script>
```
添加并修改文章标题、作者、发布时间、修改时间、本文链接、版权声明。这里增加了文章链接复制功能，以及时间的调用。时间的调用显示格式以下三种都可以：
发布时间：
```swig
{{ page.date.format("YYYY年MM月DD日") }}
{{ date(post.date, 'YYYY年MM月DD日') }}
{{ date(post.date, config.date_format) }}
```
更新时间：
```swig
{{ page.updated.format("YYYY年MM月DD日") }}
{{ date(post.updated, 'YYYY年MM月DD日') }}
{{ date(post.updated, config.date_format) }}
```
不同之处在于第三种没有中文年月日，显示样式和站点配置文件时间样式相同：
```yml
date_format: YYYY-MM-DD
time_format: HH:mm:ss
```
完成以上修改后，打开 `themes\next\languages\zh-Hans.yml` 搜索 `copyright：` 自定义修改类别名称如下：
```yml
copyright:
    title: 本文标题
    created_at: 发布时间
    updated_at: 最后更新
    author: 本文作者
    link: 本文链接
    license_title: 版权声明
    license_content: '本博客所有文章除特别声明外，均采用
      <a href="%s" rel="external nofollow" target="_blank">%s</a> 许可协议。转载请注明出处！'
```
自此完成了对文中底部版权的自定义修改，在文章底部附上全部自定义样式代码.styl。

### 17、修改文章底部的带#号的标签
打开 `themes\next\layout\_macro\post.swig` 文件 搜索 ` rel="tag"` 把 `#` 换成图形标签`<i class="fa fa-tag"></i>`复制如下代码：
```html
<i class="fa fa-tag"><!--把#换成图形标签<i class="fa fa-tag"></i>--></i>
```

### 18、文章列表显示阅读全文
打开主题配置文件并搜索 `auto_excerpt:` 做如下修改：
```yml
auto_excerpt:
  enable: true
  length: 150
```
### 19、添加字数统计、阅读时长
在博客文件夹（CJCSDN.github.io）目录下鼠标右键选择`Git Bash Here`执行安装 `hexo-wordcount`：
```bash
$ npm install hexo-wordcount --save
```
然后在主题配置文件中找到如下配置，并修改配置如下：
```yml
post_meta:
  item_text: true
  created_at: true #发布时间
  updated_at: false #更新时间
  categories: true #分类

post_wordcount:
  item_text: true
  wordcount: true #单篇字数统计
  min2read: true #单篇阅读时长
  totalcount: false #站点字数统计
  separated_meta: true
```
显示样式加上“字”和“分钟”，则打开 `themes\next\layout\_macro\post.swig` 文件分别搜索代码：
```html
<span title="{{ __('post.wordcount') }}">
  {{ wordcount(post.content) }}
</span>
```
```html
<span title="{{ __('post.min2read') }}">
  {{ min2read(post.content) }}
</span>
```
并把“字”和“分钟”按如下添加到代码后面：
```html
<span title="{{ __('post.wordcount') }}">
  {{ wordcount(post.content) }} 字
</span>
```
```html
<span title="{{ __('post.min2read') }}">
  {{ min2read(post.content) }} 分钟
</span>
```

## 四、自定义样式代码.styl
```styl
// Custom styles.
//主题 scheme: Mist 自定义样式
html.mist{
  //中间背景颜色
  .container{
      background-color: rgba(219, 219, 219, 0.5);
  }
  
  //头部进度条
  .pace .pace-progress{
    background: #222;
  }

  .site-title{
    //头部logo字体谷歌样式
    font-family: 'Kaushan Script', cursive;
    font-size: 2em;
    line-height: 1.4em;
  }

  //文章添加阴影效果
  .post{
    margin-top:60px;
    .post-block {
      padding: 35px 30px;
      background: #fff;
      box-shadow: 0 2px 2px 0 rgba(0,0,0,0.12), 0 3px 1px -2px rgba(0,0,0,0.06), 0 1px 5px 0 rgba(0,0,0,0.12);
      border-radius: initial;
      //自定义文章结束标记样式
      .article_TheEnd{
        width: 100%;
        margin: 0 auto;
        font-size: 16px;
        text-align: center;
        color: #ccc;
      }
    }
  }

  //右侧头像最大宽度
  .site-author-image{
    max-width: 155px;
  }
  //右侧字体颜色
  .sidebar-nav .sidebar-nav-active{
    color: #fc6423;
    border-bottom-color: #fc6423;
  }
  .sidebar-nav .sidebar-nav-active:hover{
    color: #fc6423;
  }
  .post-toc .nav .active > a{
    color: #fc6423;
    border-bottom-color: #fc6423;
  }
  .post-toc .nav .active-current > a{
    color: #fc6423;
  }
    
  //文章底部版权样式
  .post-copyright{
    line-height: 2em;
    font-size: 0.93rem;
    padding: 0.5em 0.75em;
    strong{
      color: #b5b5b5;
      word-break: break-all;
    }
  }
  .copy-path{
    display: inline-block;
    width: 1em;
    margin-left: 0.5em;
    color: #b5b5b5;
    &:hover{
    color: #000;
    cursor: pointer;
    }
  }

 @media (min-width: 1600px) {
    .container .header-inner,
    .container .main-inner{
    width: $main-desktop;
    }
  }
  //自定义移动端布局
  @media (max-width: 767px) {
    .menu {
      margin: 10px auto;
      padding: 0;
    }

    .site-meta {
      margin-left: 0;
        .site-title {
        line-height: 28px;
      }
    }

    .header-inner {
      width: auto;
      margin-bottom: 50px;
      padding: 10px 10px 0;
      .site-brand-wrapper{
        margin-bottom: 10px;
        content: " ";
        display: table;
        clear: both;
        width: 100%;
      }
    }

    .container .main-inner {
      width: auto;
      margin-top: 0;
    }

    .github-corner{
      display: none;
    }

    .copy-path {
      display: none;
    }
    
  }
}
```

## 五、站点配置文件
```yml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: CJ'S BLOG
subtitle: CJ的博客小站
description: 欢迎来到CJ的技术分享站~
author: CJ
language: zh-Hans
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://cjcsdn.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: true #资源文件夹开启
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
#添加RSS插件
plugins: hexo-generate-feed
## Themes: https://hexo.io/themes/
theme: next

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/CJCSDN/CJCSDN.github.io.git
  branch: master

```

## 六、主题配置文件
```yml
# ---------------------------------------------------------------
# Theme Core Configuration Settings
# ---------------------------------------------------------------

# Set to true, if you want to fully override the default configuration.
# Useful if you don't want to inherit the theme _config.yml configurations.
override: false

# ---------------------------------------------------------------
# Site Information Settings
# ---------------------------------------------------------------

# To get or check favicons visit: https://realfavicongenerator.net
# Put your favicons into `hexo-site/source/` (recommend) or `hexo-site/themes/next/source/images/` directory.

# Default NexT favicons placed in `hexo-site/themes/next/source/images/` directory.
# And if you want to place your icons in `hexo-site/source/` root directory, you must remove `/images` prefix from pathes.

# For example, you put your favicons into `hexo-site/source/images` directory.
# Then need to rename & redefine they on any other names, otherwise icons from Next will rewrite your custom icons in Hexo.
favicon:
  small: /uploads/favicon-16x16.png
  medium: /uploads/favicon-32x32.png
  apple_touch_icon: /uploads/apple-touch-icon.png
  safari_pinned_tab: /uploads/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml

# Set default keywords (Use a comma to separate)
keywords: "CJ, CJCSDN, Hexo, NexT" # 网站关键词，有利于SEO优化

# Set rss to false to disable feed link.
# Leave rss as empty to use site's feed link.
# Set rss to specific value if you have burned your feed already.
rss: /atom.xml

footer:
  # Specify the date when the site was setup.
  # If not defined, current year will be used.
  since: 2017

  # Icon between year and copyright info.
  #修改底部心型图形
  icon: heart

  # If not defined, will be used `author` from Hexo main config.
  copyright: 
  # -------------------------------------------------------------
  # Hexo link (Powered by Hexo).
  powered: false

  theme:
    # Theme & scheme info link (Theme - NexT.scheme).
    enable: false
    # Version info of NexT after scheme info (vX.X.X).
    version: false
  # -------------------------------------------------------------
  # Any custom text can be defined here.
  #custom_text: Hosted by <a target="_blank" href="https://pages.github.com">GitHub Pages</a>

# ---------------------------------------------------------------
# SEO Settings
# ---------------------------------------------------------------

# Canonical, set a canonical link tag in your hexo, you could use it for your SEO of blog.
# See: https://support.google.com/webmasters/answer/139066
# Tips: Before you open this tag, remember set up your URL in hexo _config.yml ( ex. url: http://yourdomain.com )
canonical: true

# Change headers hierarchy on site-subtitle (will be main site description) and on all post/pages titles for better SEO-optimization.
seo: false

# If true, will add site-subtitle to index page, added in main hexo config.
# subtitle: Subtitle
index_with_subtitle: false


# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash from link value (/archives -> archives).
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If translate for this menu will find in languages - this translate will be loaded; if not - Key name will be used. Key is case-senstive.
# Value before `||` delimeter is the target link.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, question icon will be loaded.
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

# Enable/Disable menu icons.
menu_icons:
  enable: true


# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
scheme: Mist
#scheme: Pisces
#scheme: Gemini


# ---------------------------------------------------------------
# Sidebar Settings
# ---------------------------------------------------------------

# Social Links.
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimeter is the target permalink.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, globe icon will be loaded.
social:
  GitHub: https://github.com/CJCSDN || github
  #E-Mail: mailto:yourname@gmail.com || envelope
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype

social_icons:
  enable: true
  icons_only: false
  transition: false

# Blog rolls
links_icon: link
links_title: 友情链接
links_layout: inline

links:
  百度搜索: https://www.baidu.com/
  hexo: https://hexo.io/
  theme-next: http://theme-next.iissnan.com/
  我的网址: https://cjcsdn.github.io/

# Sidebar Avatar
# in theme directory(source/images): /images/avatar.gif
# in site  directory(source/uploads): /uploads/avatar.gif
avatar: /uploads/Head_portrait.png

# Table Of Contents in the Sidebar
toc:
  enable: true

  # Automatically add list number to toc.
  number: true

  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: false

# Creative Commons 4.0 International License.
# http://creativecommons.org/
# Available: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
#creative_commons: by-nc-sa
#creative_commons:

sidebar:
  # Sidebar Position, available value: left | right (only for Pisces | Gemini).
  position: left
  #position: right

  # Sidebar Display, available value (only for Muse | Mist):
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  Totally remove sidebar including sidebar toggle.
  display: post
  #display: always
  #display: hide
  #display: remove

  # Sidebar offset from top menubar in pixels (only for Pisces | Gemini).
  offset: 12

  # Back to top in sidebar (only for Pisces | Gemini).
  b2t: false

  # Scroll percent label in b2t button.
  scrollpercent: false

  # Enable sidebar on narrow view (only for Muse | Mist).
  onmobile: false


# ---------------------------------------------------------------
# Post Settings
# ---------------------------------------------------------------

# Automatically scroll page to section which is under <!-- more --> mark.
# 开启后使用 <!-more--> 可以实现点击查看全文效果
scroll_to_more: true

# Automatically saving scroll position on each post/page in cookies.
save_scroll: false

# Automatically excerpt description in homepage as preamble text.
excerpt_description: true

# Automatically Excerpt. Not recommend.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true
  length: 150

# Post meta display settings
post_meta:
  item_text: true
  created_at: true #发布时间
  updated_at: false #更新时间
  categories: true #分类

# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true #单篇字数统计
  min2read: true #单篇阅读时长
  totalcount: false #站点字数统计
  separated_meta: true

# Wechat Subscriber
#wechat_subscriber:
  #enabled: true
  #qcode: /path/to/your/wechatqcode ex. /uploads/wechat-qcode.jpg
  #description: ex. subscribe to my blog by scanning my public wechat account

# Reward
#reward_comment: Donate comment here
#wechatpay: /images/wechatpay.jpg
#alipay: /images/alipay.jpg
#bitcoin: /images/bitcoin.png

# Declare license on posts
post_copyright:
  enable: true
  license: CC BY-NC-ND 4.0
  license_url: https://creativecommons.org/licenses/by-nc-nd/4.0/deed.zh


# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Reduce padding / margin indents on devices with narrow width.
mobile_layout_economy: false

# Android Chrome header panel color ($black-deep).
android_chrome_color: "#222"

# Custom Logo.
# !!Only available for Default Scheme currently.
# Options:
#   enabled: [true/false] - Replace with specific image
#   image: url-of-image   - Images's url
custom_logo:
  enabled: false
  image:

# Code Highlight theme
# Available value:
#    normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal


# ---------------------------------------------------------------
# Font Settings
# - Find fonts on Google Fonts (https://www.google.com/fonts)
# - All fonts set here will have the following styles:
#     light, light italic, normal, normal italic, bold, bold italic
# - Be aware that setting too much fonts will cause site running slowly
# - Introduce in 5.0.1
# ---------------------------------------------------------------
# CAUTION! Safari Version 10.1.2 bug: https://github.com/iissnan/hexo-theme-next/issues/1844
# To avoid space between header and sidebar in Pisces / Gemini themes recommended to use Web Safe fonts for `global` (and `logo`):
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------
font:
  enable: false

  # Uri of fonts host. E.g. //fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: xx`. Use `px` as unit.

  # Global font settings used on <body> element.
  global:
    external: true
    family: Lato
    size:

  # Font settings for Headlines (h1, h2, h3, h4, h5, h6).
  # Fallback to `global` font settings.
  headings:
    external: true
    family:
    size:

  # Font settings for posts.
  # Fallback to `global` font settings.
  posts:
    external: true
    family:

  # Font settings for Logo.
  # Fallback to `global` font settings.
  logo:
    external: true
    family:
    size:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
    size:


# ---------------------------------------------------------------
# Third Party Services Settings
# ---------------------------------------------------------------

# MathJax Support
mathjax:
  enable: false
  per_page: false
  cdn: //cdn.bootcss.com/mathjax/2.7.1/latest.js?config=TeX-AMS-MML_HTMLorMML

# Han Support docs: https://hanzi.pro/
han: false

# Swiftype Search API Key
#swiftype_key:

# Baidu Analytics ID
#baidu_analytics:

# Duoshuo ShortName
#duoshuo_shortname:

# Disqus
disqus:
  enable: false
  shortname: 
  count: true

# Hypercomments
#hypercomments_id:

# changyan
changyan:
  enable: false
  appid:
  appkey:


# Valine.
# You can get your appid and appkey from https://leancloud.cn
# more info please open https://valine.js.org
valine:
  enable: false
  appid:  # your leancloud application appid
  appkey:  # your leancloud application appkey
  notify: false # mail notifier , https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: Just go go # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size


# Support for youyan comments system.
# You can get your uid from http://www.uyan.cc
#youyan_uid: your uid

# Support for LiveRe comments system.
# You can get your uid from https://livere.com/insight/myCode (General web site)
#livere_uid: your uid

# Gitment
# Introduction: https://imsun.net/posts/gitment-introduction/
# You can get your Github ID from https://api.github.com/users/<Github username>
gitment:
  enable: false
  mint: true # RECOMMEND, A mint on Gitment, to support count, language and proxy_gateway
  count: true # Show comments count in post meta area
  lazy: false # Comments lazy loading with a button
  cleanly: false # Hide 'Powered by ...' on footer, and more
  language: # Force language, or auto switch by theme
  github_user: # MUST HAVE, Your Github ID
  github_repo: # MUST HAVE, The repo you use to store Gitment comments
  client_id: # MUST HAVE, Github client id for the Gitment
  client_secret: # EITHER this or proxy_gateway, Github access secret token for the Gitment
  proxy_gateway: # Address of api proxy, See: https://github.com/aimingoo/intersect
  redirect_protocol: # Protocol of redirect_uri with force_redirect_protocol when mint enabled

# Baidu Share
# Available value:
#    button | slide
# Warning: Baidu Share does not support https.
#baidushare:
##  type: button

# Share
# This plugin is more useful in China, make sure you known how to use it.
# And you can find the use guide at official webiste: http://www.jiathis.com/.
# Warning: JiaThis does not support https.
#jiathis:
  ##uid: Get this uid from http://www.jiathis.com/
#add_this_id:

# Share
#duoshuo_share: true

# NeedMoreShare2
# This plugin is a pure javascript sharing lib which is useful in China.
# See: https://github.com/revir/need-more-share2
# Also see: https://github.com/DzmVasileusky/needShareButton
# iconStyle: default | box
# boxForm: horizontal | vertical
# position: top / middle / bottom + Left / Center / Right
# networks: Weibo,Wechat,Douban,QQZone,Twitter,Linkedin,Mailto,Reddit,
#           Delicious,StumbleUpon,Pinterest,Facebook,GooglePlus,Slashdot,
#           Technorati,Posterous,Tumblr,GoogleBookmarks,Newsvine,
#           Evernote,Friendfeed,Vkontakte,Odnoklassniki,Mailru
needmoreshare2:
  enable: false
  postbottom:
    enable: false
    options:
      iconStyle: box
      boxForm: horizontal
      position: bottomCenter
      networks: Weibo,Wechat,Douban,QQZone,Twitter,Facebook
  float:
    enable: false
    options:
      iconStyle: box
      boxForm: horizontal
      position: middleRight
      networks: Weibo,Wechat,Douban,QQZone,Twitter,Facebook

# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
#google_site_verification:

# Google Analytics
#google_analytics:

# Bing Webmaster tools verification setting
# See: https://www.bing.com/webmaster/
#bing_site_verification:

# Yandex Webmaster tools verification setting
# See: https://webmaster.yandex.ru/
#yandex_site_verification:

# CNZZ count
#cnzz_siteid:

# Application Insights
# See https://azure.microsoft.com/en-us/services/application-insights/
# application_insights:

# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: false
  user_id: 0
  #admin_nickname: Author

# Post widgets & FB/VK comments settings.
# ---------------------------------------------------------------
# Facebook SDK Support.
# https://github.com/iissnan/hexo-theme-next/pull/410
facebook_sdk:
  enable:       false
  app_id:       #<app_id>
  fb_admin:     #<user_id>
  like_button:  #true
  webmaster:    #true

# Facebook comments plugin
# This plugin depends on Facebook SDK.
# If facebook_sdk.enable is false, Facebook comments plugin is unavailable.
facebook_comments_plugin:
  enable:       false
  num_of_posts: 10    # min posts num is 1
  width:        100%  # default width is 550px
  scheme:       light # default scheme is light (light or dark)

# VKontakte API Support.
# To get your AppID visit https://vk.com/editapp?act=create
vkontakte_api:
  enable:       false
  app_id:       #<app_id>
  like:         true
  comments:     true
  num_of_posts: 10

# Star rating support to each article.
# To get your ID visit https://widgetpack.com
rating:
  enable: false
  id:     #<app_id>
  color:  fc6423
# ---------------------------------------------------------------

# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.
leancloud_visitors:
  enable: false
  app_id: #<app_id>
  app_key: #<app_key>

# Another tool to show number of visitors to each article.
# visit https://console.firebase.google.com/u/0/ to get apiKey and projectId
# visit https://firebase.google.com/docs/firestore/ to get more information about firestore
firestore:
  enable: false
  collection: articles #required, a string collection name to access firestore database
  apiKey: #required
  projectId: #required
  bluebird: false #enable this if you want to include bluebird 3.5.1(core version) Promise polyfill

# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: <i class="fa fa-user"></i> 本站访客数
  site_uv_footer: 人次
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i> 本站总访问量
  site_pv_footer: 次
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i> 本文总阅读量
  page_pv_footer: 次


# Tencent analytics ID
# tencent_analytics:

# Tencent MTA ID
# tencent_mta:


# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO
baidu_push: true

# Google Calendar
# Share your recent schedule to others via calendar page
#
# API Documentation:
# https://developers.google.com/google-apps/calendar/v3/reference/events/list
calendar:
  enable: false
  calendar_id: <required>
  api_key: <required>
  orderBy: startTime
  offsetMax: 24
  offsetMin: 4
  timeZone:
  showDeleted: false
  singleEvents: true
  maxResults: 250

# Algolia Search
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# Local search
# Dependencies: https://github.com/flashlab/hexo-generator-search
local_search:
  enable: false
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1


# ---------------------------------------------------------------
# Tags Settings
# ---------------------------------------------------------------

# External URL with BASE64 encrypt & decrypt.
# Usage: {% exturl text url "title" %}
# Alias: {% extlink text url "title" %}
exturl: false

# Note tag (bs-callout).
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Label tag.
label: true

# Tabs tag.
tabs:
  enable: true
  transition:
    tabs: false
    labels: true
  border_radius: 0


#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! ---------------------------------------------------------------

# Use velocity to animate everything.
motion:
  enable: true
  async: false
  transition: 
    # Transition variants:
    # fadeIn | fadeOut | flipXIn | flipXOut | flipYIn | flipYOut | flipBounceXIn | flipBounceXOut | flipBounceYIn | flipBounceYOut
    # swoopIn | swoopOut | whirlIn | whirlOut | shrinkIn | shrinkOut | expandIn | expandOut
    # bounceIn | bounceOut | bounceUpIn | bounceUpOut | bounceDownIn | bounceDownOut | bounceLeftIn | bounceLeftOut | bounceRightIn | bounceRightOut
    # slideUpIn | slideUpOut | slideDownIn | slideDownOut | slideLeftIn | slideLeftOut | slideRightIn | slideRightOut
    # slideUpBigIn | slideUpBigOut | slideDownBigIn | slideDownBigOut | slideLeftBigIn | slideLeftBigOut | slideRightBigIn | slideRightBigOut
    # perspectiveUpIn | perspectiveUpOut | perspectiveDownIn | perspectiveDownOut | perspectiveLeftIn | perspectiveLeftOut | perspectiveRightIn | perspectiveRightOut
    post_block: fadeIn
    post_header: slideDownIn
    post_body: slideDownIn
    coll_header: slideLeftIn
    # Only for Pisces | Gemini.
    sidebar: slideUpIn

# Fancybox
fancybox: true

# Progress bar in the top during page loading.
#顶部加载条 默认false
pace: true
# Themes list:
#pace-theme-big-counter
#pace-theme-bounce
#pace-theme-barber-shop
#pace-theme-center-atom
#pace-theme-center-circle
#pace-theme-center-radar
#pace-theme-center-simple
#pace-theme-corner-indicator
#pace-theme-fill-left
#pace-theme-flash
#pace-theme-loading-bar
#pace-theme-mac-osx
#pace-theme-minimal #默认
# For example
# pace_theme: pace-theme-center-simple
pace_theme: pace-theme-minimal

# Canvas-nest
canvas_nest: false

# three_waves
three_waves: false

# canvas_lines
canvas_lines: false

# canvas_sphere
canvas_sphere: false

# Only fit scheme Pisces
# Canvas-ribbon
# size: The width of the ribbon.
# alpha: The transparency of the ribbon.
# zIndex: The display level of the ribbon.
canvas_ribbon:
  enable: false
  size: 300
  alpha: 0.6
  zIndex: -1

# Script Vendors.
# Set a CDN address for the vendor you want to customize.
# For example
#    jquery: https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js
# Be aware that you should use the same version as internal ones to avoid potential problems.
# Please use the https protocol of CDN files when you enable https on your site.
vendors:
  # Internal path prefix. Please do not edit it.
  _internal: lib

  # Internal version: 2.1.3
  jquery:

  # Internal version: 2.1.5
  # See: http://fancyapps.com/fancybox/
  fancybox:
  fancybox_css:

  # Internal version: 1.0.6
  # See: https://github.com/ftlabs/fastclick
  fastclick:

  # Internal version: 1.9.7
  # See: https://github.com/tuupola/jquery_lazyload
  lazyload:

  # Internal version: 1.2.1
  # See: http://VelocityJS.org
  velocity:

  # Internal version: 1.2.1
  # See: http://VelocityJS.org
  velocity_ui:

  # Internal version: 0.7.9
  # See: https://faisalman.github.io/ua-parser-js/
  ua_parser:

  # Internal version: 4.6.2
  # See: http://fontawesome.io/
  fontawesome:

  # Internal version: 1
  # https://www.algolia.com
  algolia_instant_js:
  algolia_instant_css:

  # Internal version: 1.0.2
  # See: https://github.com/HubSpot/pace
  # Or use direct links below:
  # pace: //cdn.bootcss.com/pace/1.0.2/pace.min.js
  # pace_css: //cdn.bootcss.com/pace/1.0.2/themes/blue/pace-theme-flash.min.css
  pace:
  pace_css:

  # Internal version: 1.0.0
  # https://github.com/hustcc/canvas-nest.js
  canvas_nest:

  # three
  three:

  # three_waves
  # https://github.com/jjandxa/three_waves
  three_waves:

  # three_waves
  # https://github.com/jjandxa/canvas_lines
  canvas_lines:

  # three_waves
  # https://github.com/jjandxa/canvas_sphere
  canvas_sphere:

  # Internal version: 1.0.0
  # https://github.com/zproo/canvas-ribbon
  canvas_ribbon:

  # Internal version: 3.3.0
  # https://github.com/ethantw/Han
  han:

  # needMoreShare2
  # https://github.com/revir/need-more-share2
  needMoreShare2:


# Assets
css: css
js: js
images: images

# Theme version
version: 5.1.3

```