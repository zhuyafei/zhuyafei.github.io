---
layout: post
title: 在Mac OSX Yosemite 10.10.3上安装OpenCV3.0（包含在Xcode中配置OpenCV）
category: 软件安装
---
首先交代下安装环境Mac OSX Yosemite 10.10.3，安装的OpenCV为[OpenCV官网](http://opencv.org/)上2015-06-04发布的3.0版本，Xcode为6.2 (6C131e)版本。下面详细介绍安装步骤：

一、安装cmake
在终端输入port install cmake。

二、到OpenCV官网下载Mac/Linux版本的OpenCV
![OpenCV-DOWNLOADS](/figures/OpenCV-DOWNLOADS.png)
下载后的文件名为opencv-3.0.0.zip，大小为101MB。双击解压，进入到/Users/fei/software/OpenCV/opencv-3.0.0/路径下，然后新建一个build文件夹，再进到build文件夹下。参考官网输入：
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
make
sudo make install
至此，OpenCV在Mac上就安装完毕了。

三、在Xcode中配置OpenCV，并进行测试
打开Xcode，新建一个command line工程：工程名字TestOpenCVDemo，注意语言选择C++。这样C++的HelloWorld就建好了，编译应该能正常运行。接下来开始在Xcode中配置OpenCV了。
最左边选中工程，然后右边选中Targets，再BuildSettings下，右边搜索框里输入search，很快就能找到Search Paths设置项。在Header Search Paths里输入:/usr/local/include  在Library Search Paths里输入:/usr/local/lib
示意图如下：
![SearchPaths](/figures/SearchPaths.png)
接着在Build Phases里找到Link Binary With Libraries，点击＋号
![LinkBinaryWithLibraries](/figures/LinkBinaryWithLibraries.png)
选择add other，如下图：
![AddLibraries](/figures/AddLibraries.png）
然后按下／键，输入lib的路径/usr/local/lib,点go：
![ChooseDirectory](/figures/ChooseDirectory.png)
然后就是选择OpenCV的库了，这里可以将所有OpenCV的库（以libopencv开头，.dylib格式）都添加上，按下command键可以实现多选。添加完毕后可以在左侧看到：
![ListsofLibraries](/figures/ListsofLibraries.png)
在main.cpp里输入以下内容，实现显示原图像及灰度化后图像的功能：
![Xcode-OpenCV-Example](/figures/Xcode-OpenCV-Example.png)
运行结果如下：
![result](/figures/result.png)
至此大功告成。



