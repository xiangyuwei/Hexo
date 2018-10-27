title: matplotlib 中文显示及同时多个单词替换

tags:
- python


-----------

## 中文显示
[我们来解决一下 matplotlib 的中文显示问题](https://www.jianshu.com/p/15b5189f85a3)
[解决Linux系统中python matplotlib画图的中文显示问题](https://www.cnblogs.com/sunqifs/p/7011677.html?utm_source=itdadao&utm_medium=referral)
 
１、/fc-list (“:lang=zh”可添加此后缀单独查看安装的中文字体）
下载SimHei.ttf字体

由于系统没有任何中文字体，需要自己准备中文字体，Ubuntu支持TTF字体，这里笔者下载的是SimHei字体（百度搜索下载，注意要是ttf）

２.upyter输入并运行：

  import matplotlib

  matplotlib.matplotlib_fname()
进入到文件内容中，使用上下光标建找到

1）font.family : sans-serif ，去掉前面的 # 号

2）font.sans-serif ，去掉前面的  # 号，并在后面内容首位添加一个SimHei

３./home/linuxbrew/.linuxbrew/opt/python/lib/python3.6/site-packages/matplotlib/mpl-data

即可看到fonts文件夹—->进入ttf文件夹——->将字体拷贝进入即可
1）放到系统文件夹下:
/usr/share/fonts
2） 放到matplotlib的字体文件夹下：
/usr/local/lib/python2.7/dist-packages/matplotlib/mpl-data/fonts/ttf/

４、删除~/.cache/matplotlib缓存文件夹

一定要删除这个文件夹，一般在系统目录下面，比如ubuntu这个文件夹下面
找到fontList.cache文件

    sudo find / -name fontList.cache

假设我的在/home/user/.cache/matplotlib/fontList.cache，删除：

    rm /home/user/.cache/matplotlib/fontList.cache 

５．画图代码部分

    import matplotlib as mpl
    font_name = ‘SIMHEI’
    mpl.rcParams[‘font.family’] = font_name #用来正常显示中文标签
    mpl.rcParams[‘axes.unicode_minus’]=False #用来正常显示负号
--------------------- 


“以上方式都没解决"，
https://blog.csdn.net/u013617229/article/details/82632751
    根据os.path返回的结果，结合其他网友分享的文章得到最终的字体位置：
    os.path + site-packages/matplotlib/mpl-data/fonts/ttf

将想使用的字体命名为DejaVuSans.ttf替换上述路径下的DejaVuSans.ttf即可。
--------------------- 
https://www.cnblogs.com/lingLongBaby/p/8079588.html

常见问题

1）当matplotlib/mpl-data/fonts/ttf中没有指定字体是执行时会出现如下错误

font_manager.py:1287: UserWarning: findfont: Font family [u’sans-serif’] not found. Falling back to Bitstream Vera Sans (prop.get_family(), self.defaultFamily[fontext]))

2）有字体但还是显示小方块,一般是没有删除~/.cache/matplotlib 的缓冲目录

## pyhon 同时替换多个单词

https://blog.csdn.net/huludan/article/details/50925735
正则断言http://blog.sina.com.cn/s/blog_a71b93220102wczi.html

def multiple_replace(text, idict):
    rx = re.compile(r'\b%s\b' % r'\b|\b'.join(map(re.escape, idict)))
    def one_xlat(match):
        return idict[match.group(0)]
    return rx.sub(one_xlat, text)
