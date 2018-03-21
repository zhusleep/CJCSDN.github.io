---
title: 一个项目push到多个远程Git仓库
date: 2018-02-27 10:01:03
tags: 
    - git
categories: git
---
>创建一个项目，然后通过命令 `push` 到了 `GitHub` 的仓库上，如何再将这个项目 `push` 到其他远程仓库用于协同、备份或者保管等别的用处时，我们该怎么做呢？如何才能一个`push`就能把我们的代码推送到多个远程仓库，而且还可以单独管理等呢？请接着往下看！

### 方法一：使用 git remote add 命令
1、使用如下命令： 
```bash
$ git remote  //查看远程仓库名字
$ git remote -v  //查看远程仓库链接
```
查看远程库的的情况，可以看到只有一个叫`origin`的远程库以及远程库fetch和push链接，如下图：![查看远程库](01.png)
2、接着使用如下命令添加一个远程仓库（这里以coding为例）
```bash
$ git remote add coding https://git.coding.net/cjcsdn/CJCSDN.git   //添加一个远程仓库叫coding后面是这个远程仓库的地址
```
然后用如下命令：
```bash
$ git remote  //查看远程仓库名字
$ git remote -v  //查看远程仓库链接
```
可以查看是否添加成功，成功如图所示：![查看远程库](02.png)然后再使用相应的命令 `push` 到对应的仓库就行了，例如：
```bash
$ git push origin master //这里是push到远程主机origin上的对应master分支
$ git push coding master //这里是push到远程主机coding上的对应master分支
```
这种方法的缺点是每次要`push`两次,因为是两个不一样的远程库名。

### 方法二: 使用 git remote set-url 命令
1、使用`$ git remote rm coding`命令删除方法一中的`coding`远程仓库，检查是否删除成功用前面列出的查看远程仓库命令，如下图：![查看远程库](03.png)。
2、接着使用如下命令添加一个远程仓库（这里添加相同名称的库为origin）
```bash
$ git remote set-url --add origin https://git.coding.net/cjcsdn/CJCSDN.git
```
3、查看远程仓库情况，可以看到远程主机仓库列表有两个 `push` 地址。这种方法的好处是每次只需要 `push` 一次就行了,如下图：![查看远程库](04.png)

### 方法三: 修改配置文件.git/config
1、打开本地项目中 `.git/config` 文件找到 [remote "origin"]（这里根据个人的实际显示），添加对应的 `url` 即可。这种方法其实和方法二是一样的，好处也是和方法二一样每次只需要 `push` 一次就行了,如下图：![查看远程库](05.png)

### 总结
方法二和方法三在 `push` 的时候比较方便。但是在 `pull` 的时候只能从方法三图中的第一个 `url` 地址拉取代码。而方法一则不存在这种问题（可能要解决冲突）。所以，如果只进行 `push` 操作，推荐方法二和方法三，如果也要进行 `pull` 操作，推荐方法一。
