#title

title: python小知识
# 所属分类

categories:

- python

# 标签(多个标签如下所示)

tags:

- python

- 软件安装


------
## np.where()

带一个星号（*）参数的函数传人的参数存储为一个元组（tuple）；

而带两个星号（*）参数的函数传人的参数则存储为一个字典（dict）

<!-- more -->

    np.where()[0] 表示行的索引，
    np.where()[1] 则表示列的索引
shape函数是numpy.core.fromnumeric中的函数，它的功能是读取矩阵的长度，比如shape[0]就是读取矩阵第一维度的长度

## pycharm 配置
一、在PyCharm下为你的Python项目配置Python解释器

　　　　1、Settings--》Editor--》Project：当前项目名--》Project Interpreter--》Add Local

二、在Python下创建Python文件、Python模块

　　　　1、File--》New--》Python File

　　　　2、File--》New--》Python Package

三、使用PyCharm安装Python第三方模块

　　　　1、Settings--》Editor--》Project：当前项目名--》Project Interpreter--》点击右侧绿色加号

四、Python基本设置

　　　　1、不使用Tab，Tab=4空格：Editor--》Code Style--》Python--》Tabs and Indents页签

　　　　2、字体、字体颜色：           Editor--》Colors & Fonts--》Font/Language Defaults/Python

　　　　3、关闭自动更新：              Editor--》Appearance & Behavior--》System Settings--》Updates

　　　　4、脚本头设置：                 Editor--》Code Style--》File and Code Templates--》Python Script

　　　　5、显示行号：  　　　　　　 Editor--》General--》Appearance--》Show line numbers

　　　　6、右侧竖线是PEP8的代码规范：提示一行不要超过120个字符。

　　　　7、导出、导入你自定义的配置：File--》Export Settings、Import Settings

五、常用快捷键

　　　　 Editor--》Keymap

　　　　1、Crtl + D ：复制当前行

　　　　2、Ctrl + Y  ：删除当前行

　　　　3、Shift + Enter ：快速换行

　　　　4、Ctrl + / ：快速注释 （选中多行后可以批量注释）

　　　　5、Tab ：缩进当前行 （选中多行后可以批量缩进）

　　　　6、Shift + Tab ：取消缩进 （选中多行后可以批量取消缩进）

　　　　7、Ctrl + F ：查找

　　　　8、Ctrl + R ：替换

　　　　9、Ctrl + ] ：跳到行尾

