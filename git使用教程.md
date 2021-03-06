# Git

> Git是目前世界上最先进的分布式版本控制工具
>
> 

## 1.git的作用

> 协同开发
>
> 版本记录
>
> 历史追查
>
> 代码备份
>
> 分支管理
>
> ........

## 2.配置git签名

> 选中你要作为git工程存放的目录 然后单击鼠标右键选择git bash here

tip:

git 需要填写用户名喝邮箱作为一个标志

> C:\user\cver\.gitconfig 有一个--global属性，所有的git项目都会公用这个属性
>
> git config --global user.name "tao"
>
> git config --global user.email "2254511413@qq.com"

## 3.创建版本库

1. 选中一个git目录
2. 输入命令初始化版本库

> git init      ----初始化一个空的仓库 会有一个.git文件

## 4.Git的命令行操作

- > git status ---- 查看文件状态

- > git add 文件名/目录名 ---- 将文件/目录添加到临时暂存区
  >
  > eg git add src/test.c

- > git commit -m "提交提示信息" ----将文件（所有暂存区的文件）提交到一个统一的版本文件

  tip:

  每当文件被修改/添加。删除的时候 都需要重新git add 然后git commit

- > git log  ----查看历史记录
  >
  > git log --pretty=oneline ----没有时间、作者信息

### 4.1回退历史

- > git reset --hard HEAD^1----回退到上一次提交
  >
  > tip
  >
  > HEAD是一个指针，永远指向最新的版本  ^1表示指向上1个版本
  >
  > --hard硬:不但将版本回顾 还会将指定的数据抹除 不会保留任何你修改的记录
  >
  > --soft软：回退版本 也会保留改动记录 会自动帮你git abb
  >
  > --mix折中：回退版本 并保留所有的改动记录 但不会自动git add
  >
  > git reset:本质修改HEAD位置

  reset这种方式当前版本之后的版本就会不复存在

- > git reset --hard HEAD~2 ---- 回退到两个版本之前的版本

### 4.2版本穿越

- > git reflog ---- 查看历史记录的版本号
  >
  > git reset --hard ID号

### 4.3还原文件

- > git checkout 文件名
  >
  > 修改一个文件 但是没有add和commit 使用上面操作还原修改文件

### 4.4删除文件

- > 先删除
  >
  > 然后add
  >
  > 然后commit

## 5.工作区 本地库 暂存区 

> 工作区：电脑本地磁盘目录
>
> 本地库：在工作区中有一个隐藏目录.git 就是git的本地版本库
>
> 暂存区：一般在git目录下的index文件 暂存区有时也叫索引

## 6.分支

项目已经上线，但是产品经理又提出了新的需求，评估实现这个新功能需要2个月的时间 但是项目还是需要同时上线运行 时不时修改BUG 如何管理这几个版本

> 使用分支解决

### 6.1分支相关命令

> git branch -v ----查看分支

### 6.2 创建分支

> git branch 分支名称

### 6.3切换分支

> git checkout 分支名称

### 6.4合并分支（将其他分支合并到master）

> 1.git checkout master ---- 切换到住分支
>
> 2.git merge 分支名 ----合并
>
> 

## 7.冲突

同一个文件同一位置的代码 在两种版本的仓库合并时 版本的管理软件无法判断应该保留哪一个版本 因此会提示该文件发生冲突 冲突一般是需要程序员手动解决

> 1.先在master分支上创建一个test.c文件
>
> 2.先在common分支上创建一个test.c文件
>
> 3.分别commit
>
> 4.合并必定产生冲突

### 7.1 查看冲突

> git diff ----查看冲突

### 7.2解决冲突

> 切换到那个目录 然后查看文件
>
> 重新add和commit

# Github

github是一个git项目托管网站，主要提供基于git版本托管服务

![](image-20220408100802336.png)

## 1.Github上传代码操作

> 建立本地仓库
>
> 1.创建目录
>
> 2.搭建代码库
>
> git init 
>
> git config --global user.name "tao"
>
> git config --global user.email "2254511413@qq.com"
>
> 3.提交代码
>
> git add 文件/目录
>
> git commit -m "提交信息"

-------------------------------------------------------------------------------------------------

> 创建github的项目库

-----------------------------------------------------------------------------------------------------------------------------------------------------------

> 增加远程地址
>
> git remote add <远端代号><远端地址>
>
> <远端代号> 一般用origin做代号 也可自定义
>
> <url> 仓库地址

------------------------------------------------------------------------------------------------------------------------

> 推送到远程库
>
> git push <远端代号><分支名>
>
> 输入github用户名 密码

## 2.下载Github的库

> git clone <远端地址><项目的目录名>
>
> <项目的目录名>：在本地的文件名
>
> git clone url C100

----------------------------

> 修改完后怎么上传回去？
>
> git add
>
> git commit
>
> git push origin master 会出现问题 授权

## 3.自己同步更新代码

> git pull origin master

## 4.协同冲突

在上传或者同步代码时候 由于你和他人都修改了同一文件的同一位置代码 版本管理工具无法判断究竟以谁为准 这就会报告冲突 需要程序员手动结局

> push会报错 必须先同步再修改
>
> 同步的时候 会出现冲突------------->找到文件 进行修改
>
> git add
>
> git commit
>
> 然后push

## 5.第三方协作

有一个fork 第三放fork出来 在自己就有一个库

生成一个从库 会发送一个同步请求 需要同意

第三方修改文件之后 查看CODE 就会有一个new pull request---->提交

管理员就会收到一封邮件



# Gitab

> 自架私服版的github
>
> 使用和github一样	局域网中

# IDEA整合git

- 

# 几个问题

> $ git push origin master
> fatal: unable to access 'https://github.com/tao-source/C.git/': OpenSSL SSL_read: Connection was reset, errno 10054

取消git代理 使用自己的代理

//取消http代理
git config --global --unset http.proxy
//取消https代理 
git config --global --unset https.proxy

