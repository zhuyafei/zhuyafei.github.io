---
layout: post
title: shell脚本
category: 技术
---

1. 某文件夹下有number_all个pdf格式的文件，文件按数字1~number_all命名，如果要在中间加入一个文件（如：27.pdf），那么原文件夹中的文件从27开始就要依次加1以留出空隙。

```Bash
#!/bin/bash

if [ $# != 2 ]; then
	echo -ne "Arguments Error.\n"
	echo -ne "Usage:\n"
	echo -ne "\t$0 <number_all> <number_insert>\n"
	exit 7
else

number_all=$1
number_insert=$2

for ((i=${number_all};i>${number_insert};i=i-1))
do
	mv ${i}.pdf $[${i}+1].pdf
done
fi
```
