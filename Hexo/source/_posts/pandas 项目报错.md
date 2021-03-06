
title: pandas使用

# 所属分类

categories:

- python

# 标签(多个标签如下所示)

tags:

- pandas




------



pandas.read_csv参数详解
https://www.cnblogs.com/datablog/p/6127000.html

协同过滤
https://blog.csdn.net/xiaokang123456kao/article/details/74735992

## CParserError: Error tokenizing data


## python处理数据的风骚操作[pandas 之 groupby&agg]
https://segmentfault.com/a/1190000012394176


## 特征选择 (feature_selection)

    特征是否发散：如果一个特征不发散，例如方差接近于0，也就是说样本在这个特征上基本上没有差异，这个特征对于样本的区分并没有什么用。
    特征与目标的相关性：这点比较显见，与目标相关性高的特征，应当优选选择。除移除低方差法外，本文介绍的其他方法均从相关性考虑。

https://www.cnblogs.com/stevenlk/p/6543628.html


## Bagging（Bootstrap aggregating）、随机森林（random forests）、AdaBoost
https://blog.csdn.net/xlinsist/article/details/51475345

## 特征转换
https://www.cnblogs.com/jasonfreak/p/5619260.html

## GBDT原理及利用GBDT构造新的特征-Python实现
https://blog.csdn.net/shine19930820/article/details/71713680/

## 推荐系统
http://www.infoq.com/cn/articles/user-portrait-collaborative-filtering-for-recommend-systems
一般来说推荐系统的特征体系由 3 个部分组成：用户特征、内容特征、上下文特征。

用户特征：包括但不限于用户姓名、性别、年龄、注册时间、收货地址、常用区域等用户特征

内容特征：包括但不限于以及商品、内容的标题分词、内容的 TF-IDF、内容来源、内容渠道、内容生产者等等

那么上下文特征， 是代表用户当前时空状态、最近一段时间的行为抽象的特征。比如说用户当前的 GPS 坐标，大家可能觉得奇怪， GPS 坐标怎么用来推荐呢？其实很简单，地球一圈是 4 万公里，GPS 一圈是 360°，一度大概是 100 公开。如果我们把 GPS 坐标保存到小数点后一位，组合起来，这样的特征就是 10*10 公里的格子，这就代表了一个有泛化能力的用户的位置。
### How Feature Engineering can help you do well in a Kaggle competition
https://medium.com/unstructured/how-feature-engineering-can-help-you-do-well-in-a-kaggle-competition-part-i-9cc9a883514d
https://jiasuhui.com/article/13888(翻译)

## pandas模块进行数据分析
https://www.cnblogs.com/nxld/p/6058591.html
https://blog.csdn.net/cbbing/article/details/50721468

## Model_selection原理
https://blog.csdn.net/stranger_man/article/details/78886060
https://blog.csdn.net/stranger_man/article/details/78376837
from sklearn.model_selection import cross_validate
from sklearn.metrics import recall_score
#组合评估参数字典
scoring = ['precision_macro', 'recall_macro']
clf = svm.SVC(kernel='linear', C=1, random_state=0)

###注意最后一个参数的用法，默认情况下是true返回训练的时间，使用时可以设置成False，因为返回的一般用不到。
###scoring参数，如果多个参数则必须组合成字典结构。一个参数时则是字符串结构。也可以使用默认的f1-score。

scores = cross_validate(clf, iris.data, iris.target, scoring=scoring,
                       cv=5, return_train_score=False)

###建议以后自己用的时候也这样打印一下，方便自己的使用。

sorted(scores.keys())
    ['fit_time', 'score_time', 'test_precision_macro', 'test_recall_macro']
scores['test_recall_macro'] 
    array([ 0.96...,  1.  ...,  0.96...,  0.96...,  1.        ])

## python 合并（merge , concat , join , combine_first)
https://www.jianshu.com/p/baaf8c89c9e2


## 互联网广告综述之点击率特征工程
https://blog.csdn.net/yas12345678/article/details/52956085
CTR预估模型
https://www.cnblogs.com/qcloud1001/p/7513982.html

## plot是一种将所有列及其标签进行绘制的简便方法

## value_counts()
是一种查看表格某列中有多少个不同值的快捷方法，并计算每个不同值有在该列中有多少重复值。
value_counts()是Series拥有的方法，一般在DataFrame中使用时，需要指定对哪一列或行使用
https://www.jianshu.com/p/f773b4b82c66
