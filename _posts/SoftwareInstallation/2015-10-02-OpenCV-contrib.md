---
layout: post
title: 安装OpenCV扩展库contrib
category: 软件安装
---

安装的OpenCV是官网上的3.0 RC1版本，contrib是从github上[https://github.com/Itseez/opencv_contrib](https://github.com/Itseez/opencv_contrib)下载的，安装步骤如下：

$ cd <opencv_build_directory>
$ cmake -DOPENCV_EXTRA_MODULES_PATH=<opencv_contrib>/modules <opencv_source_directory>
$ make -j5

最后，运行`sudo make install`。
