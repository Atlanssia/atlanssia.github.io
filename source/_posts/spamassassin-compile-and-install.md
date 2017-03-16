---
title: spamassassin-compile-and-install
date: 2017-03-16 16:44:07
tags:
---

## 准备
下载源代码

```
http://spamassassin.apache.org
```

## 依赖
spamassassin的编译依赖以下perl模块：

```
REQUIRED module : NetAddr::IP
optional module : Digest::SHA1
optional module : Mail::SPF
optional module : Geo::IP
optional module : Net::CIDR::Lite
optional module : Razor2
optional module : Mail::DKIM
optional module : DBI
optional module : Encode::Detect::Detector
optional module : Net::Patricia
optional binary : fetch
```

## 编译和安装
解压源代码，在源代码工程root路径下：

``` bash
$ export LC_ALL=C
$ perl Makefile.PL
$ make
$ sudo make install
```

## 配置和启动

TODO