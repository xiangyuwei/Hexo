
#title

title: DigitalOcean+shadowSocks + Docker 科学上网+挖矿
# 所属分类

categories:

- Web

# 标签(多个标签如下所示)

tags:

- DigitalOceam

- 科学上网
- Docker


------

## ss科学上网

注册[DigitalOcean](https://www.digitalocean.com/?refcode=e188e648d051)，从[这个链接](https://m.do.co/c/e70af193c2c0) https://m.do.co/c/e70af193c2c0 进去可以有$10的优惠券。


<!-- more -->

参考[教程](http://cnodejs.org/topic/56a6d3c67ec020ed4b96b357)上的步骤创建了一个Droplet,选了洛杉矶的服务器，不过好像有点慢，下载了DOcker,拉取了Docker中shadowSock镜像，端口号为1984,。[另一篇](http://liujin.me/blog/2015/05/27/Docker-DigitalOcean-Shadowsocks-5-%E5%88%86%E9%92%9F%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91/)参考。[这篇](http://www.jianshu.com/p/864a7d2a2a5f)里有详细解释。

这几天发现上不了外网，用`docker ps` 发现报错，连接不到守护进程，
service docker  stop 后 docker -d ,service docker start
查看docker是否在运行`ps aux | grep  docker`
`docker info`查看信息2017/7/4 11:53:55 
[windows查看端口被占用](http://www.cnblogs.com/wangcp-2014/p/5780056.html)：
```
netstat -ano
net -ano|findstr "***"
tasklist|findstr "***"
```
[linux查看端口被占用](http://www.cnblogs.com/benio/archive/2010/09/15/1826728.html)
```
ps -aux | grep tomcat
netstat -apn
ps -aux | grep ***
```
[使用shadowsocks，搭建ipv6 VPN，让ipv4上ipv6，下载速度提升到100M](https://www.polarxiong.com/archives/%E6%90%AD%E5%BB%BAipv6-VPN-%E8%AE%A9ipv4%E4%B8%8Aipv6-%E4%B8%8B%E8%BD%BD%E9%80%9F%E5%BA%A6%E6%8F%90%E5%8D%87%E5%88%B0100M.html)

[一键脚本配置](ttp://tieba.baidu.com/p/5105380292)
## 挖矿

### 第一步
百度一不小心看到了[服务器挖莱特比](http://www.linuxde.net/2013/12/15514.html)，心血来潮试了一下挖[莱特币](http://www.laiteb.com/)

接着在服务器上安cpuminer,最终没装上。先下载一堆[依赖包](https://baijiahao.baidu.com/po/feed/share?wfr=spider&for=pc&context=%7B%22sourceFrom%22%3A%22bjh%22%2C%22nid%22%3A%22news_4042329101433198772%22%7D),又在github上[下载包](https://github.com/noncepool/cpuminer-yescrypt),参考这篇[博客](https://rumorscity.com/2014/01/04/compile-and-install-cpuminer-on-linux-centos/)，但``./config`报错

![编译报错](\img\digitalOceam 科学上网\编译报错.png)

>gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:3447: $? = 1
configure:3436: gcc -qversion >&5
gcc: error: unrecognized command line option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:3447: $? = 1
configure:3467: checking whether the C compiler works
configure:3489: gcc -03   conftest.c  >&5
gcc: error: unrecognized command line option '-03'
configure:3493: $? = 1
configure:3531: result: no

按照这[上面](http://bbs.csdn.net/topics/390222850)添加`环境变量`并没有解决。

这篇[文章](http://www.iitshare.com/linux-litecoin-ltc-mining-tutorial.html)里的方法还没试。

## Xshell
### 生成密钥
过程中想用Xshell连接服务器，发现需要用户密钥.

```bash
#ssh-keygen -t rsa 
```

生成[密钥对](http://blog.sina.cn/dpool/blog/s/blog_6561ca8c0102vb0d.html
)服务器上的密钥在authorized_key文件中

### 安装vsftpd
在服务器上安装了vsftpd
>[which](http://man.linuxde.net/which)  vsftpd
看有没有安装vsftpd。
```
service vsftp start #启动服务
service vsftp stop # 停止服务
service vsftp restart #重启服务
```
用[vi](http://man.linuxde.net/vi) 修改[配置文件](http://m.jb51.net/LINUXjishu/66611.html)
>：q是退出，当不存在任何没有保存的修改时它才会用
:q!是退出并不保存。
u可以取消刚才的修改，ctrl＋R可以取消你所取消的修改。
注意：有：号的命令是先ESC，再：命令回车执行，不带：的，就是ESC后再输入执行。
忘 了当前编辑的是什么文件，可以用ctrl＋G来查看。
VI中可以执行命令。:!command就可以执行命令。命令完成后，可以按回车返回。
甚至可以在VI中使用SHELL，（：！bash）从SHELL中执行几个命令后，exit退回到VI。
保存退出，ZZ或:wq。

### FTP传输
ftp 传输有主动模式和被动模式，
由客户端选择，一般cmd是主动模式，应在控制面板internet选项高级中把被动ftp关闭
```
ftp>passive #可开/关被动模式
```
ftp 命令：
> open ip 打开连接
  put 文件 上传文件
  get 文件名 下载文件
  close 关闭连接
  bye/quit 离开ftp
 
ftp 默认传输的文件在c盘的用户目录下
标签（空格分隔）： 科学上网

---






