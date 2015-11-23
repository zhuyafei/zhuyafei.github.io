---
layout: post
title: 遗传算法
category: 机器学习
---

遗传算法的主要步骤：
1. 个体编码
在遗传算法里，优化问题的解被称为个体（又叫做染色体或者基因串）。个体一般被表达为简单的字符串或数字串，这一过程称为编码。
常见的编码方式有：二进制编码、树形编码
2. 初始群体的产生
遗传算法是对群体进行的进化操作，需要给其准备一些表示起始搜索点的初始群体数据。定义群体规模的大小为n，则群体由n个个体组成，每个个体可通过随机方法产生。
3. 适应度计算
一般用适应性函数（fitness function）来衡量遗传算法解（即个体）的优劣。
4. 遗传算子（选择、交叉、变异）
选择：把当前群体中适应度较高的个体按某种规则或模型遗传到下一代群体中。
交叉：遗传算法中产生新个体的主要操作过程，它以某一概率相互交换某两个个体之间的部分染色体。交叉的概率一般都选择得比较大，在[0.6, 1.0]之间，这个交叉概率反映两个被选中的个体进行交配的概率。例如，交叉概率为0.8，则80%的“夫妻”会生育后代。
变异：对个体的某一个或某一些基因值按某一较小的概率进行改变，它也是产生新个体的一种操作方法。

由不同的编码方法和不同的遗传算子就构成了各种不同的遗传算法。

### GA (Genetic Algorithm)
Holland等于1975年提出了遗传算法，遗传算法使用确定长度的二进制位串作为遗传编码。

### GP (Genetic Programming)
遗传编程的首批实验由Stephen F. Smith（1980年）和Nichael Cramer（1985年）发表。John R. Koza于1992年写了一本著名的书"Genetic Programming: On the Programming of Computers by Means of Natural Selection"来介绍遗传编程。

### GEP (Gene Expression Programming)
基因表达式编程是葡萄牙学者Candida于2001年首次提出的一种新型的进化计算算法。
GEP有其特有的算子--插串。