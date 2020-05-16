---
title: wps-for-linux的字体添加及配置
copyright: true
date: 2020-05-16 08:38:48
tags:
categories: Tools
abbrlink: the-font-configuration-of-wps-for-linux
---
这两天需要在wps中写点东西，但是里边并没有word中中文的大部分字体，所以需要添加一些字体。

---
<!-- toc -->

---

因为我的系统(ubuntu16.04)默认的是英文环境，所以在wps的字体选项中没有一个中文选项，就先将系统默认环境改成了中文。
在系统应用中搜索`language support`，然后将选择语言中的`中文`调到第一项中，之后`应用到整个环境`，这些都做完之后，登出重新登录。

现在打开wps for linux，我发现字体选项中多了几种中文字体，但是常见的字体如"宋体"/“黑体”这些并没有。所以需要为wps配置字体。

## 配置字体步骤
(1) 如果旁边有另一台配置windows系统的电脑或者本机里有windows电脑，就很方便，直接从`C:\windows\fonts\`下复制字体文件，需要什么字体就在文件夹下搜索字体名称即可。

(2) 将复制的字体拷贝到ubuntu下的`/usr/share/fonts/`下，下一步执行以下命令，生成字体的索引信息：
```bash
sudo mkfontscale
sudo mkfontdir
sudo fc-cache
```

(3) 重启wps后发现字体选项中中文字体出现了我们新添加的几种字体。

## 参考
[1] [Ubuntu下WPS中文字体显示问题](https://blog.csdn.net/liweibin1994/article/details/73384790)
