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

<!--more-->
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

    cp {id_rsa.pub*,id_rsa*} /home/wxy/.ssh
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

## du命令也是查看使用空间的，但是与df命令不同的是Linux du命令是对文件和目录磁盘使用的空间的查看，还是和df命令有一些区别的

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

##  查看磁盘信息。/boot空间不足
> df -lh
 dpkg --get-selections|grep linux-image
    uname -a
sudo apt-get purge linux-image-3.5.0-27-generic 使用purge卸载3.5.0-27，若使用remove卸载则会有类似3.5.0-17的遗留
sudo gdebi teamviewer_12.0.85001_i386.deb
sudo dpkg -i teamviewer_12.0.85001_i386.deb
     df
    fdisk
    fdisk -l
   sudo fdisk -l
   sudo ntfsfix /dev/sda5

http://blog.csdn.net/cloud_xy/article/details/10278769
新建备份文件夹：
devel@devServer:~$ sudo mkdir /opt/kernel
[sudo] password for devel:
devel@devServer:~$
挑选/boot下体积较大的几个文件备份出来，其中，以vmlinuz、initrd.img开头的文件较大，然后将21~27的内核中以这两个开头的全部备份至刚才新建的文件夹，最后直接删除(sudo rm –f),再查看一下，这回腾出好几十M的空间了，然后再执行之前的那个命令（sudo apt-get -f install），这回顺利更新完毕！然后再去尝试卸载那些旧的内核，所有的都能正常卸载了！

## nohup(no hang up)
nohup python -u test.py > out.log &
无论是否将 nohup 命令的输出重定向到终端，输出都将附加到当前目录的 nohup.out 文件中。如果当前目录的 nohup.out 文件不可写，输出重定向到 $HOME/nohup.out 文件中
ohup命令：如果你正在运行一个进程，而且你觉得在退出帐户时该进程还不会结束，那么可以使用nohup命令。该命令可以在你退出帐户/关闭终端之后继续运行相应的进程。nohup就是不挂起的意思( n ohang up)。

## 查看守护进程
ps -ef | grep xxx
linux进程查看系统进程信息命令主要分为：静态进程查看命令（ps）、动态进程查看命令（top）和查看进程树命令(pstree)
http://blog.csdn.net/longerzone/article/details/8015941
一、静态进程查看 ps

ps命令格式：     ps -aux     查看系统所有进程

                          ps -lA        查看所有系统的数据

                          ps axjf       连通部分进程树状态

     -A：与-e意思一样，表列出所有进程

     -a ：不与terminal有关的进程

     -u：有效用户相关的进程

      x：通常与a这个参数一起用，可以列出完整信息

输出格式：  l：较仔细列出该pid信息

                   j：工作格式

                  -f：做一个更为完整的输出


pts是所谓的伪终端或虚拟终端，具体表现就是你打开一个终端，这个终端就叫pts/0，如果你再打开一个终端，这个新的终端就叫pts /1。比如用who命令查询当前登录的用户，可以看到每个用户的TTY设备（简单来说就是用户输入命令还有显示信息的设备，比如终端）
有一个tty7是表示图形界面，我当前登录的是GNOME，当然就是图形界面了。还有tty1-tty6表示文字界面，可以用Ctrl+Alt+F1-F6切换，+F7就是切换回图形界面。下面两行说明我当前打开了两个终端窗口，所以就有pts/0和pts/1
tmux是指通过一个终端登录远程主机并运行后，在其中可以开启多个控制台的终端复用软件
tty是Teletype的缩写
 伪终端（Pseudo Terminal）
如果你发现某个进程的CMD后面接上<defunct>时，就代表该进程是僵尸进程，例如：

1  2598  2598  2598 ?           -1 Ss       0   0:00 /usr/sbin/hcid<defunct>

## 后台进程
后台进程退出是由于登陆shell收到了SIGHUP信号后在退出前将SIGHUP转发给所有的作业(jobs)。jobs由于收到SIGHUP而终止运行。 
http://doc.okbase.net/leehomjan/archive/107550.html
http://www.cnblogs.com/xianlai-huang/p/6543751.html

