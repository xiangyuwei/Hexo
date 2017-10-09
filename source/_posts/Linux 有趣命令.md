#title

title: 没想到你是这样的Linux | 终端下有趣的命令合集
# 所属分类

categories:

- Linux

# 标签(多个标签如下所示)

tags:

- 有趣命令

- 软件安装


------

[转载Freebuf](http://mp.weixin.qq.com/s?__biz=MjM5NjA0NjgyMA==&mid=2651064730&idx=2&sn=89f448b84ca16a2dc19668b80a9f2f77&chksm=bd1f9b118a6812076d78b3938bf88f3d2a511dc1d1aa40879cd4af18e0ac97eb338d4987ced1&mpshare=1&scene=1&srcid=0825oAnJzsX50DcfdTsx8V3h#rd)

toilet
简介

toilet能用字母拼写出更大字母的工具，具体拼出什么字由命令后面的参数决定，不仅如此，它还能打印出各种风格的效果，比如彩色，金属光泽等。
安装

apt-get install toilet

参数解释

toilet -f mono12 -F metal FreeBuf

sl
简介

你可能了解Linux的ls命令，并经常使用它来查看文件夹的内容。但是，有些时候你可能会拼写成sl ,这时我们应该如何获得一些乐趣而不是看见“command not found”呢？
某编程牛人也经常犯把ls敲成sl的错误，所以他自己编了一个程序娱乐一下,这个程序的作用很简单，就是当你输入sl的时候终端会出现一个火车呼啸而过～～
安装

apt-get install sl


cmatrix
简介

《黑客帝国》的代码雨视觉特效。
安装

apt-get install cmatrix

参数解释

-B: 字体加粗
-C: 颜色 后面跟上参数颜色


cowsay
简介

Cowsay命令是一个有趣的命令。它会用ASCII字符描绘牛，羊和许多其他动物。但是不是每个Linux发行版都带有这个命令。
安装

apt-get install cowsay

参数解释

列出所有支持可用的动物:cowsay -l list

sciinema
简介

本文其实最初很多特效都用这个终端去录制的，但是由于需要引用外部的js，所以最后这些终端下的特效才换成了gif图。asciineme 可以完美录制完美终端下所敲的命令。
官网:https://asciinema.org/