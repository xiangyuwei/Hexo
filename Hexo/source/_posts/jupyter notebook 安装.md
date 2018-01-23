#title

title: anaconda+jupyter notebook安装
# 所属分类

categories:

- python

# 标签(多个标签如下所示)

tags:

- 编程

- 深度学习


------

# 安装anaconda2和anaconda3
先在[清华镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)下载2和3
可以任意先安装一个版本，然后另一个版本安装在/envs/py2路径下，py2是自己起的文件名。
再打开CMD下载jupyter notebook

```
pip install jupyter notebook
```

notebook同时有两个版本时，可在kernel文件夹中，例如路径为D:\ProgramData\Anaconda3`\share\jupyter\kernels`，放两个kernel

可把/envs文件下的python拷贝到此路径中。
<!-- more -->