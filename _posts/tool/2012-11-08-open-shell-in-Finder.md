---
layout: post
title: Mac中在Finder里面打开终端
category: 杂货箱
---
在开发过程中经常会用到Shell，而我们可以用Mac中一个叫终端的App进入Shell。打开这个App后，默认进入用户的home目录，即“/Users/username”，而这往往不是我们想要的工作目录。因此我们需要敲好几次“cd”命令才可以进入我们的工作目录。这显得很麻烦，其实我们可以利用系统的“服务”来这文件夹的右键菜单中直接加入一个在所选目录打开Shell的功能，而且不用借助任何第三方软件，只需要用系统自带的Automator应用即可。
首先打开Automator，在“文件”下点击“新建”，选取文稿类型为“服务”，如下图：
![Automator-Create services](http://blog.xcodev.com/images/post/automator-create-services.png)
然后在右侧视图上方，设置为选定“文件夹”和位于“Finder”，如下图：
![Automator-Target setting](http://blog.xcodev.com/images/post/automator-target-setting.png)
Automator左侧会显示很多操作，你可以将左侧的操作拖到右侧的视图来在运行时进行这些操作。这里我们需要一个“打开Finder项目的操作”，由于操作实在太多，你可以在搜索框中输入“open”进行搜索。将操作的打开方式设置为“终端”App，如果打开方式中没有这一项，可以选择“其他”，然后在“实用工具”中找到“终端”App。
![Automator-Open in shell](http://blog.xcodev.com/images/post/automator-open-in-shell.png)
在菜单中选择保存，保存文件名为“打开终端”。这样当你在Finder中右键一个文件夹时，右键菜单里面的“服务”选择“打开终端”就可以打开当前位置的终端了。类似Linux下面的右键，用终端打开。
