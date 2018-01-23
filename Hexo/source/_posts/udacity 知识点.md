#title

title: udacity知识点
# 所属分类

categories:

- 学习

# 标签(多个标签如下所示)

tags:

- 深度学习

- python


------

splitext()作用类似与split(),不过它会根据扩展名分隔符而不是目录分隔符来分解路径

python 在内部使用两个字节来存储一个unicode，使用unicode对象而不是str的好处，就是unicode方便于跨平台。
<!-- more -->
你可以用如下两种方式定义一个unicode:
Python
s1 = u"人生苦短"
s2 = unicode("人生苦短", "utf-8")
1
2
	
s1 = u"人生苦短"
s2 = unicode("人生苦短", "utf-8")

在windows上面开始使用路径时，一定带上r，不然路径里面类似\t \n这种会被转义
不信，自己找路径试试

Python pickle模块作用是持久化的储存数据。

numpy.random.shuffle打乱顺序函数：在做将caffe模型和预训练的参数转化为tensorflow的模型和预训练的参数，以便微调