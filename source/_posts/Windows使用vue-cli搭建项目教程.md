---
title: Windows使用vue-cli搭建项目教程
date: 2017-12-16 16:54:23
tags: 
    - 使用 vue-cli 搭建项目
    - vue
    - vue-cli
categories: 使用 vue-cli 搭建项目
---

# 一、环境介绍
**1、Node.js:** javascript运行环境(runtime),不同系统直接运行各种编程语言。
**2、npm:** Nodejs下的包管理器。由于国内使用npm会很慢,这里推荐使用淘宝NPM镜像 [https://npm.taobao.org](https://npm.taobao.org/)
```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```
**3、webpack:** 它主要的用途是通过 CommonJS 的语法把所有浏览器端需要发布的静态资源做相应的准备，比如资源的合并和打包。
**4、vue-cli:** 用户生成Vue工程模板。

# 二、 环境搭建
## 安装 node.js
**1、** 首先需要安装node环境，可以直接到node官网下载安装包安装：[node中文网](http://nodejs.cn/)、[node英文网](https://nodejs.org/en/)，[更多配置详情可点此参考](http://www.runoob.com/nodejs/nodejs-install-setup.html)。安装完成后检测`PATH`环境变量是否配置了`Node.js`，快捷键`win+R` 输入`cmd` => 输入命令`path`输出如下结果：![检测PATH环境变量](01.png)我们可以看到环境变量中已经包含了`D:\Program Files\nodejs\`然后继续分别输入`node -v` 和 `npm -v` 等待一会，显示出`node`和`npm`的版本号，就说明安装成功。如果 cmd 中运行`npm –v`光标闪烁长时间未出现版本号，npm命令完全无反应，不是加载的那种状态。请删除`C:\Users\{账户}\下的.npmrc`文件。**注意：** 不是`nodejs`安装目录`npm`模块下的那个`.npmrc`文件。

**2、** `nodejs prefix`（全局）和 `cache`（缓存）`windows`下设置：
- *2-1、* **说明：** 在安装完`nodejs`后，通过`npm`下载全局模块默认安装到`C:\Users\username\AppData\Roaming\npm`下，这当然是不太对的默认。
打开下载好的Windows安装包(.msi)安装，`nodejs`安装路径会自动添加到`PATH`环境变量；本文安装路径为：`D:\Program Files\nodejs`
- *2.2、* 在nodejs安装路径下新建文件夹`node_cache`用来存放下载包的缓存；即：`D:\Program Files\nodejs\node_cache`，修改完成之后如下图：![新建文件夹node_cache](02.png)
- *2.3、* 在`cmd`中运行 `npm config set cache "D:\Program Files\nodejs\node_cache"` 设置缓存文件夹；在`cmd`中运行 `npm config set prefix "D:\Program Files\nodejs"` 设置全局模块存放路径；
**注意：** `nodejs`会自动寻找该路径下的`node_modules`文件夹为实际存放全局模块的路径，这也是为啥`prefix`不设置`global`的原因；以后安装的全局模块都会被放到`D:\Program Files\nodejs\node_modules`下，跟`npm`模块在一个文件夹中；
- *2.4、* 修改`D:\Program Files\nodejs\node_modules\npm\npmrc`文件，将默认值改为：`prefix=D:\Program Files\nodejs`，如果不做这个修改，则`npm`在运行 `npm ls -g` 的时候，仍然以默认的路径来查找已安装的全局模块；
- *2.5、*`cmd`中运行`npm install express -g` 以全局方式安装`express`模块，可发现，在`D:\Program Files\nodejs\node_modules`下出现`express`文件夹；如下图：![出现express文件夹](03.png)
- *2.6、*`cmd`中运行`npm list -g`,列出所有全局模块。包含了express和npm两个模块，及其依赖模块；最后有洁癖的同学可以将用户环境变量中的默认路径;`C:\Users\Administrator\AppData\Roaming\npm`删除；
环境变量名`NODE_PATH`值`D:\Program Files\nodejs\node_global\node_modules`如果有也可删除；本文包含的方法，并不需要另外设置`PATH`变量；

## 安装vue-cli
**1、** 安装好了node，我们可以直接全局安装vue-cli：`cmd`中运行`npm install -g vue-cli`但是这种安装方式比较慢，推荐使用国内镜像来安装，所以我们先设置cnpm：在`cmd`中输入
```
npm install -g cnpm --registry=http://registry.npm.taobao.org
```
然后等待，安装完成如下图：![安装cnpm](04.png)如果安装失败，可以使用命令 `npm cache clean` 清理缓存，然后再重新安装。后面的安装过程中，如有安装失败的情况，也需要先清理缓存。完成后同样可以使用 `cnpm -v` 查看是否安装成功，有些会出现版本号，有些会出现一堆东西，具体看具体情况，只要不报错就OK。
**2、** 然后使用 cnpm 安装 vue-cli 和 webpack，输入命令`cnpm install -g vue-cli`等待安装完成。最新的 vue 项目模板中，都带有 webpack 插件，所以这里可以不安装 webpack，安装完成后，可以输入 `vue -V`（注意 V 大写）查看是否安装成功，成功显示版本号。如果提示“无法识别 'vue' ” ，有可能是 npm 版本过低，可以使用 `npm install -g npm` 来更新版本

# 三、 用vue-cli构建项目
**1、** 通过以上步骤，我们需要准备的环境和工具都准备好了，接下来就开始使用vue-cli来构建项目。要创建项目，首先我们要选定目录，然后在命令行中把目录转到选定的目录。在这里，我选择桌面来存放新建的项目，则我们需要先把目录cd到桌面，你也可以根据自己的路径建立项目文件夹。如下图：![存放新建的项目路径](05.png)
**2、** 在桌面目录下，在命令行中运行命令 `vue init webpack myVue` 。解释一下这个命令，这个命令的意思是初始化一个项目，其中webpack是构建工具，也就是整个项目是基于webpack的。![初始化项目](06.png)运行初始化命令的时候会让用户输入几个基本的选项，如项目名称，描述，作者等信息，如果不想填直接回车默认就好。其中myVue是整个项目文件夹的名称，这个文件夹会自动生成在你指定的目录中。本文例子生成文件夹如下图：![文件夹会自动生成在你指定的目录中](07.png)
**3、** 打开myVue文件夹，项目文件如下所示：![存放新建的项目路径](08.png)这就是整个项目的目录结构，其中，我们主要在src目录中做修改。这个项目现在还只是一个结构框架，整个项目需要的依赖资源都还没有安。要安装依赖包，首先cd到项目文件夹（myVue文件夹），然后运行命令 `cnpm install` ，等待安装。![安装依赖包](09.png)安装完成之后，会在我们的项目目录myVue文件夹中多出一个node_modules文件夹，这里边就是我们项目需要的依赖包资源。![node_modules文件夹](10.png)
**4、** 安装完依赖包之后，就可以运行整个项目了。在项目目录中，运行命令 `npm run dev` ，会用热加载的方式运行我们的应用，热加载可以让我们在修改完代码后不用手动刷新浏览器就能实时看到修改后的效果。这里简单介绍下 `npm run dev` 命令，其中的“run”对应的是package.json文件中，scripts字段中的dev，也就是 `node build/dev-server.js` 命令的一个快捷方式。![命令说明](11.png)项目运行成功后，浏览器会自动打开`localhost:8080`（如果浏览器没有自动打开，可以手动输入）。运行成功后，会看到如下所示的界面:![运行成功界面](12.png)如果浏览器打开之后，没有加载出页面，有可能是本地的 `8080` 端口被占用，需要修改一下配置文件 `config>index.js`![修改一下配置文件](13.png)建议将端口号改为不常用的端口。另外我还将 build 的路径前缀修改为 ' ./ '（原本为 ' / '），是因为打包之后，外部引入 js 和 css 文件时，如果路径以 ' / ' 开头，在本地是无法找到对应文件的（服务器上没问题）。所以如果需要在本地打开打包后的文件，就得修改文件路径。
**5、** 自己的项目文件都需要放到 src 文件夹下。项目开发完成之后，可以输入 `npm run build` 来进行打包工作。打包完成后，会生成 dist 文件夹，如果已经修改了文件路径，可以直接打开本地文件查看。项目上线时，只需要将 dist 文件夹放到服务器就行了。

