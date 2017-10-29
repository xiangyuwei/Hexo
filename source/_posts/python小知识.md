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
