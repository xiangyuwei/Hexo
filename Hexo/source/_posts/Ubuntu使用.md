#title

title: Ubuntu使用

tags:

- Ubuntu

categories:
- 系统

---

CTRL+h  显示隐藏文件
ctrl+win +D 显示桌面
长按ｗｉｎ  显示快捷键

/usr是Unix Software Rrsources的意思，相当于windows的C盘的，C:\Windows\和C:\Program Files的结合体。

ls /usr可以得到：bin include lib share local 等等。

其中share就是安装后的文件，文件夹所在位置

而local是第三方库的位置，比如我安装了：boost和libtorrent库，就在这里面
参考：
[1](http://m.blog.csdn.net/wait_for_taht_day5/article/details/50382423)



## 中文输入法不能用

### wps

sudo gedit /usr/bin/wps

增加

>
export XMODIFIERS="@im=fcitx" 
export QT_IM_MODULE="fcitx" 

一定要在开头添加
或者
基于qt的程序下不能使用基于fcitx的中文输入法
sudo apt-get install fcitx-frontend-qt4 fcitx-frontend-qt5 fcitx-libs-qt fcitx-libs-qt5 libfcitx-qt0 libfcitx-qt5-1

### mendenley

Ubuntu

用命令locate libfcitxplatforminputcontextplugin.so找到系统中的libfcitxplatforminputcontextplugin.so。（一般是/usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so）
拷贝

重命名为libfcitxplatforminputcontextplugin.so，然后拷贝到mendeley安装位置，debian和ubuntu为：

/opt/mendeleydesktop/plugins/qt/plugins/platforminputcontexts/

Arch为：

/opt/mendeleydesktop/lib/mendeleydesktop/plugins/platforminputcontexts/

重新启动mendeley即可发现中文可以输入了。

###  不能上网
sudo gedit /etc/network/interfaces
添加如下内容：
auto enp2s0（网卡ifconfig　查看）
iface enp2s0 inet static
address 10.0.0.156
netmask 255.255.255.0
gateway 10.0.0.1
dns-nameserver 202.112.144.236

sudo gedit /etc/network/interfaces

## DNS 问题导致不能上网
sudo gedit /etc/resolv.conf
插入　nameserver 202.112.144.236

## var/tmp 文件过大，磁盘空间满
mkinitramfs× 此类文件过多
用rm -rf mkinitramfs* 删除

http://forum.ubuntu.org.cn/viewtopic.php?p=3189497
lsof看看有没有正在使用
