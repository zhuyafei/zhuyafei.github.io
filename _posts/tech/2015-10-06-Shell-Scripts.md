---
layout: post
title: shell脚本
category: 技术
---

1. 某文件夹下有number_all个pdf格式的文件，文件按数字1~number_all命名，如果要在中间加入一个文件（如：27.pdf），那么原文件夹中的文件从27开始就要依次加1以留出空隙。

```Bash
  1 #!/bin/bash
  2 
  3 if [ $# != 3 ]; then
  4         echo -ne "Arguments Error.\n"
  5         echo -ne "Usage:\n"
  6         echo -ne "\t$0 <dir> <number_all> <number_insert>\n"
  7         exit 7
  8 else
  9 
 10 dir=$1
 11 number_all=$2
 12 number_insert=$3
 13 
 14 for ((i=${number_all};i>${number_insert};i=i-1))
 15 do
 16         mv ${dir}/${i}.pdf ${dir}/$[${i}+1].pdf
 17 done
 18 fi
```
注1：给一个变量赋值的格式为：
**变量名**=**变量值**，“=”前后不可以有空格。和C语言不同，Shell中不需要显式的语法来声明变量。
注2：if与[之间必须有空格，[]与判断条件之间也必须有空格。

2. 将某文件夹下的所有文件（扩展名相同）重新按数字命名。

```Bash
 1 \begin{bash}
 2  #!/bin/bash
 3 if [ $# != 2 ]; then
 4 	echo -ne "Arguments Error.\n"
 5 	echo -ne "Usage:\n"
 6 	echo -ne "\t$0 <Dir> <Extension>\n"
 7 	exit 7
 8 else
 9 num=1
 10 dir=$1
 11 Extension=$2
 12 for i in $(find ${dir} -type f)
 13 do
 14 	mv $i $dir/${num}.${Extension}
 15 	((num++))
 16 done
 17 fi
```
