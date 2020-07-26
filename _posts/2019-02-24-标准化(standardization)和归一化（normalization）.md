---
layout: post
category: Data Science 数据科学
title: 标准化(standardization)和归一化（normalization）
---

知乎原文：[标准化(standardization)和归一化（normalization）](https://zhuanlan.zhihu.com/p/57541603)

**注意，我们下面讨论的归一化和标准化针对的都是特征（数据列），而非针对样本（数据行）进行。**

归一化（Normalization）和标准化（Standardization）都是为了解决不同特征取值范围相差太大的问题。因为，如果部分特征的取值特别大而远超其他特征的值，那模型训练的结果就会被这少部分的特征所支配，从而错失了其他小值特征所含有用信息。

<!-- more -->

<h2>标准化</h2>
<h3>公式</h3>

**z  = (x - u) / s**

对每个值x，减去其所在列的平均值u，再除以所在列的标准差s，得到的就是标准化后的值z。每列的标准化独立进行，标准化后的数据每列的均值为0，标准差为1。

<h3>工具</h3>

[sklearn.preprocessing.StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html)

示例代码：

```python
>>> from sklearn.preprocessing import StandardScaler
>>> data = [[0, 0], [0, 0], [1, 1], [1, 1]]
>>> scaler = StandardScaler()
>>> scaler.fit(data)

>>> print(scaler.mean_)
[0.5 0.5]

>>> print(scaler.transform(data))
[[-1. -1.]
 [-1. -1.]
 [ 1.  1.]
 [ 1.  1.]]

>>> print(scaler.transform([[2, 2]]))
[[3. 3.]]
```

<h2>归一化</h2>
<h3>公式</h3>

**z  = (x - min) / (max - min)**

对每个值x，减去其所在列的最小值min，再除以所在列的极差（最大值与最小值之差），得到的就是归一化后的值z。每列的归一化独立进行，归一化后的数据每列的取值范围为[0, 1]。

<h3>工具</h3>

[sklearn.preprocessing.MinMaxScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html#sklearn.preprocessing.MinMaxScaler)

示例代码：

```python
>>> from sklearn.preprocessing import MinMaxScaler
>>> data = [[-1, 2], [-0.5, 6], [0, 10], [1, 18]]
>>> scaler = MinMaxScaler()
>>> scaler.fit(data)
>>> print(scaler.data_max_)
[ 1. 18.]

>>> print(scaler.transform(data))
[[0.   0.  ]
 [0.25 0.25]
 [0.5  0.5 ]
 [1.   1.  ]]

>>> print(scaler.transform([[2, 2]]))
[[1.5 0. ]]
```

<h2>总结</h2>
两种特征缩放的方法都有它们的缺点，如果数据里面含有异常值（Outlier），那归一化会使得绝大部分数据都集中在一个极小的范围值内；而使用标准化转换后的数值可能很大，不像归一化那样有限定的取值范围。
