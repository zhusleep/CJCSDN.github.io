---
title: SourceTree免登录跳过初始设置
date: 2018-05-22 16:09:58
tags: SourceTree
categories: SourceTree
---
![SourceTree出现的问题](01.png)
SourceTree 安装之后需要使用账号登陆以授权。

安装之后，转到用户本地文件夹下的 SourceTree 目录，没有则新建
```
%LocalAppData%\Atlassian\SourceTree\
```
在SourceTree新建 accounts.json 文件
文件内容：
```
[
  {
    "$id": "1",
    "$type": "SourceTree.Api.Host.Identity.Model.IdentityAccount, SourceTree.Api.Host.Identity",
    "Authenticate": true,
    "HostInstance": {
      "$id": "2",
      "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountInstance, SourceTree.Host.AtlassianAccount",
      "Host": {
        "$id": "3",
        "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountHost, SourceTree.Host.AtlassianAccount",
        "Id": "atlassian account"
      },
      "BaseUrl": "https://id.atlassian.com/"
    },
    "Credentials": {
      "$id": "4",
      "$type": "SourceTree.Model.BasicAuthCredentials, SourceTree.Api.Account",
      "Username": "",
      "Email": null
    },
    "IsDefault": false
  }
]
```