　　　　10、Ctrl + [：跳到行首

　　六、PyCharm安装插件

　　　　1、 Editor--》Plugins Editor--》Browse repositories --》Install

　　七、Git配置

　　　　1、Editor--》Version Control--》Git

　　八、常用操作指南

　　　　1、复制文件路径：左侧文件列表右键选中的文件--》Copy Path

　　　　2、在文件管理器中打开：左侧文件列表右键选中的文件--》Show in Explorer

　　　　3、快速定位：Ctrl + 某些內建模块之后，点击在原文件中展开

　　　　　　Scroll from Source / Collapse All

　　　　4、查看结构：IDE左侧边栏Structure查看当前项目的结构

　　　　5、Tab批量换Space：Edit--》Convent Indents--》To Spaces/To Tobs

　　　　6、TODO的使用：#TODO要做的事情

　　　　7、把当前Tab页移到窗口右边（下边），方便对比：Tab页签右键--》Move to Right（Down）

　　　　8、查看文件修改前后对比：文件中右键--》Local History

　　　　9、IDE右下角一些有用的信息：当前光标在第几行的第几个字符/当前回车换行/当前编码类型/当前Git分支

 　　　10、IDE右侧边栏--》DataBase

　　九、PEP8代码规范

　　　　1、单独一行的注释：# + 1空格 + 注释内容

　　　　2、代码后跟着的注释：2空格 + # + 1空格 + 注释内容

　　十、SSH Terminal Default encoding

　　　　1、Editor--》Tools--》SSH Terminal--》Default encoding UTF-8

　　十一、编码统一

　　　　Editor--》File Encoding--》IDE Encoding 和 Project Encoding 编码统一 UTF-8
##  python中的字符数字之间的转换函数
    int(x [,base ])         将x转换为一个整数    
    long(x [,base ])        将x转换为一个长整数    
    float(x )               将x转换到一个浮点数    
complex(real [,imag ])  创建一个复数    
str(x )                 将对象 x 转换为字符串    
repr(x )                将对象 x 转换为表达式字符串    
eval(str )              用来计算在字符串中的有效Python表达式,并返回一个对象    
tuple(s )               将序列 s 转换为一个元组    
list(s )                将序列 s 转换为一个列表    
chr(x )                 将一个整数转换为一个字符    
unichr(x )              将一个整数转换为Unicode字符    
ord(x )                 将一个字符转换为它的整数值    
hex(x )                 将一个整数转换为一个十六进制字符串    
oct(x )                 将一个整数转换为一个八进制字符串   
 
 
chr(65)='A'
ord('A')=65
 
int('2')=2;
str(2)='2'

## 获取绝对路径，相对路径
　　>os.path.abspath("文件名")：

显示的是一个文件的[绝对路径](http://www.cnblogs.com/zhangqigao/p/5756704.html)
>os.path.dirname("文件名"):

显示的是一个文件的相对路径
os.getcwd()——获得当前工作的目录
[os模块常用命令](http://www.cnblogs.com/kaituorensheng/archive/2013/03/18/2965766.html)

  ### [文件和目录访问](http://blog.csdn.net/pipisorry/article/details/38964135)

## 函数中×和××的区别
* 函数接收参数为元组

 例如 

def myfun(*args): #相当于 def myfun(1,2,3)    ==> args 就相当于（1,2,3）

　　for a in args:

　　　　print(a)

** 表示函数接收参数为一个字典

def myfun(**args) :#相当于 def myfun({a:1,b:2,c:3}) ==>args 就相当于{a:1,b:2,c:3}

　　for k,v in args:

　　　　print(k,":",v)

## [查看帮助](http://blog.csdn.net/american199062/article/details/51444117)

python中每个modul，每个class，每个def都是留有写doc的地方的，写没写是另一回事，可以用“对象名称.__doc__”查看。这是一个字符串，所以内容只能是字符串允许的内容。如果字符不足以满足说明需求，可能会加上web链接，或者专门的说明函数。

你要查看的应该是
import scipy
print scipy.quiver.__doc__

或者
import scipy
print help(scipy.quiver)


## zip
import numpy as np
a=[1,2,3]
b=[4,5,6,7]
c=[8,9,10,11,12]
zz=zip(a,b,c)
print(zz)

x,y,z=zip(*zz)
print(x)
print(y)
print(z)

输出：
[(1, 4, 8), (2, 5, 9), (3, 6, 10)]
(1, 2, 3)
(4, 5, 6)
(8, 9, 10)


unzip后的列表b和c的值都少了。
https://blog.csdn.net/csdn15698845876/article/details/73411541


## pd.cut
https://blog.csdn.net/cbbing/article/details/50721468

## Python3pandas库transform 
>import pandas as pd
import numpy as np
A=np.array([[1,2,3,4,5],[2,1,1,2,2],[1,2,3,4,5],[2,1,1,2,2],[1,2,3,4,5]])
data=pd.DataFrame(A,index=['li','chen','wang','zhao','qian'],columns=['a','b','c','d','e'])
print(data)


      a  b  c  d  e
li    1  2  3  4  5
chen  2  1  1  2  2
wang  1  2  3  4  5
zhao  2  1  1  2  2
qian  1  2  3  4  5


key=['ss','kk','kk','ss','ss']  #给定index分组标记
print(data.groupby(key).mean())  #mean是按key做分组的列均值

   
           a         b         c         d    e
kk  1.500000  1.500000  2.000000  3.000000  3.5
ss  1.333333  1.666667  2.333333  3.333333  4.0

   

data里每个元素位置的取值由transform函数的参数函数计算

print(data.groupby(key).transform(np.mean))
#data里每个位置元素取对应分组列的均值

    

             a         b         c         d    e
li    1.333333  1.666667  2.333333  3.333333  4.0
chen  1.500000  1.500000  2.000000  3.000000  3.5
wang  1.500000  1.500000  2.000000  3.000000  3.5
zhao  1.333333  1.666667  2.333333  3.333333  4.0
qian  1.333333  1.666667  2.333333  3.333333  4.0

    

生成的tsf里，每个位置元素取值是data里“对应位置元素”按transform的“函数参数”运算（这里是’对应元素’减去’对应分组列的均值’）；x取值是data的每个位置元素，只不过x.mean中的mean方法作用范围由key决定

>my_transform = lambda x : x-x.mean()  
tsf=data.groupby(key).transform(my_transform)
print(tsf)

    

             a         b         c         d    e
li   -0.333333  0.333333  0.666667  0.666667  1.0
chen  0.500000 -0.500000 -1.000000 -1.000000 -1.5
wang -0.500000  0.500000  1.000000  1.000000  1.5
zhao  0.666667 -0.666667 -1.333333 -1.333333 -2.0
qian -0.333333  0.333333  0.666667  0.666667  1.0
https://blog.csdn.net/cymy001/article/details/78300775

##  groupby+agg
从0.20.1开始，pandas引入了agg函数，它提供基于列的聚合操作。而groupby可以看做是基于行，或者说index的聚合操作。

从实现上看，groupby返回的是一个DataFrameGroupBy结构，这个结构必须调用聚合函数（如sum）之后，才会得到结构为Series的数据结果。
而agg是DataFrame的直接方法，返回的也是一个DataFrame。当然，很多功能用sum、mean等等也可以实现。但是agg更加简洁, 而且传给它的函数可以是字符串，也可以自定义，参数是column对应的子DataFrame
https://segmentfault.com/a/1190000012394176

## 特征选择 (feature_selection)

    特征是否发散：如果一个特征不发散，例如方差接近于0，也就是说样本在这个特征上基本上没有差异，这个特征对于样本的区分并没有什么用。
    特征与目标的相关性：这点比较显见，与目标相关性高的特征，应当优选选择。除移除低方差法外，本文介绍的其他方法均从相关性考虑。
https://www.cnblogs.com/stevenlk/p/6543628.html

##  Bagging（Bootstrap aggregating）、随机森林（random forests）、AdaBoost
https://blog.csdn.net/xlinsist/article/details/51475345

## 列 ——> 索引
df.set_index('date')
df.set_index('date', inplace=True) # column 改为 index
## 索引 ——> 列
df['index'] = df.index
df.reset_index(level=0, inplace=True)
df.reset_index(level=['tick', 'obs'])

## loc——通过行标签索引行数据
loc扩展——索引某列
 
print df.loc[:,['c']]

iloc——通过行号获取行数据

df[]直接索引

    直接索引索引的是列，方口号里面的内容一般是列索引名。也可以接受一个列名组成的list来接受多个列名
    索引slice对象，索引的是行，df[0:1]

http://www.cnblogs.com/daozhongshu/archive/2018/04/30/8973439.html

## 函数注解

当使用Python编写复杂的函数时，我们常常为没有合适的提示而苦恼。函数注解可以帮助我们解决这个问题。

def add(a: int, b: int) -> int:
    return a + b

## jieba 分词及词性表
 jieba.load_userdict(file_name) # file_name为自定义词典的路径 （https://blog.csdn.net/li_31415/article/details/48660073）

词性表：https://blog.csdn.net/huludan/article/details/52727298

## 类型和运算
解码：b'\xe4\xbd\xa0\xe5\xa5\xbd'.decode()
b'\xc4\xe3\xba\xc3'.decode('gb2312')
b'\xff\xfe`O}Y'.decode('utf16')
b'\x60\x4f\x7d\x59'.decode('utf16')


链接：https://www.jianshu.com/p/f6d90d53027a

