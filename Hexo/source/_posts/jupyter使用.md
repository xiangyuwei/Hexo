title: jupyter使用

catogories:

- 软件使用

tags:

- jupyter


-------------

如果希望屏蔽输出，可以在最后一条语句之后添加一个分号：”;”。
在cell中可以直接按tab键，可以自动补全
请按两下 i 按键终止循环，注意右上角的图标变回空心圈

https://www.zhihu.com/question/59392251

官方文档https://ipython.org/ipython-doc/1/interactive/notebook.html#keyboard-shortcuts
http://python.jobbole.com/87527/
Jupyter 支持多光标操作，与 Sublime Text 类似。按住 Alt 进行点击和拖拽鼠标即可。
查看快捷键的方式是使用命令面板：Cmd + Shift + P(或者Linux和Windows上 Ctrl + Shift + P)
http://liuchengxu.org/pelican-blog/jupyter-notebook-tips.html


Jupyter Notebook 有两种键盘输入模式。编辑模式，允许你往单元中键入代码或文本；这时的单元框线是绿色的。命令模式，键盘输入运行程序命令；这时的单元框线是灰色。

命令模式 (按键 Esc 开启)

Enter : 转入编辑模式
Shift-Enter : 运行本单元，选中下个单元
Ctrl-Enter : 运行本单元
Alt-Enter : 运行本单元，在其下插入新单元
Y : 单元转入代码状态
M :单元转入markdown状态
R : 单元转入raw状态
1 : 设定 1 级标题
2 : 设定 2 级标题
3 : 设定 3 级标题
4 : 设定 4 级标题
5 : 设定 5 级标题
6 : 设定 6 级标题
Up : 选中上方单元
K : 选中上方单元
Down : 选中下方单元
J : 选中下方单元
Shift-K : 扩大选中上方单元
Shift-J : 扩大选中下方单元
｀A : 在上方插入新单元｀
｀B : 在下方插入新单元｀
X : 剪切选中的单元
C : 复制选中的单元
Shift-V : 粘贴到上方单元
V : 粘贴到下方单元
Z : 恢复删除的最后一个单元
D,D : 删除选中的单元
Shift-M : 合并选中的单元
Ctrl-S : 文件存盘
S : 文件存盘
L : 转换行号
O : 转换输出
Shift-O : 转换输出滚动
Esc : 关闭页面
Q : 关闭页面
H : 显示快捷键帮助
I,I : 中断Notebook内核
0,0 : 重启Notebook内核
Shift : 忽略
Shift-Space : 向上滚动
Space : 向下滚动
编辑模式 ( Enter 键启动)

｀Tab : 代码补全或缩进｀
｀Shift-Tab : 提示｀
Ctrl-] : 缩进
Ctrl-[ : 解除缩进
Ctrl-A : 全选
Ctrl-Z : 复原
Ctrl-Shift-Z : 再做
Ctrl-Y : 再做
Ctrl-Home : 跳到单元开头
Ctrl-Up : 跳到单元开头
Ctrl-End : 跳到单元末尾
Ctrl-Down : 跳到单元末尾
Ctrl-Left : 跳到左边一个字首
Ctrl-Right : 跳到右边一个字首
Ctrl-Backspace : 删除前面一个字
Ctrl-Delete : 删除后面一个字
Esc : 进入命令模式
Ctrl-M : 进入命令模式
Shift-Enter : 运行本单元，选中下一单元
Ctrl-Enter : 运行本单元
Alt-Enter : 运行本单元，在下面插入一单元
Ctrl-Shift-- : 分割单元
Ctrl-Shift-Subtract : 分割单元
Ctrl-S : 文件存盘
Shift : 忽略
Up : 光标上移或转入上一单元
Down :光标下移或转入下一单元

## 增加kernel
首先，在anaconda中切换到myPython2环境下，确认是否安装了ipykernel这个包，如果没有则安装。
然后，在这个环境下输入一下命令



```
#xxx是在jupyter中显示的名字，建议使用环境的名字，但是不一样也没关系
# 我这里和环境名字一样，使用myPython2这个名字
python -m ipykernel install --name XXXX

---------------------

https://blog.csdn.net/wj1066/article/details/72891667?utm_source=copy 
