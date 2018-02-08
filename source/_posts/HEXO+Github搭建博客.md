---
title: HEXO+Github搭建博客
date: 2017-12-16 16:55:33
tags: 
    - HEXO+Github搭建博客
    - HEXO
    - Github
categories: HEXO
---
## 一、前言
过了很久回过头来写这篇文章，算是总结吧。因为一开始就想随便搞个博客啥的玩一下，力求简单简洁，不想自己搞站点啥的。所以找到了GitHub Pages，而且给我们提供域名和空间，省事！Github Pages 需要相应的博客引擎来驱动，主流的有两个 [Hexo](https://hexo.io/) 和 [jekyll](https://jekyllrb.com/)。一开始我用的是jekyll，真真感受到了那句经典的话：从入门到放弃！Orz...。git两者都要，为了push到github。而jekyll需要安装ruby，hexo需要nodejs。两者的官网直观感受和文档介绍详细以及易用性来说，我更倾向于Hexo。于是转用Hexo，后期补写的文章。

## 二、配置环境
### 申请GitHub
申请GitHub做博客的远程创库、域名、服务器等等，如果你有账号了也创建有库了可以跳过。这里只说申请账号，至于创建库我会在下面安装Hexo的时候会说到。github账号没有的话直接[github官网](https://github.com/)申请就行了（看不懂英文就百度翻译），跟一般的注册账号差不多，网上也有教程。还有网上很多人说的SSH Keys，看你自己了，可以不配制。我当时是用GitHub Desktop把库Clone到本地，因为我安装了Git，所以在Clone到本地的库文件夹内鼠标右键选择`Git Bash Here`也能管理自己的博客，包括修改提交等等操作。这里根据个人实际情况灵活处理，就不过多的啰嗦了。

### 安装 node.js
安装node环境，用来生成静态页面。可以直接到node官网下载安装包安装：[node中文网](http://nodejs.cn/)、[node英文网](https://nodejs.org/en/)，[更多配置详情可点此参考](http://www.runoob.com/nodejs/nodejs-install-setup.html)或者我[这篇文章nodejs安装部分](https://cjcsdn.github.io/2017/12/16/Windows使用vue-cli搭建项目教程/)。如果你已安装有，跳过此步骤。

### 安装 Git
作用就是把本地的hexo内容提交到github上去，安装git比较常用的有两种方式：
1、[Git安装包](https://git-scm.com/downloads)
2、[GitHub for Windows](https://desktop.github.com/)
我的环境是Windows，所以安装git这里也没啥好说的。还有就是Git Bash命令和GitHub Desktop这些使用，网上一搜基本有很多教程。GitHub Desktop会更加方便些，界面处理。登录你的GitHub账号，把你的库Clone到你本地就好了，这个后面会说到。
3、这里，我们要区分清楚git与github。git是一个版本控制的工具，而github就看做远程仓库，用于存放用git管理的各种项目。通俗说就是一个是工具，一个是存储的仓库。你通过操作这个工具来拉取和推送等方式管理你的仓库的东西。

## 三、安装Hexo流程
### 安装前言
安装Hexo相当简单。在安装之前我都会考虑长远一点，包括转移、hexo更新、主题更新、博文更新、markdown语法使用、多台设备管理操作等等。但是目前我只说下面的两种情况，一下说太多就会显得啰嗦，留到以后有时间在补上吧。我要说的两种情况是：
1、第一种是如果只满足于简单的部署发布，在自己的GitHub账号下创建一个新的仓库，命名为username.github.io（username是你的账号名)，就完全够用了，因为这种情况Hexo部署到GitHub上的文件是.md（你的博文）转化之后的.html（静态网页），不会把你Hexo网站文件包括你的设置和一些IDKey放上去。。然后想绑定个人域名或者放到coding上的都根据自身情况决定了，因为网上也有很多教程。
2、第二种情况就是利用分支来管理你的博客hexo文件和生成的网站文件。当你重装电脑或者想在不同电脑上修改博客时，第一种情况就有点麻烦，也不是没有办法解决，目前多数都喜欢用GitHub的分支来解决。将所有文件放在hexo分支下，将public文件夹通过插件自动发布放在master分支以供加载展示。同时因为有配置.gitignore文件，无需担心node_modules等文件被手动发布到hexo分支下，达到文件分类存放的目的。下面就是用这种情况来安装hexo。

### 创建对应仓库
在自己的GitHub账号下创建一个新的仓库`New repository`![创建新库](01.png)，命名为username.github.io（username是你的账号名)。![命名库](02.png)GitHub >Pages有两种类型：User/Organization Pages 和 Project Pages，而我们所使用的是User Pages。
User Pages 与 Project Pages的区别是：
1、User Pages 是用来展示用户的，而 Project Pages 是用来展示项目的。
2、用于存放 User Pages 的仓库必须使用username.github.io的命名规则，而 Project Pages 则没有特殊的要求。
3、User Pages 将使用仓库的 master 分支，而 Project Pages 将使用 gh-pages 分支。
4、User Pages 通过 http(s)://username.github.io 进行访问，而 Projects Pages通过 http(s)://username.github.io/projectname 进行访问。
更多详情：[User/Organization and Project Pages](https://help.github.com/articles/user-organization-and-project-pages/)

### Clone 刚才创建好的远程库到本地
这里有两种方式把远程库复制到本地：
1、第一种方法是在你想要存储的文件夹内鼠标右键选择`Git Bash Here`（前提是你安装了[Git](https://git-scm.com/downloads)）然后直接使用 `$ git clone https://github.com/CJCSDN/CJCSDN.github.io.git` 拷贝仓库，这里的https链接换成你自己的远程库https链接；![拷贝仓库](04.png)
或者使用 `$ git clone git@github.com:CJCSDN/CJCSDN.github.io.git` 拷贝仓库，这里的ssh协议链接换成你自己的远程库ssh协议链接；![拷贝仓库](05.png)这种方式就要你生成SSH并进行配置了，可自行搜索教程配置。我使用的是https链接拷贝，[更多介绍点这里](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375233990231ac8cf32ef1b24887a5209f83e01cb94b000)。
2、第二种方法更加快捷，直接打开[GitHub Desktop](https://desktop.github.com/)（前提是你安装了）直接上图吧：![步骤截图](06.png)![步骤截图](07.png)![步骤截图](08.png)


### 创建master与hexo分支
创建两个分支：master 与 hexo。master是默认的，所以创建hexo分支并切换将其设为默认，只需要手动管理这个分支上的hexo网站文件。简单地说，每个想建立GitHub Pages的仓库，起码有两个分支，一个（hexo）用来存放Hexo网站的文件，一个（master）用来发布网站。
1、创建本地分支hexo并切换分支到hexo：`$ git checkout -b hexo` 它是下面两条命令的简写：
```
$ git branch hexo   //创建分支
$ git checkout hexo   //切换分支
```
**注：**hexo是分支名称，可以随便定义，以下是扩展操作分支命令。此步骤可以执行前五点亦可，其余按实际情况使用。
2、列出本地分支：`$ git branch` 列出的分支中前面带“ * ”的就是当前默认分支![列出分支](03.png)
3、列出远程分支：`$ git branch -r` 列出的分支中 `origin/HEAD ->` 就像一个指针，表示默认分支![列出分支](09.png)
4、列出远程和本地分支：`$ git branch -a` ![列出分支](010.png)
5、本地分支push到服务器上：`$ git push origin hexo` hexo是分支名称，可以随便定义。然后可以在远程库刷新查看![列出分支](011.png)
6、删除本地分支：`$ git branch -d dev` 这里的dev是本地的分支名称，可以列出分支对应删除不需要的分支。
7、删除远程分支：`$ git push origin :dev` 这里的dev是远程的分支名称，可以列出分支对应删除不需要的分支。本条慎重使用，请勿失手操作。
8、合并某分支到当前分支：`$ git merge dev` 这里的dev是分支名称。
9、如果想把本地的某个分支dev提交到远程仓库，并作为远程仓库的master分支，或者作为另外一个名叫dev的分支，如下：
```
$ git push origin dev:master         // 提交本地dev分支作为远程的master分支
$ git push origin dev:dev              // 提交本地dev分支作为远程的test分支
```

### 开始安装HEXO
1、所有准备完成后，即可使用 npm 安装 [Hexo](https://hexo.io/zh-cn/docs/)。在本地CJCSDN.github.io文件夹下通过Git bash依次执行：
```
$ npm install -g hexo-cli
$ hexo init
$ npm install
$ npm install hexo-deployer-git //（此时当前分支应显示为hexo，如果不确定请看前面命令列出列表，切换设置为默认分支）
```
2、修改网站的配置信息_config.yml中的deploy参数，分支应为master
```
deploy:
  type: git
  repo: https://github.com/CJCSDN/CJCSDN.github.io.git
  branch: master
```
3、依次执行
```
$ git add .             //注意最后的.(点号),这个.(点号)表示当前目录
$ git commit -m “…”     //“引号这里写你要提交的信息，例如：git commit -m “文章更新” ”
$ git push origin hexo  //提交网站相关的文件到hexo分支上（此时当前分支应为hexo），便于更换电脑或者重装数据恢复；
```
4、执行
```
$ hexo clean        //清除缓存和已生成的静态文件
$ hexo generate -d  //生成静态文件并部署
```
生成网站并部署到GitHub上。`$ hexo generate -d`它是下面两条命令的简写：
```
$ hexo generate   //自动生成静态文件 (public)
$ hexo deploy     //将生成的静态页面部署到GitHub master分支上用于展示
```
如果部署不生效运行 `$ hexo clean` 清除缓存文件 (db.json) 和已生成的静态文件 (public)。然后再运行 `$ hexo deploy clean` 部署到GitHub刷新页面查看。
***关于部署这一点做一个延伸：就是生成后的静态文件代码不是压缩的，所以如需要压缩再部署按照如下步骤进行。**
4-1、在本地站点的根目录（CJCSDN.github.io文件夹下，这是我的站点文件夹。）执行以下命令：
```
$ npm install gulp -g
$ npm install gulp-minify-css gulp-uglify gulp-htmlmin gulp-htmlclean gulp --save
```
4-2、然后在站点根目录下新建`gulpfile.js`文件![站点根目录下新建gulpfile.js文件](012.png)，并填入以下JS代码内容。
```javascript
var gulp = require('gulp');
var minifycss = require('gulp-minify-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
// 压缩 public 目录 css
gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss())
        .pipe(gulp.dest('./public'));
});
// 压缩 public 目录 html
gulp.task('minify-html', function() {
  return gulp.src('./public/**/*.html')
    .pipe(htmlclean())
    .pipe(htmlmin({
         removeComments: true,
         minifyJS: true,
         minifyCSS: true,
         minifyURLs: true,
    }))
    .pipe(gulp.dest('./public'))
});
// 压缩 public/js 目录 js
gulp.task('minify-js', function() {
    return gulp.src('./public/**/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 执行 gulp 命令时执行的任务
gulp.task('default', [
    'minify-html','minify-css','minify-js'
]);
```
替换第4步骤，生成网站并部署到GitHub上依次执行：
```
$ hexo clean     //清除缓存和已生成的静态文件
$ hexo generate  //自动生成静态文件 (public)
$ gulp           //根据 gulpfile.js 中的配置对 public 目录中的静态资源文件进行压缩
$ hexo deploy    //将压缩的静态页面部署到GitHub master分支上用于展示
```
5、本地启动服务器`$ hexo server`。默认情况下，访问网址为： http://localhost:4000/

***hexo 命令支持简写，自行查阅，这里就不多说了。**
这样一来，在GitHub上的CJCSDN.github.io仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页。
自此hexo安装和部署就全部完成。更换主题，修改配置文件装饰等等后面在慢慢说。

## 四、博客管理流程
### 日常修改
在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理：
1、依次执行
```
$ git add .             //注意最后的.(点号),这个.(点号)表示当前目录
$ git commit -m “…”     //“引号这里写你要提交的信息，例如：git commit -m “文章更新” ”
$ git push origin hexo  //提交网站相关的文件到hexo分支上（此时当前分支应为hexo），便于更换电脑或者重装数据恢复；
```
2、然后再依次执行
```
$ hexo clean     //清除缓存和已生成的静态文件
$ hexo generate  //自动生成静态文件 (public)
$ gulp           //根据 gulpfile.js 中的配置对 public 目录中的静态资源文件进行压缩
$ hexo deploy    //将压缩的静态页面部署到GitHub master分支上用于展示
```
***注意： 每次换电脑进行博客更新时，不管上次在其他电脑有没有更新，最好先执行`$ git pull`拉取远程库上最新数据**

### 本地资料丢失情况
当重装电脑之后，或者想在其他电脑上修改博客，可以使用下列步骤：
1、使用 `$ git clone https://github.com/CJCSDN/CJCSDN.github.io.git` 拷贝仓库（默认分支为hexo）
2、在本地新拷贝的CJCSDN.github.io文件夹下通过Git bash依次执行下列指令：
```
$ npm install hexo
$ npm install
$ npm install hexo-deployer-git //（此时当前分支应显示为hexo，记得，不需要`hexo init`这条指令）
```
然后就可以修改推送等操作了。

### 部署常用命令流程
```
$ hexo new "postName"   //新建文章,hexo官网有详细说明
$ git add .             //注意最后的.(点号),这个.(点号)表示当前目录
$ git commit -m “…”     //“引号这里写你要提交的信息，例如：git commit -m “文章更新” ”
$ git push origin hexo  //提交网站相关的文件到hexo分支上（此时当前分支应为hexo），便于更换电脑或者重装数据恢复；
$ hexo clean            //清除缓存和已生成的静态文件
$ hexo generate         //自动生成静态文件 (public)
$ gulp                  //根据 gulpfile.js 中的配置对 public 目录中的静态资源文件进行压缩
$ hexo deploy           //将压缩的静态页面部署到GitHub master分支上用于展示
```
## 五、参考文献
http://crazymilk.github.io/2015/12/28/GitHub-Pages-Hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/#more
https://www.cnblogs.com/visugar/p/6821777.html
http://dontcry2013.github.io/2016/03/02/hexo-change-workstation/
http://shenzekun.cn/hexo%E7%9A%84next%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE%E6%95%99%E7%A8%8B.html
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000
https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/markdown-basics?id=%e8%af%ad%e6%b3%95%e8%af%b4%e6%98%8e