#title

title: Ubuntu 系统软件安装
# 所属分类

categories:

- Linux

# 标签(多个标签如下所示)

tags:

- ubuntu

- 软件安装


------
注意安装要在安装包目录下。


## 安装eclipse+pydev
[教程](http://www.cnblogs.com/restran/archive/2011/11/11/2245812.html)

## 安装ss

参考github上[内容](https://github.com/shadowsocks/shadowsocks-qt5/wiki/%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97)下载shadowsock

```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```

<!-- more -->

## ssh 连接远程服务器
用户user的home目录：/home/user的权限变成了777，造成不能正常登陆SSH，报如下错误：Permission denied (publickey,gssapi-with-mic


SSH对公钥、私钥的权限和所有权的要求是非常严格的，总结如下：

1、下面两个目录的所有权必须是user，所属组也应该是user，权限必须为700

\home\user

\home\user\.ssh

2、下面公钥文件的所有权必须是user，所属组也应该是user，权限必须为644

\home\user\.ssh\authorized_keys

3、下面私钥文件的所有权必须是user，所属组也应该是user，权限必须是600

\home\user\.ssh\id_rsa

将ssh公钥加入本地ssh环境中
```
ssh-add ~./ssh/wenjianming
```
改变公钥文件权限
```
chmod 700 wenjianming
```

## cmd markdown
1.去[官网](https://www.zybuluo.com/cmd/)下载＂cmd_markdown_linux64.tar.gz＂并解压;
2.运行 tar -xvf cmd_markdown_linux64.tar.gz
3.双击Cmd Markdown，或在终端运行./Cmd\ Markdown即可打开界面

gdebi可免于安装各种依赖，
```
sudo apt-get install gdebi
```
## 百度云下载
[开发者主页下载Bcloud](https://github.com/LiuLang/bcloud-packages)

## 安装微信
在网上先去下载electronic-wechat-Linux https://github.com/geeeeeeeeek/electronic-wechat/releases
双击打开解压后的文件夹，找到electronic-wechat这个文件，双击运行或者右键选择运行

## 安装qq
参考[博客](http://blog.csdn.net/zhangrelay/article/details/52398037)
Wine QQ

1  http://www.ubuntukylin.com/application/show.php?lang=cn&id=279

百度云下载地址：

1  http://pan.baidu.com/s/1hr5Z4I4

安装说明：

下载后解压，在解压后文件夹下输入如下命令：

[objc] view plain copy
print?

    sudo dpkg -i fonts-wqy-microhei_0.2.0-beta-2_all.deb  
      
    sudo dpkg -i ttf-wqy-microhei_0.2.0-beta-2_all.deb  
      
    sudo dpkg -i wine-qqintl_0.1.3-2_i386.deb   

如果，最后一步报错。使用如下命令修复：


    sudo apt-get -f install   
      
    sudo dpkg -i wine-qqintl_0.1.3-2_i386.deb  

安装完成，就可以使用了。

## 安装flash

进入保存Adobe Flash Player压缩包的路径，将压缩包解压，

首先我们执行先命令：cd 下载，进入文件下载的目录，然后在执行命令：tar -zxvf install_flash_player_11_linux.x86_64.tar.gz
sudo cp libflashplayer.so /usr/lib/firefox/browser/plugins

拷贝完之后再将“usr”目录下所有文件拷到/usr下，执行命令：

　　sudo cp -r usr/* /usr

## 网易云音乐

网易云音乐下载地址

http://music.163.com/#/download 

## 安装anaconda+tersorflow
1.首先安装Anaconda

下载Linux对应的anaconda版本，下载到你的路径 ： PATH
2.安装anaconda，

打开终端bash PATH/Anaconda3-4.0.0-linux-x86_64.sh 安装在其余路径的，请根据下面网站提示更改路径表

https://docs.continuum.io/anaconda/install

添加环境变量
```
gedit ~/.bashrc
#added by 
import PATH="/home/XXX/bin:$PATH"
soure ~/.bashrc
```

在终端或cmd中输入以下命令搜索当前可用的tensorflow版本

$ anaconda search -t conda tensorflow
选择一个较新的CPU或GPU版本，如jjh_cio_testing/tensorflow-gpu的1.0.1版本，输入如下命令查询安装命令

$ anaconda show jjh_cio_testing/tensorflow-gpu

使用最后一行的提示命令进行安装

$ conda install --channel https://conda.anaconda.org/jjh_cio_testing tensorflow-gpu
进入python，输入

import tensorflow as tf

如果没有报错说明安装成功。
装完成后，使用如下命令生成一个名为tensorflow的conda环境，根据python版本选择正确的命令执行即可

# Python 2.7
$ conda create -n TensorFlow python=2.7

# Python 3.4
$ conda create -n TensorFlow python=3.4

# Python 3.5
$ conda create -n TensorFlow python=3.5
使用如下命令进入TensorFlow环境：
source activate tensorflow

**在tensorflow下安装jupyter notebook**

查看TensorFlow的版本：

>>> import tensorflow as tf
>>> tf.__version__
'0.11.0rc2'

　　查看TensorFlow安装路径：

>>> tf.__path__
['/usr/local/ml/anaconda2/envs/tensorflow/lib/python2.7/site-packages/tensorflow']

更新tensorflow
 pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.1-cp27-none-linux_x86_64.whl
pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.1.0-cp27-none-linux_x86_64.whl
安装theano和keras

在python 3.5中，安装keras之前要安装theano。

activate tensorflow
conda install mingw libpython
conda install theano
pip install keras

## 安装google浏览器


## 安装pycharm
[下载](http://www.jetbrains.com/pycharm/download/)、然后到/bin下 ./pycharm.sh 即可
激活时使用服务器网址： http://idea.imsxm.com/
## 小知识


~代表你的/home/用户明目录
假设你的用户名是x，那么~/就是/home/x/
.是代表此目录本身，但是一般可以不写
所以cd ~/. 和cd ~ 和cd ~/效果是一样的
但是.后面有东西又是另外一个问题，点在文件名头部，代表一个隐藏文件
~/.local是你的主目录下一个.local的文件夹的路径，并且从.可以看出，这是一个饮藏文件，如果不用ls -a的话，一般ls是无法看到的apt:adobe-flashplugin?channel=$distro-partner
### 安装ｓｓｈ
>>>
sudo apt-get update  #更新一部分东西
sudo apt-get install openssh-server #安装ssh，中间选择y
sudo ps -e |grep ssh  #如果有sshd说明ssh服务已经启动，如果没有，输入sudo service ssh start启动
sudo gedit /etc/ssh/sshd_config  #配置文件
sudo apt-get install putty  #安装putty    

从本地上传文件到服务器 从服务器下载文件到本地

在终端输入

“`
scp -r 本地文件路径 服务器帐号名@服务器的adress:想要保存的路径 #从本地到服务器
scp -r 服务器帐号名@服务器的adress:文件路径 本地保存路径 #从服务器到本地

上述为本地和服务器端口号一致的时候，默认为22

如果不一致，都是在-r之后加入 -P 端口号 即可

### 修改ｈｏｓｔ
首先打开HOST文件

sudo vim /etc/hosts

添加你需要的域名

216.239.37.99 www.google.com

注意不要加上http://这样的协议前缀和/后缀等；

编辑后，你需要重新启动一下你的网络。

sudo /etc/init.d/networking restart

### 内核升级与更换顺序
http://www.360doc.com/content/13/0629/15/12892305_296361964.shtml
想把ｗｉｎｄｏｗｓ启动放在前面时调整　/boot/grub/grub.cfg　中启动顺序

### 换源

这个[博客](http://blog.csdn.net/u011557212/article/details/53233944)比较全.
1.在终端中，输入以下命令：

sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/

将下载源加入到系统的源列表
2.在终端中，输入以下命令：

wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -

导入谷歌软件的公钥，用于下面步骤中对下载软件进行验证。

如果顺利的话，命令将返回“OK”
3.在终端中，输入以下命令：

sudo apt-get update

用于对当前系统的可用更新列表进行更新。这也是许多 Linux 发行版经常需要执行的操作，目的是随时获得最新的软件版本信息。
4.在终端中，输入以下命令：

sudo apt-get install google-chrome-stable

执行对谷歌 Chrome 浏览器（稳定版）的安装
5.最后，如果一切顺利，在终端中执行以下命令：

/usr/bin/google-chrome-stable

将会启动谷歌 Chrome 浏览器

阿里云


# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse #Added by software-properties
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse 

用vi和gedit 打开 /etc/apt/sources.list 将其中的us.archive 全部替换为 cn.archive即可，这样，以后使用apt-get下载就会使用源自http://cn.archive.ubuntu.com 了
'''
vi /etc/apt/sources.list

'''

udo cp /etc/apt/sources.list /etc/apt/sources.list_backup
而后用gedit或其他编辑器打开:
 gksu gedit /etc/apt/sources.list
 kdesudo kate /etc/apt/sources.list  
 gksu mousepad /etc/apt/sources.list
 gksu leafpad /etc/apt/sources.list (12.04版)
 gksu gedit /etc/apt/sources.list
从下面列表中选择合适的源，替换掉文件中所有的内容，保存编辑好的文件:
 **注意：一定要选对版本**
然后，刷新列表:
sudo apt-get update
 **注意：一定要执行刷新**

### 显示所有文件（包含隐藏文件）
ls -a

### 只显示隐藏文件
l.
或者
ls -d .*


复制多个文件

cp /home/user/{1,2,3} /home/usr/des

外接设备在 /media/wxy 目录下
件之后带一个星号"*"的含义 表面这个文件是可执行文件

## 壁纸
Wallpaper manager 是一款桌面壁纸软件
sudo add-apt-repository ppa:baitsart/wallpaper-manager
sudo apt-get update
sudo apt-get install wallpaper-manager

或者　http://www.lovebizhi.com/linux.html

## LaTex安装

[官网](http://www.ctex.org/HomePage)

```
sudo apt-get install texlive-full  配置环境


sudoapt-getinstalltexmaker  LaTeX 文档需要一个编辑器
sudo apt-get install latex-cjk-all  字体包中包含bsmi，bkai，gkai，gbsn四种中文字体。bsmi和bkai是Big5编码的宋体和楷体字；后两者gkai和gbsn分别处理简体中文楷体字和宋体字

```

## 安装ＭｙＳＱＬ
在[官网](https://dev.mysql.com/downloads/file/?id=474212)下载系统对应版本相关安装包
community 是社区版本，开源,DEB Bundle类型就是离线deb安装包，把所有软件打包进去了,DEB Package的，这个其实就是deb文件，不过也是在线安装的形式，所以文件很小，不建议选择
安装过程参考https://www.cnblogs.com/jpfss/p/7944622.html
> sudo dpkg -i mysql-apt-config_0.8.6-1_all.deb
sudo apt-get update
sudo apt-get install mysql-server
sudo apt-get install -f

安装好之后会创建如下目录：

数据库目录：/var/lib/mysql/ 

配置文件：/usr/share/mysql（命令及配置文件） ，/etc/mysql（如：my.cnf）

相关命令：/usr/bin(mysqladmin mysqldump等命令) 和/usr/sbin

启动脚本：/etc/init.d/mysql（启动脚本文件mysql的目录）

#服务启动后端口查询sudo netstat -anp | grep mysql

复制代码

#服务管理#启动sudo service mysql start#停止sudo service mysql stop#服务状态sudo service mysql status

复制代码

#连接数据库mysql -h 127.0.0.1 -P 3306 -uroot -p123456#-h为远程IP，-P为端口号，-u为用户名，-p为密码

#测试SQLshow databases;
#首先使用以下命令删除MySQL服务器：sudo apt-get remove mysql-server#然后，删除随MySQL服务器自动安装的任何其他软件：sudo apt-get autoremove#卸载其他组件：sudo apt-get remove <<package-name>>#查看从MySQL APT存储库安装的软件包列表：dpkg -l | grep mysql | grep ii


因为安装过程密码选择sha2加密，导致workbench连接不上，解决过程参考下列文字

>ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root'

http://www.myexception.cn/mysql/2211995.html

https://my.oschina.net/leejun2005/blog/678202




## python mysqlclient

MySQLdb 名字改为了mysqlclient,下载mysqlclient　时出错：
>gcc -pthread -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -Dversion_info=(1,3,12,'final',0) -D__version__=1.3.12 -I/usr/include/mysql -I/home/wxy/anaconda2/envs/python34/include/python3.4m -c _mysql.c -o build/temp.linux-x86_64-3.4/_mysql.o
    _mysql.c: In function ‘_mysql_ConnectionObject_ping’:
    _mysql.c:1894:3: error: unknown type name ‘my_bool’
       my_bool recon = reconnect;
       ^
    error: command 'gcc' failed with exit status 1
    
    ----------------------------------------
Command "/home/wxy/anaconda2/envs/python34/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-7mflijl8/mysqlclient/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-mcyvcf3v-record/install-record.txt --single-version-externally-managed --compile" failed with error code 1 in /tmp/pip-build-7mflijl8/mysqlclient/
You are using pip version 9.0.1, however version 10.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.

在网上查了各种资料，都是要下载安装
sudo apt-get install python-dev 
sudo apt-get install gcc libffi-dev
sudo apt-get install  openssl
sudo apt-get install libssl-dev

都不对，甚至用easy_install mysqlclient也出错

>Searching for mysqlclient
Reading https://pypi.python.org/simple/mysqlclient/
Downloading https://files.pythonhosted.org/packages/6f/86/bad31f1c1bb0cc99e88ca2adb7cb5c71f7a6540c1bb001480513de76a931/mysqlclient-1.3.12.tar.gz#sha256=2d9ec33de39f4d9c64ad7322ede0521d85829ce36a76f9dd3d6ab76a9c8648e5
Best match: mysqlclient 1.3.12
Processing mysqlclient-1.3.12.tar.gz
Writing /tmp/easy_install-jlo_d443/mysqlclient-1.3.12/setup.cfg
Running mysqlclient-1.3.12/setup.py -q bdist_egg --dist-dir /tmp/easy_install-jlo_d443/mysqlclient-1.3.12/egg-dist-tmp-4972dlv6
_mysql.c: In function ‘_mysql_ConnectionObject_ping’:
_mysql.c:1894:3: error: unknown type name ‘my_bool’
   my_bool recon = reconnect;
   ^
error: Setup script exited with error: command 'gcc' failed with exit status 1

最终用mysql.c:1894:3: error: unknown type name ‘my_bool’
   my_bool recon = reconnect;搜索，找到[一篇文章](https://github.com/PyMySQL/mysqlclient-python/issues/218),
> pip install git+https://github.com/PyMySQL/mysqlclient-python.git解决了问题，好像是权限过期问题。

'搜索问题时应该找到最小的那个问题，一起查，不要查大类'

##  python 环境切换(Python多版本切换工具-Pyenv\virtualenv及Anaconda科学计算环境的配置)

https://segmentfault.com/a/1190000004020387
http://www.jb51.net/article/137786.htm

> 

    # 创建一个名为python34的环境，指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
    conda create --name python34 python=3.4

    # 此时，再次输入
    python --version
    # 可以得到`Python 3.4.5 :: Anaconda 4.1.1 (64-bit)`，即系统已经切换到了3.4的环境

    # 如果想返回默认的python 2.7环境，运行
    deactivate python34 # for Windows
    source deactivate python34 # for Linux & Mac

    # 删除一个已有的环境
    conda remove --name python34 --all

    # 安装好后，使用activate激活某个环境
    activate python34 # for Windows
    source activate python34 # for Linux & Mac
    # 激活后，会发现terminal输入的地方多了python34的字样，实际上，此时系统做的事情就是把默认2.7环境从PATH中去除，再把3.4对应的命令加入PATH

用户安装的不同python环境都会被放在目录~/anaconda/envs下，可以在命令中运行conda info -e查看已安装的环境，当前被激活的环境会显示有一个星号或者括号。

说明：有些用户可能经常使用python 3.4环境，因此直接把~/anaconda/envs/python34下面的bin或者Scripts加入PATH，去除anaconda对应的那个bin目录。这个办法，怎么说呢，也是可以的，但总觉得不是那么elegant

onda的一些常用操作如下：

 >   # 查看当前环境下已安装的包
    conda list

    # 查看某个指定环境的已安装包
    conda list -n python34

    # 查找package信息
    conda search numpy

    # 安装package
    conda install -n python34 numpy
    # 如果不用-n指定环境名称，则被安装在当前活跃环境
    # 也可以通过-c指定通过某个channel安装

    # 更新package
    conda update -n python34 numpy

    # 删除package
    conda remove -n python34 numpy

## [Linux中/var空间不足的解决办法](https://blog.csdn.net/hqzhon/article/details/49027351)
>mv /var/www /home   #将var下的www目录移动到home或者其他空间富足的区块中
ln －s  /home/www /var  #/var/www指向/home/www，这样www目录将不再占用/var目录的空间

Linux软链接：它只会在你选定的位置上生成一个文件的镜像，不会占用磁盘空间，命令：ln －s xxx
Linux硬链接：它会在你选定的位置上生成一个和源文件大小相同的文件，命令：ln xxx

  

无论是软链接还是硬链接，文件都保持同步变化。
因此，使用软链接可以将/var目录下占用空间较大的目录移动到富足的空间区块（如/home）下，使得/var下不再占用空间

## 配置http代理
>    export http_proxy="http://127.0.0.1:8084"  
    wget www.google.com  

>#访问https加密的需要设置https_proxy变量  
export https_proxy="http://127.0.0.1:8084"  
wget https://www.google.com 
[ubuntu开启http和socks全局代理测试与检验](http://govfate.iteye.com/blog/2069022)

### 安装polipo
> apt-get install polipo
  sudo gedit /etc/polipo/config
  sudo /etc/init.d/polipo restart
配置文件中添加：
socksParentProxy = "127.0.0.1:1080"
socksProxyType = socks5
proxyAddress = "0.0.0.0"
proxyPort = 17070

验证是否工作：
>export http_proxy="http://127.0.0.1:8123/"
curl ifconfig.me

[hadowsocks和polipo配置全局代理](tps://blog.denghaihui.com/2017/10/10/shadowsocks-polipo/)


