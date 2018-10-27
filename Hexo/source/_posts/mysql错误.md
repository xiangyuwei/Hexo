title: mysql错误集及使用
# 所属分类

categories:

- 编程

# 标签(多个标签如下所示)

tags:

- 编程
- mysql

-------

## 1114 – The table ‘xxxx’is full解决方法
ubuntu中mysql 的配置文件 my.cnf 的路径是/etc/mysql/my.cnf。
2、其它非debian系列的linux中mysql的配置文件my.cnf的路径一般是/etc/my.cnf。


## ERROR: Export data to file: ('Lost connection to MySQL server during query', 2013

MySQL workbench Q&A找到原因，链接如下  https://dev.mysql.com/doc/workbench/en/workbench-faq.html#faq-workbench-error-lost-connection

 

Yes, go to ' edit ,Preferences, SQL Editor', and adjust the DBMS connection read time out option that defaults to 600 seconds. This sets the maximum amount of time (in seconds) that a query can take before MySQL Workbench disconnects from the MySQL server.

 

通过修改红色字体的值，并重启启动workbench 生效（一定要重启哦！）。


## The MySQL server is running with the --secure-file-priv option

```
mysql -u -p
show variables like '%secure%';查看 secure-file-priv 当前的值是什么
导出的数据必须是这个值的指定路径才可以导出，默认有可能是NULL就代表禁止导出，所以需要设置一下


知道mysql安装路径下的my.ini文件，设置一下路径：
然后重启数据库即可

##  Error executing task: 'ascii' codec can't decode byte 0xc4 in position 32: ordinal not in range(128)
存储路径名不要有中文
https://bbs.csdn.net/topics/390347030
https://blog.csdn.net/ACMAIN_CHM/article/details/4174186


## mysql 导出csv

命令行：
SELECT * FROM server_warning_repaired

into outfile '/tmp/test.csv'
https://my.oschina.net/u/2335552/blog/733185

mysql workbench:
表的右键有导出数据选项，但好像只能一张表一张表
整个数据库的导出是导出sql

## 查看端口
终端mysql -uroot -ppasswd 进入
show global variables like 'port';查看端口号

https://blog.csdn.net/LANGZI7758521/article/details/51391932


