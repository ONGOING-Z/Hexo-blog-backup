---
layout: '[layout]'
title: Install Yahei Consolas Hybrid font in linux mint
date: 2020-04-16 16:18:51
tags: 
    - Font
    - Linux
categories: 
    - Linux mint

abbrlink: Install-Yahei-Consolas-Hybrid-font-in-linux-mint
---
由于刚刚安装的Linux mint终端中的中文字体显示为**楷体**，但是这个楷体在终端中显示有些问题：字与字之间空隙很大。所以就打算换一款字体。

---
<!-- toc -->

----

### 1 | 字体介绍及下载
关于`Yahei Consolas Hybrid`这个字体我是从[怎样修改终端字体](https://forum.ubuntu.org.cn/viewtopic.php?p=1312510)这篇文章中发现的。关于这款字体linux公社有一篇文章[^1]，其中有这样一段描述:
> Consolas雅黑混合字体是什么？？Consolas是一种专门为编程人员设计的字体,这一字体的特性是所有字母、数字与符号均能非常容易辨认！而且所有字符都具有相同的宽度，让编程人员看着更舒服，当然在打个人和商业信函的时候，用这个字体也是不错的选择，这一字体还专门为ClearType做了优化，可以让它更舒适地展示在屏幕上。

这款字体的下载链接在这里[^2]。

### 2 | 字体的安装

将`YaHei.Consolas.1.11b.rar`解压，得到`YaHei.Consolas.1.11b.ttf`。

之后在linux mint 系统字体文件夹中建立对应的字体文件夹
```
sudo mkdir /usr/share/fonts/vista
```
复制字体文件到对应的文件夹下
```
sudo cp YaHei.Consolas.1.11b.ttf /usr/share/fonts/vista
```
更改字体文件权限
```
sudo chmod 644 /usr/share/fonts/vista/YaHei.Consolas.1.11b.ttf
```
刷新并安装字体
```
sudo mkfontscale && sudo mkfontdir && sudo fc-cache -fv
```

### 3 | 安装之后设置字体

在mint的左下角`Menu`中搜索`appearance`，打开。如下边这个界面

![Appearance Preferences_001](Install-Yahei-Consolas-Hybrid-font-in-linux-mint/Appearance_Preferences_001.png)
在这里面可以设置应用字体，文档字体，桌面字体，窗口标题字体等等。

下面设置**终端字体**
打开终端，在终端左上角`Edit -> Profiles`，打开

![Profiles_002](Install-Yahei-Consolas-Hybrid-font-in-linux-mint/Profiles_002.png)
点击右边的`Edit`, 就可以在`General`界面下的`font`进行选择字体了，在其中选择我们之前已经安装好了的Yahei Consolas Hybrid字体即可。

![Editing_Profile_Default_004](Install-Yahei-Consolas-Hybrid-font-in-linux-mint/Editing_Profile_Default_004.png)


### 全部参考文档
[1] [怎样修改终端字体](https://forum.ubuntu.org.cn/viewtopic.php?p=1312510)
[2] [Consolas雅黑混合版yahei consolas hybrid编程字体下载](https://www.linuxidc.com/Linux/2011-08/40747.htm)
[3] [下载yahei consolas hybrid字体](https://linux.linuxidc.com/linuxconf/download.php?file=Li9saW51eGZpbGVzL3B1Yi9PdGhlci/X1szlL0NvbnNvbGFz0cW62rvsus+w5nlhaGVpIGNvbnNvbGFzIGh5YnJpZLHgs8zX1szlz8LU2C8lNUJMaW51eElEQy5jb20lNURZYUhlaS5Db25zb2xhcy4xLjExYi5yYXI=)
[4] [Linux下设置雅黑-Consolas混合字体](https://www.cnblogs.com/MonkeyF/archive/2013/05/13/3076466.html)
[5] [ubuntu安装微软雅黑和Consolas字体](https://www.iteye.com/blog/fooler5-2406227)

[^1]: [Consolas雅黑混合版yahei consolas hybrid编程字体下载](https://www.linuxidc.com/Linux/2011-08/40747.htm)
[^2]: [下载yahei consolas hybrid字体](https://linux.linuxidc.com/linuxconf/download.php?file=Li9saW51eGZpbGVzL3B1Yi9PdGhlci/X1szlL0NvbnNvbGFz0cW62rvsus+w5nlhaGVpIGNvbnNvbGFzIGh5YnJpZLHgs8zX1szlz8LU2C8lNUJMaW51eElEQy5jb20lNURZYUhlaS5Db25zb2xhcy4xLjExYi5yYXI=)
