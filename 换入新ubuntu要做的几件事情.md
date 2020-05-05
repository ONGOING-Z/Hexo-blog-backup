---
layout: '[layout]'
title: 换入新ubuntu要做的几件事情
date: 2020-04-04 13:11:08
categories: "Ubuntu"
abbrlink: things-should-be-donw-when-change-into-new-ubuntu
---
记录自己换入新ubuntu系统后的一些操作。

---
<!-- toc -->

----

## 换源

到阿里云或者其他镜像网站复制对应安装版本的源

## Install vim 8+

安装vim的方式
- 将源文件下载下来后可以采用编译的方法进行。
- 在命令行中安装
    ```
    sudo apt install vim
    sudo apt install vim-gtk3
    ```

安装完毕后安装`vim-plug`，其作用是管理vim的插件。安装有以下两种方式
- 在终端中键入下边命令
    ```
    curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
    ```
- 将[plug.vim](https://github.com/ONGOING-Z/dotfiles)下载下来后移入`~/.vim/autoload`文件夹下即可使用。
**注**: 使用vim-plug必须先安装git，不然不能使用!
使用自己的[.vimrc](https://github.com/ONGOING-Z/dotfiles)

## Install tmux

```
sudo apt install tmux
```
使用自己的[.tmux.conf](https://github.com/ONGOING-Z/dotfiles)

## Git

```
sudo apt install git
```
## Install googlepinyin

在`text entry setting`可以设置，可能出现安装之后重新启动又得再次选择输入法的情况．
- 在命令行中输入`fcitx`，检查其是否已经安装，如果未安装，执行`sudo apt install fcitx`进行安装。
- 在命令行中执行`im-config`(Input Method Configuration)，进行一番点击之后在选择面板中选择**fcitx**
- 安装**googlepinyin**，在命令行中执行`sudo apt install fcitx-googlepinyin`
- 重启电脑，使配置生效。(注意: 不重启有可能在接下来的步骤看不到googlepinyin的选项哦！)
- 在命令行中执行`fcitx-config-gtk3`，打开配置面板:
  - 点击`+`
  - **不要勾选**Only Show Current Language，搜索一下就可以看到`googlepinin`了，加入即可。
**注**: googlepinyin对于ubuntu20也同样适用。

## Install chrome

- CLI安装
```
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable
```
- 到Chrome官网直接下载`.deb`包进行安装
    手动安装: `sudo dpkg -i xxx.deb`

## 卸载不必要软件

当然如果在安装过程中选择了`最小安装`，就直接跳过此步，因为那种最小安装方式只会安装浏览器和一些必要组件。
```
# 删除Amazon广告图标
sudo apt-get -y purge gedit* 
sudo rm -f /usr/share/applications/com.canonical.launcher.amazon.desktop
sudo rm -f /usr/share/applications/ubuntu-amazon-default.desktop
# 其他软件
#邮件
sudo apt-get -y purge thunderbird*
#火狐浏览器
sudo apt-get -y purge firefox
#备份
sudo apt-get -y purge deja-dup
#扫描
sudo apt-get -y purge simple-scan
#打印
sudo apt-get -y purge hplip* 
#打印驱动
sudo apt-get -y purge printer-driver* 
#音乐播放
sudo apt-get -y purge rhythmbox* 
#文本编辑
sudo apt-get -y purge gedit* 
#办公套件
sudo apt-get -y purge libreoffice* 
#屏幕阅读
sudo apt-get -y purge gnome-orca 
#屏幕键盘
sudo apt-get -y purge onboard 
#对对碰
sudo apt-get -y purge mahjongg 
#纸牌王
sudo apt-get -y purge aisleriot 
#数独
sudo apt-get -y purge gnome-sudoku 
#扫雷
sudo apt-get -y purge gnomine 
#命令刻碟
sudo apt-get -y purge wodim 
```

卸载内置视频软件`totem`，没有太多功能，使用`smplayer`代替
```
sudo apt purge totem
```

## Install xdm

`xdm`是一款下载软件，使用过后发现下载速度相对浏览器下载会比较快。
[这个链接](https://hansteam.coding.net/s/7ab96bda-abd0-4f4c-80a3-899f07cb7f3b)是一位博主的，xdm官网在国外，下载很慢，这里下载会比较快。
- 使用xdm在chrome官网下载.deb包
- 使用xdm在vmware官网下载.deb包

## Display netspeed
```
$sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor
$sudo apt-get update
$sudo apt-get install indicator-sysmonitor
$indicator-sysmonitor &
```
启动之后就可以在屏幕右上角出现网速了。
右键右上角图标，勾选run on startup，使其开机启动。

## ~~系统负载指示器~~

```
sudo apt-get install  indicator-multiload
```
*没啥用，是图形化的，不能显示数据*

## Unity tewak tool

作用：
  - 可以隐藏侧边栏

## 设置bash字体颜色为"#82B92E"

不那么鲜艳的绿色。
设置bash bgcolor="#282828"

## 色温软件redshift

  超级不错！安装之后屏幕不会那么刺眼。
  config file is stored in `~/.config/`, the `redshift.conf` is:
  ```
  [redshift]
  ; 白天屏幕温度
  temp-day=4500
  ; 夜晚屏幕温度
  temp-night=3500
  ; 昼夜是否平滑过度(1/0)
  transition=1
  
  ; 位置提供方式(redshift -l list)
  location-provider=manual
  
  [manual]
  ; 位置提供方式设置
  ; 经纬度(北京)
  lat=39.90
  lon=116.41
  ```

## 安装命令行打字软件gtypist

之前一直是在[typing.com](https://typing.com)上来进行训练的，之后在一个帖子中突然发现了下方这个命令行软件，这里记录一下。

`gtypist`是一款GNU开源软件，可以用来训练自己的打字效率。
使用`sudo apt install gtypist`即可在ubuntu上进行安装。

但是我并未在gtypist中发现记录历史的功能，也就是说每次打开都得重新开始玩。

## 参考
[1] [Ubuntu18.04安装googlepinyin](https://www.jianshu.com/p/180cd9634b4a)
