---
layout: post
title: 一维信号去噪
category: 机器学习
---

利用小波进行信号去噪的基本步骤主要包括：
1. 信号的小波分解；
2. 小波分解高频系数的阈值量化；
3. 信号的小波重构。使用分解的低频系数以及阈值量化后的高频系数进行小波重构。

```Matlab
%将信号origin使用小波函数'sym5'分解到第5层
%使用minimaxi阈值选择对系数进行处理，消除噪声信号
lev = 5;
result = wden(origin, 'minimaxi', 's', 'mln', lev, 'sym5');
```
