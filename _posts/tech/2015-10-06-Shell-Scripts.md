---
layout: post
title: shell脚本
category: 技术
---

1. 某文件夹下有number_all个pdf格式的文件，文件按数字1~number_all命名，如果要在中间加入一个文件（如：27.pdf），那么原文件夹中的文件从27开始就要依次加1以留出空隙。

```Bash
  1 #!/bin/bash
  2 
  3 if [ $# != 2 ]; then
  4         echo -ne "Arguments Error.\n"
  5         echo -ne "Usage:\n"
  6         echo -ne "\t$0 <number_all> <number_insert>\n"
  7         exit 7
  8 else
  9 
 10 number_all=$1
 11 number_insert=$2
 12 
 13 for ((i=${number_all};i>${number_insert};i=i-1))
 14 do
 15         mv ${i}.pdf $[${i}+1].pdf
 16 done
 17 fi
```
