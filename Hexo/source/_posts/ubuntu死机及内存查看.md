title: Ubuntu 死机原因

tags:

-- ubuntu



--------------------

## Linux查看内存大小和插槽
Linux 查看内存的插槽数，已经使用多少插槽，每条内存多大，已使用内存多大
```
dmidecode | grep  -P  -A5  "Memory\s+Device" | grep Size | grep -v Range 

Linux 查看内存支持的最大内存容量
```
dmidecode | grep -P  'Maximum\s+Capacity'

Linux 查看内存的频率
```
dmidecode | grep -A16 "Memory Device" | grep "Speed" 

查看详细的主板信息

dmidecode | grep -A16 "System Information$"

查看详细的内存信息
```
dmidecode | grep -A16 "Memory Device$"
dmidecode -t memory

## 死机原因内存查看

１．free -g,free 为０，内存基本用完

释放内存：

sync

echo 3 > /proc/sys/vm/drop_caches
２．磁盘使用，  df-h
３．磁盘I/O使用，  iostat-x 1
４．cpu用 top　或ａｔｏｐ
最右侧的%id表示剩余，若很低，则表示cpu被吃完了，在top界面按shift+p对进程使用cpu排序，能看到哪些进程占用cpu较多。
ｔｏｐ 按　Ｍ　查看内存分配
５．cat /proc/meminfo 也可以看到一些细化的内存使用信息
６．按内存占用排序：
ps -eo rss,pmem,pcpu,vsize,args | sort -k 1 -r -n | less
７.释放内存空间
Linux服务器运行一段时间后，由于其内存管理机制，会将暂时不用的内存转为buff/cache，这样在程序使用到这一部分数据时，能够很快的取出，从而提高系统的运行效率，所以这也正是linux内存管理中非常出色的一点，所以乍一看内存剩余的非常少，但是在程序真正需要内存空间时，linux会将缓存让出给程序使用，这样达到对内存的最充分利用，所以真正剩余的内存是free+buff/cache

　　但是有些时候大量的缓存占据空间，这时候应用程序回去使用swap交换空间，从而使系统变慢，这时候需要手动去释放内存，释放内存的时候，首先执行命令 sync 将所有正在内存中的缓冲区写到磁盘中，其中包括已经修改的文件inode、已延迟的块I/O以及读写映射文件，从而确保文件系统的完整性
0：0是系统默认值，默认情况下表示不释放内存，由操作系统自动管理

　　1：释放页缓存

　　2：释放dentries和inodes

　　3：释放所有缓存
｀｀｀
echo 1 > /proc/sys/vm/drop_caches


正常过程是 系统先使用内存，内存不足了再使用，tmpfs 的。tmpfs 满了，系统内存再满了，你机器就挂了。
你看看系统内存什么情况吧。
如果系统内存正常，tmpfs 满了说明你服务有问题
Slab dentry 过大导致的问题

参考资料：
[Linux系统卡顿怎么排查，top命令](https://blog.csdn.net/single6/article/details/81176213)
[记一次Linux系统内存占用较高得排查](https://m.aliyun.com/yunqi/articles/161186)
[助 Linux 真实内存占用过大, htop 命令无法展示占用的进程](https://www.v2ex.com/t/432993)
[Linux 死机原因及解决方法](https://m.hqew.com/tech/fangan_388077)
[Linux释放内存空间](https://www.cnblogs.com/freeweb/p/5713513.html)
