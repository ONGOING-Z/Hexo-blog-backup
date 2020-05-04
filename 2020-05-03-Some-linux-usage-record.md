---
layout: '[layout]'
title: Some linux usage record
date: 2020-05-03 23:10:08
tags:
    - Linux
categories: 
    - Fundamental
abbrlink: some-linux-usage-record

---
记录自己在使用linux中渐渐使用的命令和一些方法。

---
<!-- toc -->

---
1. 在一个终端中打开另一个窗口
```
ctrl + shift + t
```
2. 回到上一次目录
```
cd -
```
3. 列出当前登录用户
```bash
w
```
4. Linux进出sudo的方法

    进入`sudo`mode: `sudo -i`
    退出`sudo`mode: `ctrl + d`

5. grep(general regular expression print)
   `ls | grep "linux"`: List file that its name includes string "linux".

6. Clear commands history
  `history -c`

7. 终端锁定与退出锁定(终端无法输入的假死问题)[^1]
  - 终端锁定
      `ctrl + s`
  - 退出锁定
      `ctrl + q`

8. File permission
  - `chmod`
      Change mode.
      10number: `d`(directory) or `-`(that represents file)
      Permission:
        - `r`: (100)<sub>2</sub> //4
        - `w`: (010)<sub>2</sub> //2
        - `x`: (001)<sub>2</sub> //1
      eg. `chmod 777 file/dir`  // Give file/dir rwx permission.
  - `chgrp`
      Change file group.
  - `chown`
      Change file owner.

9. Change font size in terminal

    Change bigger: `ctrl -`
    Change smaller: `ctrl +`

10. Rename

    将test.jpg改成test1.jpg
    ```bash
    mv {test,test1}.jpg
    ```

11. 在linux中跳出很深的文件夹，如果没有记住文件路径，就要一层层`cd`过去，浪费很多的时间。

    解决方法1
    在`/etc/profile.d/`目录下新建例如`dd.sh`文件，文件内容如下
    ```bash
    alias dd='cd /media/folder1/folder2/.../'
    ```
    接下来保存退出
    ```bash
    source dd.sh
    ```
    效果: 在命令行中输入`dd`即可实现挑入指定目录。
    并且重启之后在命令行中依然生效。

    解决方法2
    在`~/.bashrc`中添加
    ```bash
    alias dd='cd /media/folder1/folder2/.../'
    ```
    也可以有同样的效果。

12. Linux光标移动

    `ctrl + a`: 行首
    `ctrl + e`: 行尾

    `ctrl + f`: 光标右移
    `ctrl + b`: 光标左移

    `esc + f`: 右移一个单词
    `esc + b`: 左移一个单词

13. Linux mv
    功能
    (1) 修改名称
    (2) 移动文件

14. Bash
    (1) 注释: `#`
    (2) `#!/bin/bash`的意义
    以`#`代表是个注释，但是`#!`并不是注释了，它用来指明这个脚本所需要的`Shell`
    (3) shell变量类型
    变量类型只有字符串

15. caps -> ctrl(reference 32)

16. Download video in CLI
    (1) you-get
    (2)youtube_dl

17. du(disk usage)
18. ctrl + u: 从光标处删除文本直到行首
19. ctrl + k: 从光标处删除文本直到行尾
20. alt + f: 向后一个单词
21. alt + b: 向前一个单词
22. 重复使用上一个命令: `!!`
23. dstat
    View the net speed in late 10 seconds and other functions.
24. Symbolic links

25. I/O redirection
> I/O redirection allows us to change where output goes and where input comes from. Normally, output goes to the screen and input comes from the keyboard, but with I/O redirection we can change that.

26. The Letter-Based Method
    > In addition to the method described above there is a second way to change permissions. Chmod uses either the hexadecimal representation of the permissions or a letter-based representation. The letter-based representation is [ugoa][+-][rwx]. This is one of the letters u (user=file owner), g (group), o (others), a (all users, groups and others); followed by + or - to add or remove permissions; and then the symbolic representation of the permissions in the form of r(read) w(write) x(execute). To extend Write permissions to all for the file "file.txt",

    For example, you would type:
    ```bash
    chmod a+w file.txt
    ```

27. command - uptime

    Tell how long the system has been running.

28. Change user

    ```
    su [username]
    ```
    退出此用户: `exit`

29. Add user

    ```bash
    useradd [username]
    passwd [username]
    ```

30. Delete user

    ```bash
    userdel [-r] [username]
    ```
    -r: remove the home dir of [username]

31. Print current effective user

    ```bash
    whoami
    ```

32. linux将cpas->ctrl

    (1) Edit `/etc/default/keyboard`

    ```diff
    # KEYBOARD CONFIGURATION FILE

    # Consult the keyboard(5) manual page.

    XKBMODEL="pc105"
    XKBLAYOUT="cn"
    XKBVARIANT=""
    - XKBOPTIONS=""
    + XKBOPTIONS="ctrl:nocaps"

    BACKSPACE="guess"
    ```
    (2) 运行如下命令，设置生效
    ```bash
    sudo dpkg-reconfigure keyboard-configuration
    ```
33. cp 排除某个目录

    eg. 有目录b, c, 复制到/f下，排除b
    ```
    cp -r !(b) /f
    ```

----

### Linux各目录
#### etc
1. 含义: and so on
2. 功能: 存放零零碎碎的东西

### linux各种解压命令汇总

#### `.tar.xz`
```
$xz -d filename.tar.xz
$tar -xvf filename.tar
```
#### `tar.gz`
```
tar -zxvf xxx.tar.gz
```
#### `.rar`

```
unrar e file.rar # e: 解压压缩包中的全部问价至文件夹
```

今天因要下载win10 iso文件，奈何文件太大，只好利用winrar软件将4g的iso文件分成了4个1g的小文件，转到linux下后，直接将4个小文件提取了出来，但问题是4个提取出来的文件并没有合并在一起，这可不是我想要的结果，百度一查，赶紧在linux安装了rar,只需用`rar e name.part1.rar`，提取后的文件就是合并后的文件了。

----
### Problems

#### 在ubuntu19.01上安装curl出现问题curl : Depends: libcurl4 (= 7.58.0-2ubuntu3.8) but 7.65.3-1ubuntu3 is to be installed

问题如下
```
The following packages have unmet dependencies:
curl : Depends: libcurl4 (= 7.58.0-2ubuntu3.8) but 7.65.3-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.
```
解决方法:
```
sudo apt-get purge libcurl4
```
接下来就可以正常安装`curl`了。

#### linux升级gdb

gdb官网下载太慢，[清华大学镜像站](https://mirrors.tuna.tsinghua.edu.cn/gnu/gdb/)可以下载

[^1]: https://www.cnblogs.com/guochaoxxl/p/10428991.html