## dpkg：处理 smbclient (--configure)时出错：
 依赖关系问题 - 仍未被配置因为错误消息指示这是由于上一个问题导致的错误，没有写入 apport 报告。
    由于已经达到 MaxReports 限制，没有写入 apport 报告。
     在处理时有错误发生：
 nfs-common
 samba-common
 samba
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

  虽然出错，但是装的软件还是可以用的，这里好象是由于当时安装samba服务器的时候没有安装好，在网上有一篇文章:

http://hi.baidu.com/dream__land/blog/item/46dfe6fded06880109244d18.html

1.$ sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old //现将info文件夹更名
2.$ sudo mkdir /var/lib/dpkg/info //再新建一个新的info文件夹
3.$ sudo apt-get update, apt-get -f install //不用解释了吧
4.$ sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old //执行完上一步操作后会在新的info文件夹下生成一些文件，现将这些文件全部移到info_old文件夹下
5.$ sudo rm -rf /var/lib/dpkg/info //把自己新建的info文件夹删掉
6.$ sudo mv /var/lib/dpkg/info_old /var/lib/dpkg/info //把以前的info文件夹重新改回名字
## 重复执行历史命令
history 查看历史命令

例如：！255

## 查看文件大小

file ##.png
identify ##.jpg


##  密钥环
密钥环是存放保存密码的地方，以明文的方式，需要装系统时设置的密钥进行解锁
忘记登录密钥，在启动界面，进入高级选项，修复模式，ｒｏｏｔ下修改密码，passwd XXX  然后reboot
[参考官方文档](http://people.ubuntu.com/~happyaron/ubuntu-docs/precise-html/user-forgottenpassword.html)

> seahorse 进入密钥环

## bash快捷键
ctrl键组合
ctrl+a:光标移到行首。
ctrl+b:光标左移一个字母
ctrl+c:杀死当前进程。
ctrl+d:退出当前 Shell。
ctrl+e:光标移到行尾。
ctrl+h:删除光标前一个字符，同 backspace 键相同。
ctrl+k:清除光标后至行尾的内容。
ctrl+l:清屏，相当于clear。
ctrl+r:搜索之前打过的命令。会有一个提示，根据你输入的关键字进行搜索bash的history
ctrl+u: 清除光标前至行首间的所有内容。
ctrl+w: 移除光标前的一个单词
ctrl+t: 交换光标位置前的两个字符
ctrl+y: 粘贴或者恢复上次的删除
ctrl+d: 删除光标所在字母;注意和backspace以及ctrl+h的区别，这2个是删除光标前的字符
ctrl+f: 光标右移
ctrl+z : 把当前进程转到后台运行，使用’ fg ‘命令恢复。比如top -d1 然后ctrl+z ，到后台，然后fg,重新恢复
esc组合
esc+d: 删除光标后的一个词
esc+f: 往右跳一个词
esc+b: 往左跳一个词
esc+t: 交换光标位置前的两个单词。


## [压缩文件](https://m.baidu.com/from=1000953f/bd_page_type=1/ssid=0/uid=0/pu=usm%401%2Csz%40320_1002%2Cta%40iphone_2_5.1_2_12137.1/baiduid=97DBFCD8CBF6C3FA5C0C3620486ADE63/w=0_10_/t=iphone/l=3/tc?ref=www_iphone&lid=15262047774738399179&order=2&fm=alop&tj=www_normal_2_0_10_title&vit=osres&m=8&srd=1&cltj=cloud_title&asres=1&title=Linux%E4%B8%8B%E7%9A%84%E5%8E%8B%E7%BC%A9zip%2C%E8%A7%A3%E5%8E%8B%E7%BC%A9unzip%E5%91%BD%E4%BB%A4%E8%AF%A6%E8%A7%A3%E5%8F%8A%E5%AE%9E%E4%BE%8B..._%E5%8D%9A%E5%AE%A2%E5%9B%AD&dict=32&w_qd=IlPT2AEptyoA_yitJU7sE7EixhKXt9x2oUdM&sec=25761&di=f705b6df8ebb06b7&bdenc=1&nsrc=IlPT2AEptyoA_yixCFOxCGZb8c3JV3T5AAGGQmBX0DiyokaoxP4kHREsRCnrOi4IU-_wdoSOxBt8w83h_mAm8QwTaP1s)
压缩服务器上当前目录的内容为xxx.zip文件

zip -r xxx.zip ./*

解压zip文件到当前目录

unzip filename.zip
zip -r filename.zip filesdir

在这个例子里，filename.zip 代表你创建的文件，filesdir 代表你想放置新 zip 文件的目录。-r 选项指定你想递归地（recursively）包括所有包括在 filesdir 目录中的文件。

tar 命令详解

　　-c: 建立压缩档案

　　-x：解压

　　-t：查看内容

　　-r：向压缩归档文件末尾追加文件

　　-u：更新原压缩包中的文件

　　这五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。下面的参数是根据需要在压缩或解压档案时可选的。

　　-c: 建立压缩档案

　　-x：解压

　　-t：查看内容

　　-r：向压缩归档文件末尾追加文件

　　-u：更新原压缩包中的文件

　　下面的参数-f是必须的

　　-f: 使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。
主选项：

　　c 创建新的档案文件。如果用户想备份一个目录或是一些文件，就要选择这个选项。

　　r 把要存档的文件追加到档案文件的未尾。例如用户已经作好备份文件，又发现还有一个目录或是一些文件忘记备份了，这时可以使用该选项，将忘记的目录或文件追加到备份文件中。

　　t 列出档案文件的内容，查看已经备份了哪些文件。

　　u 更新文件。就是说，用新增的文件取代原备份文件，如果在备份文件中找不到要更新的文件，则把它追加到备份文件的最后。

　　x 从档案文件中释放文件。

　　辅助选项：

　　b 该选项是为磁带机设定的。其后跟一数字，用来说明区块的大小，系统预设值为20(20*512 bytes)。

　　f 使用档案文件或设备，这个选项通常是必选的。

　　k 保存已经存在的文件。例如我们把某个文件还原，在还原的过程中，遇到相同的文件，不会进行覆盖。

　　m 在还原文件时，把所有文件的修改时间设定为现在。

　　M 创建多卷的档案文件，以便在几个磁盘中存放。

　　v 详细报告tar处理的文件信息。如无此选项，tar不报告文件信息。

　　w 每一步都要求确认。

　　z 用gzip来压缩/解压缩文件，加上该选项后可以将档案文件进行压缩，但还原时也一定要使用该选项进行解压缩。

　　# tar -cf all.tar *.jpg

　　这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文

## 本地共享
 sudo smbpasswd -a wxy

## tail
1．命令格式;

tail[必要参数][选择参数][文件]  

2．命令功能：

用于显示指定文件末尾内容，不指定文件时，作为输入信息进行处理。常用查看日志文件。

3．命令参数：

-f 循环读取
-q 不显示处理信息
-v 显示详细的处理信息
-c<数目> 显示的字节数
-n<行数> 显示行数
--pid=PID 与-f合用,表示在进程ID,PID死掉之后结束.
-q, --quiet, --silent 从不输出给出文件名的首部
-s, --sleep-interval=S 与-f合用,表示在每次反复的间隔休眠S秒

## more 
more
作用：类似cat，不过会以一页一页的显示方便使用者一页页阅读
使用方法：more [选项] 文件名

## Linux 终端复用神器Tmux

## pychram 配置代码到服务器时ｍａｐ中服务器是新建文件夹名字，与ｃｏｎｎｎｅｃｔｉｏｎ中的路径连起来才是完整路径名

## winscp类似的软件Fillzilla

## 查看图片命令eog 

## 关机
注销或者重启一次ubuntu桌面。

$sudo  pkill  Xorg

## 在当前目录下找出占用空间最大的前10大文件
了解三个常用命令：

    du : 计算出单个文件或者文件夹的磁盘空间占用.
    sort : 对文件行或者标准输出行记录排序后输出.
    head : 输出文件内容的前面部分.

du：

-a：显示目录占用空间的大小，还要显示其下目录占用空间的大小
sort：

-n  : 按照字符串表示的数字值来排序

-r ：按照反序排列

head :

-n : 取出前多少行


以上的问题可以使用命令： du -a | sort -n -r | head -n 10
 du -h -x --max-depth=1可以查看每个目录下文件 文件夹的占用体积。
du -sh * | sort -n 统计当前文件夹(目录)大小，并按文件大小排序

du -sk filename 查看指定文件大小

## linux系统下/var空间不足的解决办法

mv /var/cuda-repo-8-0-local-ga2 /home

ln -s /home/cuda-repo-8-0-local-ga2 /var

>sudo mv /var/tmp /home/var_tmp
 sudo mv var_tmp tmp 改文件名　mv 命令 将文件移动，目标地址如果加 / 就 代表文件夹，如果没有 / 就会重新命名 
 sudo ln -s /home/tmp /var

## 文件末尾星号
ls -F /bin/
你会看到所有可执行文件后面都带有*  
这些特殊符号有什么含义？
*  :  可执行文件
/  :  目录
=  : 套接字
@ : 符号链接
|   : 管道文件


到了这，问题已经明白了大部分，但是为什么有的系统上只是执行了ls就会显示出这个结尾的特殊符号？并没有加-F呢！ 阿铭从公司的一台服务器上获得了答案：cat  ~/.bashrc  //其中有两行
unalias ls
alias ls='ls -Fa'


## 合并压缩文件
>cat file* > file

## md5值校验

>md5sum file1 file2 

## 添加用户
首先用adduser命令添加一个普通用户，命令如下： 

### adduser tommy 
//添加一个名为tommy的用户
#passwd tommy   //修改密码
Changing password for user tommy.
New UNIX password:     //在这里输入新密码
Retype new UNIX password:  //再次输入新密码
passwd: all authentication tokens updated successfully.

2、赋予root权限 

方法一： 修改 /etc/sudoers 文件，找到下面一行，把前面的注释（#）去掉

### Allows people in group wheel to run all commands
%wheel    ALL=(ALL)    ALL

然后修改用户，使其属于root组（wheel），命令如下：

### usermod -g root tommy

修改完毕，现在可以用tommy帐号登录，然后用命令 su - ，即可获得root权限进行操作。

方法二： 修改 /etc/sudoers 文件，找到下面一行，在root下面添加一行，如下所示：

### Allow root to run any commands anywhere
root    ALL=(ALL)     ALL
tommy   ALL=(ALL)     ALL


修改完毕，现在可以用tommy帐号登录，然后用命令 su - ，即可获得root权限进行操作。


## 按时间顺序查看文件

 ls -alt # 按修改时间排序
> ls --sort=time -la # 等价于> ls -alt
> ls -alc # 按创建时间排序
> ls -alu # 按访问时间排序
 
# 以上均可使用-r实现逆序排序
> ls -alrt # 按修改时间排序
> ls --sort=time -lra # 等价于> ls -alrt
> ls -alrc # 按创建时间排序

> ls -alru # 按访问时间排序


## 后台命令
1）&命令

          功能：加在一个命令的最后，可以把这个命令放在后台执行

（2）nohup命令

          功能：不挂断的运行命令

        

2、查看当前后台运行的命令

有两个命令可以用，jobs和ps,区别是jobs用于查看当前终端后台运行的任务，换了终端就看不到了。而ps命令用于查看瞬间进程的动态，可以看到别的终端运行的后台进程。

（1）jobs命令

        功能：查看当前终端后台运行的任务

       

       jobs -l选项可显示当前终端所有任务的PID，jobs的状态可以是running，stopped，Terminated。+ 号表示当前任务，- 号表示后一个任务。

（2）ps命令

          功能：查看当前的所有进程

          

         ps -aux | grep "test.sh"    #a:显示所有程序  u:以用户为主的格式来显示   x:显示所有程序，不以终端机来区分


3、关闭当前后台运行的命令

      kill命令：结束进程

     （1）通过jobs命令查看jobnum，然后执行   kill %jobnum

     （2）通过ps命令查看进程号PID，然后执行  kill %PID

       如果是前台进程的话，直接执行 Ctrl+c 就可以终止了


4、前后台进程的切换与控制

     （1）fg命令

       功能：将后台中的命令调至前台继续运行

       如果后台中有多个命令，可以先用jobs查看jobnun，然后用 fg %jobnum 将选中的命令调出。

     （2）Ctrl + z 命令

       功能：将一个正在前台执行的命令放到后台，并且处于暂停状态

     （3）bg命令

       功能：将一个在后台暂停的命令，变成在后台继续执行

       如果后台中有多个命令，可以先用jobs查看jobnum，然后用 bg %jobnum 将选中的命令调出继续执行。

## 内存

1，Linux下可以在/proc/cpuinfo中看到每个cpu的详细信息。但是对于双核的cpu，在cpuinfo中会看到两个cpu。常常会让人误以为是两个单核的cpu。
其实应该通过Physical Processor ID来区分单核和双核。而Physical Processor ID可以从cpuinfo或者dmesg中找到. flags 如果有 ht 说明支持超线程技术 判断物理CPU的个数可以查看physical id 的值，相同则为同一个物理CPU

2，查看内存大小:
cat /proc/meminfo |grep MemTotal
free 会以 KB 为单位显示信息。free 同样提供给我们 b (B), -k (KB), -m (MB), -g (GB) and –tera (TB)这些单位。要显示我们想要的单位，只要选择一个并在 free 后面跟上。下面一个是以 MB 为单位的输出样例。
我们想要每3秒统计一次内存利用率并且适于人类可读，那么就像这样做:

$ free -hs 3


3，其他一些可以查看详细信息的命令和方法:
uname -a               # 查看内核//的信息命令
head -n 1 /etc/issue   # 查看版本，是数字1不是字母L
cat /proc/cpuinfo      # 查看的信息命令
hostname               # 查看计算机名的linux系统信息命令
lspci -tv              # 列出所有PCI设备
lsusb -tv              # 列出所有USB设备的linux系统信息命令
lsmod                  # 列出加载的内核模块
env                    # 查看环境变量资源
free -m                # 查看内存使用量和交换区使用量
df -h                  # 查看各分区使用情况
du -sh         # 查看指定目录的大小
grep MemTotal /proc/meminfo   # 查看内存总量
grep MemFree /proc/meminfo    # 查看空闲内存量
uptime                 # 查看系统运行时间、用户数、负载
cat /proc/loadavg      # 查看系统负载磁盘和分区
mount | column -t      # 查看挂接的分区状态
fdisk -l               # 查看所有分区
swapon -s              # 查看所有
hdparm -i /dev/hda     # 查看磁盘参数(仅适用于)
dmesg | grep IDE       # 查看启动时检测状况网络
ifconfig               # 查看所有的属性
iptables -L            # 查看防火墙设置
route -n               # 查看路由表
netstat -lntp          # 查看所有监听端口
netstat -antp          # 查看所有已经建立的连接
netstat -s             # 查看网络统计信息进程
ps -ef                 # 查看所有进程
top                    # 实时显示用户
w                      # 查看活动用户
id             # 查看指定用户信息
last                   # 查看日志
cut -d: - /etc/passwd   # 查看系统所有用户
cut -d: - /etc/group    # 查看系统所有组
crontab -l             # 查看当前用户的计划任务服务
chkconfig –list       # 列出所有系统服务
chkconfig –list | grep on    # 列出所有启动的系统服务程序
rpm -qa                # 查看所有安装的软件包
cat /proc/cpuinfo ：查看CPU相关参数的linux系统命令
cat /proc/partitions ：查看linux硬盘和分区信息的系统信息命令
cat /proc/meminfo ：查看linux系统内存信息的linux系统命令
cat /proc/version ：查看版本，类似uname -r
cat /proc/ioports ：查看设备
cat /proc/interrupts ：查看中断
cat /proc/pci ：查看pci设备的信息
cat /proc/swaps ：查看所有swap分区的信息


##  ps aux

显示其他用户启动的进程（a）
查看系统中属于自己的进程（x）
启动这个进程的用户和它启动的时间（u）

## pts

虚拟终端

##scp XXX.txt XXX@192.168.1.50:/home/XXX/data
内网ip而不是路由器ip

