---
title: 新电脑上部署博客（已搭建博客前提下）
date: 2020-06-29 02:28:14
tags:
categories: 配置
---
# 如何在新电脑上面更新博客（hexo）
&emsp;朕于端午节从学校毕业回家后，一直闲着无事。想到年初在家搭建的博客还没有来得及上传东西，写写文章。心中甚是过意不去（假话，hhh）。如今正好有空来侍弄这玩意。这也称得上我第一篇真正意义上写的文章吧！
&emsp;事情的起源是这样的，朕于年初利用hexo在github上搭建了一个个人博客网站。当时博客文件是写在家中台式机器上，然后通过hexo -g和hexo -d命令上传至github。如今我笔记本带回家里了，我想在笔记本上也能愉快的写博客，甚至我在以后其他新的电脑上也能愉快写博客。
&emsp;那么问题来了。由于原来我们的文件是存储在最初电脑上，通过hexo -d 分发出去的是编译后的文件，用来生成网页的。换句话说，我们上传至github上的是.deploy_git文件夹里面的东西，其他的source，public等文件夹都是存储于我们原来电脑中的。
&emsp;经过朕一番阅览众大臣上传的奏折，有如下方法可以解决：
&emsp;老规矩，先介绍解题思路。拟在github上面新建分支Hexo，把博客源文件放在新建的分支Hexo上面，我们在新电脑写博客时，直接拷贝Hexo分支上面的文件。然后安装好环境就可以写了。
&emsp;操作步骤如下
&emsp;（1）于github上在原来的仓库新建一个分支Hexo，并将其设为默认分支（以便后面拷贝就是拷贝这个分支上东西）。
&emsp;（2）在原电脑其他位置打开git bash,并输入`git clone git@github.com:×××××××××（你的仓库地址）`，将Hexo分支里面东西克隆过来，把.git以外的文件夹全部删掉，并且从博客源文件（除了.deploy_git）全部复制过来。值得注意的是，如果你克隆过theme中的主题文件，必须把主题文件中的.git文件夹删掉，不然会报错。原因是git不能嵌套上传。
&emsp;（3)	
	git add . #提交所有修改 
	git commit -m "add branch" #确认修改 
	git push #推送到库上

&emsp;在新电脑上搭建环境
&emsp;(4)安装git
    sudo apt-get install git #windows 下从官网下载安装包接下来步骤默认点确定
&emsp;(5)设置git邮箱和账号
	git config --global user.name "yourgithubname"
	git config --global user.email "yourgithubemail"
&emsp;(6)设置ssh key
	ssh-keygen -t rsa -C "youremail"
&emsp;(7)登录GitHub，打开「Settings」->「SSH and GPG keys」，然后点击「new SSH key」把id_rsa.pub公钥里面东西复制到Key文本框，点击Add SSH key
&emsp;(8)安装nodejs
	linux:
	sudo apt-get install nodejs
	sudo apt-get install npm
	windows:
	下载安装包即可
&emsp;(9)安装hexo
	sudo npm install hexo-cli -g
&emsp;(10)在你选择写博客的文件夹
	git clone git@………
	cd xxx.github.io
	npm install
	npm install hexo-deployer-git --save
	hexo g #生成部署
	hexo d
	hexo new newpage #然后写博客。
&emsp;(11)注意每次写完上传源文件到github;写之前先`git pull`
	git add .
	git commit –m "xxxx"
	git push 




