---
layout: post
title: 在Mac OSX Yosemite 10.10.3上安装OpenCV3.0.0（包含在Xcode中配置OpenCV）
category: 工具
---
首先交代下安装环境Mac OSX Yosemite 10.10.3，安装的OpenCV为[OpenCV官网](http://opencv.org/)上2015-06-04发布的3.0版本，Xcode为6.2 (6C131e)版本。下面详细介绍安装步骤：

一、安装cmake
在终端输入port install cmake。

二、到OpenCV官网下载Mac/Linux版本的OpenCV
![OpenCV-DOWNLOADS](./figures/OpenCV-DOWNLOADS.png)
下载后的文件名为opencv-3.0.0.zip，大小为101MB。双击解压，进入到/Users/fei/software/OpenCV/opencv-3.0.0/路径下，然后新建一个build文件夹，再进到build文件夹下。参考官网输入：
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
make
sudo make install
至此，OpenCV在Mac上就安装完毕了。

三、在Xcode中配置OpenCV，并进行测试



