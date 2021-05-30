---
title: 那些WSL中踩过的坑
date: 2020-03-15 17:20:34
tags: 
 - Linux
 - WSL
---
不小心把.bashrc删掉了?把.bashrc玩崩溃了?默认的.bashrc在`/etc/skel/.bashrc`

不喜欢换源,但是怎么让apt用主机的代理呢?

```bash
 export http_proxy=http://yourproxyaddress:proxyport
```
貌似没什么用. apt还是我行我素的直连

后来发现得修改`/etc/apt/apt.conf`并添加

```bash
Acquire::http::Proxy "http://yourproxyaddress:proxyport";
Acquire::ftp::proxy "ftp://yourproxyaddress:proxyport";
Acquire::https::proxy "https://yourproxyaddress:proxyport";
```

才行..

git就容易一些;
添加代理:

```bash

git config --global https.proxy http://127.0.0.1:1080

git config --global https.proxy https://127.0.0.1:1080

```

取消代理:

```bash

git config --global --unset http.proxy

git config --global --unset https.proxy

```

当然, 直接上*软路由*或者*proxychains*就可以一劳永逸了..