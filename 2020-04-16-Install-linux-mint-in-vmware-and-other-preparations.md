---
layout: '[layout]'
title: Install linux mint in vmware and other preparations
date: 2020-04-16 11:40:57
tags: Linux
categories: "Linux distribution"

abbrlink: install-linux-mint-in-vmware-and-other-preparations

---
因为想要将Hexo博客的书写单独分离出一个生产环境，这样之后如果宿主操作系统更换之后博客的环境就不用再次安装了，因此昨天晚上在VMware虚拟机中安装了Linux mint（之前一直使用的桌面是Ubuntu16.04），今天来写一个安装过程以及安装好之后的一些准备工作。

----
<!-- toc -->

----

## 1 | 安装

下载[Linux mint镜像文件](https://www.linuxmint.com/edition.php?id=276)，这里我下载的是`MATE`，官网可能下载的有些慢，可以使用`xdm`进行下载。
下载之后就可以使用虚拟机了，之后的安装步骤就不多说了，一些简单的步骤。

## 2 | 下载之后的使用

### 换源
### vim
```
sudo apt install vim
sudo apt install vim-gtk
```
注意将vim的桌面版本也下载上，不然可能vim的终端版本的`clipboard`没有安装上，使用`$vim version | grep "clipboard"`进行查看，如果有`+clipboard`即表示已经安装上。

### git
```
sudo apt install git
```

### tmux

### 输入法


### 离线安装nodejs[^1]

nodejs是hexo运行所必须的环境，下载[nodejs](https://cdn.npm.taobao.org/dist/node/v12.16.2/node-v12.16.2-linux-x64.tar.xz)

下载完毕后，解压，并将解压后的文件夹移入自己的某个文件夹中，这里我将文件夹放置在`/usr/local/lib/nodejs`
```
sudo mkdir /usr/local/lib/nodejs
sudo tar -xJvf node-xxx-xxx.tar.xz -C /usr/local/lib/nodejs
sudo mv /usr/local/lib/nodejs/node-xxx-xxx /usr/local/lib/nodejs/node-xxx # 更改名称
```

设置环境变量，在`/etc/profile`中，在文件最后添加
```
# Nodejs
export NODEJS_HOME=/usr/local/lib/nodejs/node-xxx/bin  # xxx是版本号
export PATH=$NODEJS_HOME:$PATH
```

刷新文件配置
```
. /etc/profile
```

测试
```
node -v
npm version
```

创建sudo链接
```
sudo ln -s /usr/local/lib/nodejs/node-xxx/bin/node /usr/bin/node
sudo ln -s /usr/local/lib/nodejs/node-xxx/bin/npm /usr/bin/npm
sudo ln -s /usr/local/lib/nodejs/node-xxx/bin/npx /usr/bin/npx
```

### 其它一些配置

**将caps lock映射为ctrl**





















[^1]: [Linux离线安装node](https://www.jianshu.com/p/7bef118592c3)
