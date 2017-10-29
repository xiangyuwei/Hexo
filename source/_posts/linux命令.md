#title

title: linux 命令
# 所属分类

categories:

- Linux

# 标签(多个标签如下所示)

tags:

- Linux

- 命令


------

## 后台运行

在应用Unix/Linux时，我们一般想让某个程序在后台运行，于是我们将常会用 & 在程序结尾来让程序自动运行。比如我们要运行mysql在后台： /usr/local/mysql/bin/mysqld_safe –user=mysql &。可是有很多程序并不想mysqld一样，这样我们就需要nohup命令，怎样使用nohup命令呢？这里讲解nohup命令的一些用法。

## RC版本
[百度百科](https://baike.baidu.com/item/RC%E7%89%88%E6%9C%AC/188688?fr=aladdin)解释
发布候选版，主要在于除错


## 查看文件夹中文件或文件夹的个数

[内容详细介绍](http://blog.sina.com.cn/s/blog_406127500101dgl8.html)

查看目录下有多少个文件及文件夹需在终端输入
搜索
>ls | wc -w

查看目录下有多少个文件需在终端输入
>ls | wc -c

查看文件夹下有多少个文件，多少个子目录需在终端输入
>ls -l |wc -l

若只想知道文件的个数，则需在终端输入
>/bin/ls -l |grep ^-|wc -l

## 修改用户环境
~/.bashrc
[Linux下 环境变量/etc/profile、/etc/bashrc、~/.bashrc的区别](http://blog.csdn.net/qiao1245/article/details/44650929)中：
### /etc/profile:
该文件登录操作系统时，为每个用户设置环境信息，当用户第一次登录时,该文件被执行。也就是说这个文件对每个shell都有效，用于获取系统的环境信息。
### etc/bashrc：
为每一个运行bash shell的用户执行此文件，当bash shell被打开时,该文件被读取。也就是说，当用户shell执行了bash时，运行这个文件。
### ~/.bashrc
该文件存储的是专属于个人bash shell的信息，当登录时以及每次打开一个新的shell时,执行这个文件。在这个文件里可以自定义用户专属的个人信息。
在刚登录Linux时，首先启动 /etc/profile 文件，然后再启动用户目录下的 ~/.bash_profile、 ~/.bash_login或 ~/.profile文件中的其中一个，执行的顺序为：~/.bash_profile、 ~/.bash_login、 ~/.profile。如果 ~/.bash_profile文件存在的话，一般还会执行 ~/.bashrc文件

## linux下文件的复制、移动与删除
### 文件复制命令cp
    命令格式：cp [-adfilprsu] 源文件(source) 目标文件(destination)
              cp [option] source1 source2 source3 ...  directory
    参数说明：
    -a:是指archive的意思，也说是指复制所有的目录
    -d:若源文件为连接文件(link file)，则复制连接文件属性而非文件本身
    -f:强制(force)，若有重复或其它疑问时，不会询问用户，而强制复制
    -i:若目标文件(destination)已存在，在覆盖时会先询问是否真的操作
    -l:建立硬连接(hard link)的连接文件，而非复制文件本身
    -p:与文件的属性一起复制，而非使用默认属性
    -r:递归复制，用于目录的复制操作
    -s:复制成符号连接文件(symbolic link)，即“快捷方式”文件
    -u:若目标文件比源文件旧，更新目标文件
    如将/test1目录下的file1复制到/test3目录，并将文件名改为file2,可输入以下命令：
    cp /test1/file1 /test3/file2
### 文件移动命令mv
    命令格式：mv [-fiv] source destination
    参数说明：
    -f:force，强制直接移动而不询问
    -i:若目标文件(destination)已经存在，就会询问是否覆盖
    -u:若目标文件已经存在，且源文件比较新，才会更新
    如将/test1目录下的file1复制到/test3 目录，并将文件名改为file2,可输入以下命令：
    mv /test1/file1 /test3/file2
### 文件删除命令rm
    命令格式：rm [fir] 文件或目录
    参数说明：
    -f:强制删除
    -i:交互模式，在删除前询问用户是否操作
    -r:递归删除，常用在目录的删除
    如删除/test目录下的file1文件，可以输入以下命令：
    rm -i /test/file1
### 删除文件夹
linux删除目录很简单，很多人还是习惯用rmdir，不过一旦目录非空，就陷入深深的苦恼之中，现在使用rm -rf命令即可。
直接rm就可以了，不过要加两个参数-rf 即：rm -rf 目录名字
-r 就是向下递归，不管有多少级目录，一并删除
-f 就是直接强行删除，不作任何提示的意思

## 使用awk命令获取文本的某一行,某一列

##du命令也是查看使用空间的，但是与df命令不同的是Linux du命令是对文件和目录磁盘使用的空间的查看，还是和df命令有一些区别的

来自: http://man.linuxde.net/du

## 创建文件，文件夹
touch testfile
mkdir testname
1、vi

vi 1.txt 会直接创建并打开一个文件1.txt

2、touch

touch的作用是更改一个文件或目录的时间。touch 2.txt 如果2.txt不存在，则创建空文件2.txt

3、echo 

echo “abcd” > 3.txt 可以直接创建文件3.txt并将abcd写入。

4、less 、more 、cat 

三者都是将文件内容输出到标准输出，其中less和more可以分页显示，cat是显示全部。

三者可以根据已经存在的文件创建新的文件。假设已经存在文件1.txt。

cat 1.txt > 2.txt

less 1.txt > 3.txt

more 1.txt > 4.txt

此时创建的文件内容都和1.txt中文件内容相同。

## 显卡信息查看
lspci  | grep -i vga
如果想看详细的信息，比如 GeForce GT 240，即 02:00.0

[root@localhost conf]# lspci -v -s 02:00.0
### 如何查看GPU信息
1、[显示当前GPU使用情况](http://baijiahao.baidu.com/s?id=1579864792318971483&wfr=spider&for=pc)
Nvidia自带了一个nvidia-smi的命令行工具，会显示显存使用情况：

$ nvidia-smi
  



## scp
[获取远程服务器上的文件](http://www.cnblogs.com/reddusty/p/4747481.html)

### 上传文件
scp -P 2222 root@www.vpser.net:/root/lnmp0.4.tar.gz /home/lnmp0.4.tar.gz
上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，:/root/lnmp0.4.tar.gz 表示远程服务器上的文件，最后面的/home/lnmp0.4.tar.gz表示保存在本地上的路径和文件名。

### 上传目录到服务器

scp -r local_dir username@servername:remote_dir

## [Ubuntu死机](http://www.jianshu.com/p/36fb9eed82a3)
1. 进入TTY终端

    Ctrl+Alt+F1进入TTY1终端字符界面, 输入用户名和密码以登录

    输入top命令, 找到可能造成假死的进程, 用kill命令结束掉进程。然后Ctrl+Alt+F7回到桌面

2. 直接注销用户

Ctrl+Alt+F1进入TTY1终端字符界面, 输入用户名和密码以登录。

然后执行以下的任意一个命令注销桌面重新登录。

sudo pkill Xorg

或者

sudo restart lightdm

。
SysRq是一种叫做系统请求的东西, 按住 Alt-Print 的时候就相当于按住了SysRq键，这个时候输入的一切都会直接由 Linux 内核来处理，它可以进行许多低级操作。
使用“魔法键”：Alt+SysRq + r,e,i,s,u,b（确实很好背，就是单词 busier (英语"更忙"的意思)的倒写）。

## [apt安装默认位置](http://m.blog.chinaunix.net/uid-25436678-id-3853747.html)
 1.下载的软件存放位置
       /var/cache/apt/archives

     2.安装后软件默认位置
     /usr/share

     3.可执行文件位置 
     /usr/bin

     4.配置文件位置
      /etc

     5.lib文件位置
    /usr/lib
##[常见分区和个命令作用](http://m.blog.csdn.net/u012107143/article/details/54973028)
 - /var  Variable files 软件运行所产生的数据存放目录，如日志、数据库文件、缓存文件。
 - /etc  Etcetera 系统的所有配置文件，包括通过系统自动安装的程序的配置文件，如nginx，mysql等配置文件。
 - - /bin  Binaries 普通命令，如文件操作。
 -  - /mnt  Mount 一般是用于让用户自己挂载其他文件系统，挂载后装置图标不会出现在桌面窗口的左边栏。
##[密码解锁登录密钥环](http://m.blog.csdn.net/zhangrelay/article/details/52856825)
seahorse





