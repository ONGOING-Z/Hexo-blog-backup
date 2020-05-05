---
layout: '[layout]'
title: Git knowledge
date: 2020-04-26 13:11:41
tags:
    - Git
categories: 
    - Fundamental
abbrlink: git-knowledge
---
<!-- toc -->

### git 查看修改用户名与密码
- 查看用户名
```
git config --global user.name
```
- 修改用户名
```
git config --global user.name "your name"
```
- 查看邮箱地址
```
git config --global user.email
```
- 修改邮箱地址
```
git config --global user.email "your email address"
```

### git 本地与远程仓库关联与解除
- 查看远程仓库信息
```
git remote -v
```
- 建立新仓库
```
在github中建立一个新的仓库
可以不要README.md文件
```
- 关联
```
git remote add origin git@github.com:your_name/repository_name.git
```
- 解除关联
```
git remote remove origin
```

### GitHub快速更换绑定邮箱
（1）点击头像
（2）setting
（3）Email
（4）Add email address
（5）新邮箱验证，返回github，将新邮箱验证Set Primary.

### git 推送
```
git push -u origin master
```

### github 如何删除仓库
（1）settings
（2）页面最下方'Delete this repository'

### 查看本地与远程的连接
```
ssh -T git@github.com
```

### git在本地配置公钥
```
ssh-keygen -t rsa -C email_address
```

### 对文件或文件夹重命名

使用`git mv`即可对文件或文件夹进行`转移`或者`重命名`。
使用方法如下
```
git mv <source> <destination>
git mv <source> <destination directory>
```
*暂时还没看懂重命名文件夹是怎么做的。*

### git基本操作

```
# 初始化仓库
git init
# 取消初始化仓库
rm -rf .git/
# 查看仓库状态（哪些文件提交了，哪些文件未提交）
git status
# 添加文件至提交列表
git add filename
## 同时添加多个文件
git add filename1 filename2 (中间以空格区分)
```

### git删除add中的文件（缓存文件）

```
git rm --cached file_name
```

### Git每次push都需要输入用户名与密码

首先，如果我们git clone的下载代码的时候是连接的https://而不是git@git (ssh)的形式，当我们操作git pull/push到远程的时候，总是提示我们输入账号和密码才能操作成功，频繁的输入账号和密码会很麻烦，也特别烦恼。

**解决办法**
```
git bash进入你的项目目录，输入:
git config --global credential.helper store
```
此项会在本地生成一个文本，上边记录你的账号和密码。
然后你使用上述的命令配置好之后，再操作一次git pull，然后它会提示你输入账号密码，这一次之后就不需要再次输入密码了。

### 发现github上的绿色格子几天没有亮了

原因：之前github的邮箱更换了，但是本地主机的邮箱忘记更换。

使用`git config user.email`查看是否和github上保留的邮箱是否一致，

如果不一致，使用`git config user.email "your_address”`进行本地邮箱的更换。

### 在终端中键入git status后显示中文乱码

解决办法
```
git config --global core.quotepath false
```

### 重写最后一个commit信息

```
git commit --amend
```

### 恢复git rm的文件

第一步: `git reset`
第二步: `git checkout the_file_deleted`

