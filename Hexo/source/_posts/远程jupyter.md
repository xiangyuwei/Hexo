#title
title:远程登录jupyter notebook

categories:

- 服务器
- linux

tags:

- linux

------------------

## 服务器上设置

### 生成配置文件
> jupyter notebook --generate-config

### 生成密码
> ipython

In [1]: from notebook.auth import passwd
In [2]: passwd()
Enter password: 
Verify password: 
Out[2]: 'sha1:ce23d945972f:34769685a7ccd3d08c84a18c63968a41f1140274'
把生成的密文‘sha:ce…’复制下来

### 修改配置文件

>vim ~/.jupyter/jupyter_notebook_config.py

c.NotebookApp.ip='*'
c.NotebookApp.password = u'sha:ce...刚才复制的那个密文'
c.NotebookApp.open_browser = False
c.NotebookApp.port =8888 #随便指定一个端口

## 本地
本地建立一个ssh通道：

ssh wxy@服务器ＩＰ -p 端口  -L 127.0.0.1:12345:127.0.0.1:8888
浏览器上输入http://127.0.0.1:12345

http://frankchen.xyz/2017/12/25/Remote-jupyter-notebook/（'开机自启'）
https://www.cnblogs.com/wushaogui/p/8797841.html(windows)
## 另（不成功）
https://blog.csdn.net/danlei94/article/details/74049975?utm_source=itdadao&utm_medium=referral

>jupyter notebook --ip 0.0.0.0
接着你会看到有一个带token的url地址，你可以将此地址复制粘贴在你本地的浏览器，并且更换掉ip 0.0.0.0–>你服务器的ip地址

    按住 Ctrl+z键，即可将一个正在前台执行的命令放到后台，并且暂停

   >Ctrl +z （按键）

    输入jobs查看当前job的情况

    >jobs

    利用bg命令将一个在后台暂停的命令，变成继续执行

    >bg 1
    // “1” 这里就可以替换为你运行的jupyter的job号，上一步可以查到

参考文献　https://bitmingw.com/2017/07/09/run-jupyter-notebook-server/
http://bbs.bugcode.cn/t/71596 (错误，并没有用上)


## 增加内核

自己是在python3环境中conda install jupyter 下载jupyter,网上是pip3 install ipykernel
然后在python3坏境中执行'python -m ipykernel install --name XXXX'
使用命令jupyter kernelspec list可以查看当前的kernel 
jupyter notebook --config = /home.../ipython_notebook_config.py   # .py配置文件的路径,在运行时指定配置文件(只需运行一次即可更新.json配置文件，后面再运行时不用添加路径信息)

https://blog.csdn.net/Lazybones_3/article/details/78631232
https://blog.csdn.net/qq_24027563/article/details/80589880(密码没有修改的问题解决)


## 在当前环境下安装anaconda包集合
conda install anaconda
http://www.mamicode.com/info-detail-2287955.html

## 出现错误

channel 2: open failed: connect failed: Connection refused
不知道这个错误是什么原因造成的，最后换了ｃｈｒｏｍｅ浏览器访问成功

https://www.alibabacloud.com/help/zh/doc-detail/53650.htm（阿里使用jupyter）

http://www.itkeyword.com/doc/8934890860339928285/how-to-start-ipython-notebook-remotely

