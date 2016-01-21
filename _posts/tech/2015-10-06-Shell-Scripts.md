---
layout: post
title: shell脚本
category: 技术
---

### 1. 某文件夹下有number_all个pdf格式的文件，文件按数字1~number_all命名，如果要在中间加入一个文件（如：27.pdf），那么原文件夹中的文件从27开始就要依次加1以留出空隙。

```Bash
  1 #!/bin/bash
  2 
  3 if [ $# != 3 ]; then
  4	echo -ne "Arguments Error.\n"
  5	echo -ne "Usage:\n"
  6	echo -ne "\t$0 <dir> <number_all> <number_insert>\n"
  7	exit 7
  8 else
  9 
 10 	dir=$1
 11 	number_all=$2
 12 	number_insert=$3
 13 
 14 	for ((i=${number_all};i>=${number_insert};i=i-1))
 15 	do
 16		mv ${dir}/${i}.pdf ${dir}/$[${i}+1].pdf
 17 	done
 18 fi
```
注1：给一个变量赋值的格式为：**变量名**=**变量值**，“=”前后不可以有空格。和C语言不同，Shell中不需要显式的语法来声明变量。
注2：if与[之间必须有空格，[]与判断条件之间也必须有空格。

### 2. 将某文件夹下的所有文件（扩展名相同）重新按数字命名。

```Bash
 1  #!/bin/bash
 2 if [ $# != 2 ]; then
 3 	echo -ne "Arguments Error.\n"
 4 	echo -ne "Usage:\n"
 5 	echo -ne "\t$0 <Dir> <Extension>\n"
 6 	exit 7
 7 else
 8 num=1
 9 dir=$1
 10 Extension=$2
 11 for i in $(find ${dir} -type f)
 12 do
 13 	mv $i $dir/${num}.${Extension}
 14 	((num++))
 15 done
 16 fi
```

### 3. 两个文件夹下有相同数目的图片，其图片名不一样，但内容可能一样，编写脚本看其中有多少幅内容是一样的。

```Bash
  1 #!/bin/bash
  2 
  3 if [ $# != 2 ]; then
  4         echo -ne "Arguments Error.\n"
  5         echo -ne "Usage:\n"
  6         echo -ne "\t$0 <Dir1> <Dir2>\n"
  7         exit 7
  8 
  9 else
 10 
 11 sum=0
 12 dir1=$1
 13 dir2=$2
 14 for i in $(find ${dir1} -type f)
 15 do
 16         for j in $(find ${dir2} -type f)
 17         do
 18                 if cmp -s $i $j
 19                 then
 20                         ((sum++))
 21                         echo -ne "${sum}: \033[34m $i \033[0m\t\033[41;33m $j \033[0m\n"
 22                 fi
 23         done
 24 done
 25 echo -ne "\n"
 26 echo -ne "\tThe number of files with same content is \033[41;37m ${sum} \033[0m"
 27 fi
```

### 4. 列出当前目录下的所有文件夹

```Bash
ls -d */
ls -l|grep ^d|awk '{print $9}'
```

### 5. A文件夹下有1000幅bmp格式的图片，B文件夹下有5000幅jpg格式的图片，要从这5000幅图片中找到1000幅与A文件夹中文件名相同但扩展名不同的图片，放到C文件夹中。

```Bash
for i in $(ls *.bmp);do cp ${i%.bmp}.jpg C/;done
```

### 6. 查看当前目录下的所有文件，包括子文件夹中的
```Bash
ls -lR|grep "^-"|awk '{print $9}'
```
