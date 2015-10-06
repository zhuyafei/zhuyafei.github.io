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
