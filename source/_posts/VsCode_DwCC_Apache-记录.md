---
title: VsCode_DwCC_Apache-记录
date: 2017-12-25 17:55:50
tags: 
    - vsCode
    - dwCC
    - Apache
categories: 个人记录
---
### vsCode记录
vsCode安装扩展：
1、Atom One Dark Theme；2、Auto Close Tag；3、Auto Rename Tag；4、AutoFileName；5、beautify；6、cssrem；
7、Debugger for Chrome；8、EasySass；9、EditorConfig for VS Code；10、ESLint；11、Git History；
12、Git Project Manager；13、GitLens；14、HTML CSS Support；15、HTML SCSS Support；16、HTML Snippets；
17、 JavaScript Standard Style；18、jQuery Code Snippets；19、language-Stylus；20、Live Sass Compiler；
21、Live Server；22、Markdown Preview Enhanced；23、npm；24、Npm Intellisense；25、One Dark Pro；
26、Open HTML in Default Browser；27、Path Intellisense；28、Sass；29、SCSS IntelliSense ；30、Swig；31、TSlint；
32、Typings auto installer；33、Vetur；34、vscode-icons；35、Vue 2 Snippets；36、Vue VSCode Snippets；37、XML Tools

vsCode用户设置：
```json
{
    "git.enabled": false,
    "git.autorefresh": false,
    "workbench.colorTheme": "Atom One Dark",
    "editor.fontSize": 14,
    "workbench.iconTheme": "vscode-icons",
    "liveServer.settings.donotShowInfoMsg": true,
    "liveServer.settings.port": 8080,
    "liveServer.settings.root": "D:/myweb/htmlproject/template/",
    "explorer.confirmDelete": false,
    /** Easy Sass 插件 **/
    "easysass.formats": [
        {
        "format": "compressed", //输出样式"nested", "expanded", "compact" or "compressed"
        "extension": ".css"
        }
/*         {
            "format": "compressed",//输出样式
            "extension": ".min.css"
        } */
    ],
    "easysass.targetDir": "./css/", // 自定义css输出文件路径
    "easysass.compileAfterSave": false, // 保存sass不自动编译
    /** Live Sass Compile Config  插件 **/
    "liveSassCompile.settings.formats": [
        {
            "format": "compressed", //输出样式
            "extensionName": ".css",
            "savePath": "/css/" // 自定义css输出文件路径
        }
    ],
    //"liveSassCompile.settings.generateMap": false, //sass关闭编译css后的Source Map
    "editor.minimap.enabled": false,
    "window.zoomLevel": 0 //编辑器右边代码缩略图
}
```

### dwCC记录
1、设置：
```
首选项（分类列表中）
    ├── 常规
    |     └── 选择“仅限对活动文档执行撤销操作”
    ├── 代码提示
    |     ├── 选择“键入起始标签‘>’后”
    |     └── 选择“启用代码提示”
    ├── 代码格式
    |     ├── 缩进去掉勾选
    |     └── 制表符大小：2
    ├── 字体
    |     ├── 字体设置：unicode
    |     ├── 均衡字体：Times New Roman、大小：12pt
    |     ├── 固定字体：Courier New、大小：10pt
    |     ├── 代码视图：Consolas、大小：12pt
    |     └── 制表符大小：2
    └── 界面
          ├── 应用程序主题：最后一个
          └── 代码主题：选择‘Solarized Light’点击‘+’号新建自定义命名
                └── 然后点击修改打开文件：把‘@background’改为‘@background: #FeF9dd’，重启就可以使用;      
```
2、站点管理：
一般导出站点文件.ste，在新的设备使用的时候导入即可。

### Apache记录
这里说的是Windows系统重装后Apache的恢复。
运行cmd后cd到你的Apache安装目录bin下：
```cmd
C:\Users\Administrator>d:

D:\>cd D:\myweb\htmlproject\template\Apache2.2\bin

D:\myweb\htmlproject\template\Apache2.2\bin>httpd /?
Usage: httpd [-D name] [-d directory] [-f file]
             [-C "directive"] [-c "directive"]
             [-w] [-k start|restart|stop|shutdown]
             [-k install|config|uninstall] [-n service_name]
             [-v] [-V] [-h] [-l] [-L] [-t] [-S]
Options:
  -D name            : define a name for use in <IfDefine name> directives
  -d directory       : specify an alternate initial ServerRoot
  -f file            : specify an alternate ServerConfigFile
  -C "directive"     : process directive before reading config files
  -c "directive"     : process directive after reading config files
  -n name            : set service name and use its ServerConfigFile
  -k start           : tell Apache to start
  -k restart         : tell running Apache to do a graceful restart
  -k stop|shutdown   : tell running Apache to shutdown
  -k install         : install an Apache service
  -k config          : change startup Options of an Apache service
  -k uninstall       : uninstall an Apache service
  -w                 : hold open the console window on error
  -e level           : show startup errors of level (see LogLevel)
  -E file            : log startup errors to file
  -v                 : show version number
  -V                 : show compile settings
  -h                 : list available command line options (this page)
  -l                 : list compiled in modules
  -L                 : list available configuration directives
  -t -D DUMP_VHOSTS  : show parsed settings (currently only vhost settings)
  -S                 : a synonym for -t -D DUMP_VHOSTS
  -t -D DUMP_MODULES : show all loaded modules
  -M                 : a synonym for -t -D DUMP_MODULES
  -t                 : run syntax check for config files
```
根据帮助信息，执行
```cmd
D:\myweb\htmlproject\template\Apache2.2\bin>httpd.exe -k install
```
apache就注册成为windows的服务了，用
```cmd
D:\myweb\htmlproject\template\Apache2.2\bin>net start apache2.2
```
