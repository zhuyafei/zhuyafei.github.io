---
layout: post
title: 在Mac OSX Yosemite 10.10.3上安装Git
category: 软件安装
---

以下是使用wifi环境下的Git配置

一、设置SSH密钥
1. 生成密钥。到~目录下打开终端执行ssh-keygen -t rsa，然后一直按Enter键，此时在~目录下的.ssh目录下生成了id_rsa.pub。

2. 把公共密钥保存到GitHub网站上。到GitHub的Account setting上选择SSH Keys选项，点击Add SSH key，把title写为your name@macbookPro。把id_rsa.pub里面的内容复制到key中，保存。

3. 把密钥加载到SSH里。在终端输入ssh-add。

二、Git的安装与配置
安装Git需要通过Homebrew或Macports，我选择安装Homebrew，安装Homebrew时的一些命令需要用到命令行开发者工具，而安装Xcode时会默认安装上Command Line Tools，所以要先安装Xcode。

1. 安装Xcode
Xcode可以在App Store中安装，安装时出现“此Apple ID尚未在App Store使用”的错误，参考[http://jingyan.baidu.com/article/f3e34a12867bb4f5ea65356a.html](http://jingyan.baidu.com/article/f3e34a12867bb4f5ea65356a.html)解决了该问题，原因是注册账号的一些信息没有填写完整。

2. 安装Homebrew
参考Homebrew官方网站[http://brew.sh/](http://brew.sh/)进行安装，即在终端运行ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3. 安装Git
终端输入命令：brew install git

4. 设置用户名和电子邮件地址
终端输入命令：git config —global user.name “zhuyafei”和git config —-global user.email “zhuyafei4520@163.com”
用git config —list命令可以查看是否设置成功。






