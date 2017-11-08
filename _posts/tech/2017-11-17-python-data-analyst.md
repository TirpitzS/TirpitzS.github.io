---
layout: post
title: Python数据分析实战
category: 技术
tags: Python
keywords: Python、数据分析
description: 用Python对数据进行分析
---

## 数据分析

从原始数据中抽取信息的这个过程叫做***数据分析***。数据分析的目的不止于建模，更重要的是其预测能力。

## 统计方法

1、贝叶斯方法

2、回归

3、聚类

上述方法请参照统计建模篇

## 数据分析的步骤

a、数据抽取

b、数据清洗

c、数据转换

d、数据探索

e、预测模型

f、模型评估

g、结果可视化

h、解决方案部署(1、分析结果 2、决策部署 3、风险分析 4、商业评估)

## python基本数据结构

1、***字典(dict)***

其中每个元素(值)都有一个与之关联的被称作键的标签。==字典中的数据没有内在顺序，而是一个个键值对。==
```
>>>dict = {'name':'william','age':25,'city':'London'}
```
2、***列表(list)***

列表这种数据结构包含一系列具有明确顺序的元素，支持新增或删除操作。每一元素都有一个叫做==索引==的数字标识，这个数字也就是该序列的位次。
```
>>>list = [1,2,3,4]
```
如果想获取单个元素，用方括号加索引即可，想要获取列表的一部分，用索引制定所需要的上下界即可。note:索引从0开始。
```
>>>lsit[2]
>>>list[1:3]
```
用负数表示倒序
```
>>>list[-1]
4
```
==注意：list[i,j]可以看出list[0:j]去掉list[0:i]==

## NumPy库

#### 安装
```
pip install numpy
```

#### ndarray

一种由同质元素组成的多维数组，元素数量是事先指定好的。同质是指几乎所有元素的类型和大小都相同。数据类型由另外一个叫做dtype的NumPy对象来指定，每个ndarray只有一个dtype类型。

1、导入模块
```python
import numpy as np
```

1、创建数组

a:array(list[])
```python
a = np.array([1,2,3])
a.dtype ##获取ndarray的数据类型
```
b:array(嵌套元组或元组列表)
```
d = np.array(((1,2,3),(4,5,6)))
```
c:array(元组或列表元组)
```
e = np.array([(1,2,3),[4,5,6],(7,8,9)])
```
d:自带方法
```
np.zeros((3,3)) ##(3,3)表示3x3

np.arange(i, j, offset).reshape(m, n) ##随机i到j,间隔offset，然后重新定为m x n矩阵
```
2、数组的属性获取
```
a.ndim ##获取数组的轴数

a.size ##获取数组长度

a.shape ##获取数组的型，比如3x4 or 4 x 3
```
3、使用dtype修改数组的数据类型
```
f = np.array([[1,2,3],[4,5,6]], dtype=complex)
```

#### 运算

1、算术运算
```python
>>>a = np.arange(4)
>>>a
array([0,1,2,3])
>>>a+4      ##元素+4
array([4,5,6,7])
>>>a * 2    ##元素*2
array([0,2,4,6])
```
note:+ - * /均为元素运算

2、矩阵积
```
np.dot(A,B) or A.dot(B) ## 注意A, B有顺序
```

3、通用函数
a、log
b、sin
c、sqrt
更多请翻阅numpy手册

4、聚合函数（统计函数）
```
a = np.array([3.3, 4.5, 1.2, 5.7, 0.3])
a.sum()
a.max()
a.mean()
a.std()
```
#### 索引机制、切片和迭代方法

1、数组索引机制指的是用方括号[]加序号的形式应用单个数组元素
```python
>>>A = np.arange(10,19).reshape((3,3))
>>>A
array([[10,11,12],[13,14,15],[16,17,118]])
>>>A[1,2]          ## 第二个array中的第3个元素
```

2、切片操作
```
a = np.arange(10,16)
a[x:y:z]   ##x为起始引用，省略为0，y为末尾引用，省略为最大值，z为间隔，省略为1
```
```
>>>A = np.arange(10, 19).reshape((3,3))
A
array([[10,11,12],
       [13,14,15],
       [16,17,18]])
##对二维数组使用切分法
A[0,:]
array([10,11,12])
A[:,0]
array([10,13,16])

##抽取一个子矩阵
A[0:2, 0:2]
array([[10,11],[13,14]])

##非连续抽取
A[[0,2],0:2]
array([[10,11],[16,17])
```
3、数组迭代

a、for结构迭代

b、内置函数
```
np.apply_along_axis(foo, axis=0, arr=A)   ##axis = 0为列，axis=1为行
```

4、条件和布尔数组
```
A < 0.5
array([[True, True, False, False]
       [True, True, Fales, True],
       [False, True, False, False],
       [False, False, True, True]], dtype=bool)
       
A[A<0.5]   ##将返回所有小于0.5的数组成的数组
```

5、改变数组的形状
```
a.reshape()
a.ravel()           ##恢复为1维
a.transpose()       ##转置
```

#### 数组的操作
1、连接数组
```
np.vstack((A, B))       ##垂直连接
np.hstack((A,B))        ##横向连接

np.column_stack((a,b,c))        ##类似垂直连接
np.row_stack((a,b,c))           ##类似横向连接

np.hsplit()             ##水平切分
np.vsplit()             ##垂直切分

np.split(A, [1,3], axis=1) ##axis 1：列 0：行
```