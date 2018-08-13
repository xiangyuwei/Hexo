title: pycharm　远程配置

categories:

- pycharm


-----

## 文件映射
选择tools下deployment的ｃｏｎｆｉｇｕｒａｔｉｏｎ

选择ＳＦＴＰ,填写ip和端口，root/path 为可访问的路径，此路径自动添加到ｍａｐｐｉｎｇ
ＭＡＰＰＩＮＧ映射文件时不需要添加root/path,
Deployment path on server:
/code
这个就相当于root/path/code

自动上传服务器选择deployment 下的automatic upload
## 远程编译器
在file/seting/program/ 选择编译器，点击添加后选择'ssh' 添加远程编译器
