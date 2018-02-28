---
title: 'hexo问题'
date: 2018-02-28 15:36:28
tags: hexo
categories: hexo
---
在新的设备（win10）系统clone库到本地，一顿操作后使用命令`hexo -v`等命令都出现`bash: hexo: command not found`,要不就是“'hexo' 不是内部或外部命令,也不是可运行的程序 或批处理文件。”再要不就是出现“hexo : 无法将“hexo”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径正确，然后再试一次。所在位置 行:1 字符: 1”。在命令行中输入node -v 然后再检查npm -v。都是正常的，就是hexo的命令不能使用。于是查找资料亲测可行后总结如下：
在环境变量PATH后面添加上你的博客node_modules下的.bin ，例如我的：
```
D:\myweb\GitHub\CJCSDN.github.io\node_modules\.bin
```
这时候再从新打开你的命令窗口运行hexo -v,这些hexo的命令就可以正常使用了。如果你有更好的办法请再下面留言，我会积极采纳，谢谢！
