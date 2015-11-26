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
%例1：使用一维信号的自动消噪函数wden对信号进行消噪。
%将信号origin使用小波函数'sym5'分解到第5层
%使用minimaxi阈值选择对系数进行处理，消除噪声信号
lev = 5;
result = wden(origin, 'minimaxi', 's', 'mln', lev, 'sym5');
```

```Matlab
%例2：对小波分解系数使用函数wthcoef进行阈值处理，然后利用阈值处理后的小波系数进行重构达到去噪目的。
%使用小波函数'db5'对信号origin进行3层分解
[c, l] = wavedec(origin, 3, 'db5');
%设置尺度向量
n = [1, 2, 3];
%设置阈值向量
p = [120, 110, 100];
%对高频系数进行阈值处理
nc = wthcoef('d', c, l, n, p);
%对修正后的小波分解结构进行重构
result = waverec(nc, l, 'db5');
```

```Matlab
%例3：
%对含噪信号origin求消噪的阈值
[thr, sorh, keepapp] = ddencmp('den', 'wv', origin);
%对信号进行消噪
result = wdencmp('gbl', origin, 'db4', 2, thr, sorh, keepapp);
```

```Matlab
%例4：首先使用函数wnoiset获取噪声方差，然后使用函数wbmpen获取小波去噪阈值，最后使用函数wdencmp实现信号消噪。
%使用小波函数'db6'对信号origin进行3层分解
[c, l] = wavedec(origin, 3, 'db6');
%估计尺度1的噪声标准差
sigma = wnoiset(c, l, 1);
%获取消噪过程中的阈值
alpha = 2;
thr = wbmpen(c, l, sigma, alpha);
%对信号进行消噪
keepapp = 1;
result = wdencmp('gbl', c, l, 'db6', 3, thr, 's', keepapp);
```
