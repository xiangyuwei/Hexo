#title

title: Hexo + github 博客搭建过程
# 所属分类

categories:

- Web

# 标签(多个标签如下所示)

tags:

- Hexo

- GitHub


------

最近想建个博客记录一下平时的一些技术细节，以后可以随时翻翻，发现以前做过的事总是很容易忘记，真是好记性不如烂笔头,顺便整理一下思路。

> * 整理知识，学习笔记
> * 发布日记，杂文，所见所想
> * 撰写发布技术文稿（代码支持）
> * 撰写发布学术论文（LaTeX 公式支持）

------

##  搭建环境

* Windows10 64位
* node@4.4 后变成6.1.0
* hexo@3.3.7


<!-- more -->


##  前期

   百度知道了搭建博客用wordpress等需要有服务器，买不起，虽然后面知道了[`GitHub大礼包`](https://education.github.com/pack/offers#namecheap)，有[digitalOcean](https://cloud.digitalocean.com/login) 提供的优惠劵，但已经不想折腾wordpress了，以后再说。所以用了github page这个功能，再加上hexo ,类似的还有jekyll,但jekyll 好像命令有些复杂，而且需要依赖的东西有点多，所以选了hexo,hexo 用户量级好像不如jekyll。
    
##  Hexo 是什么
 **Hexo** 可以快速，简洁，高效的搭建博客框架，方便的生成*静态网页* 托管在github上。它是台湾的[@tommy351](https://github.com/hexojs/hexo)编写的，基于Node.js。

##  搭建博客

### 安装git

参考了博客http://blog.csdn.net/SmallCheric/article/details/51049683的教程，下载并安装了[Git](https://git-for-windows.github.io/)

用以下命令查看git版本
```cmd
git --version 
```

### 安装Node.js

windows环境下的Node.js的安装很简单,只需要[下载](https://nodejs.org/en/)客户端一路next就行了,第一次选择前面提到博客中的[v4.4.0LTS](https://nodejs.org/dist/v4.4.0/node-v4.4.0-x64.msi)版本64位的，后来因为css样式显示不出来，又下载了新版本V6.110，升级node又是一番折腾，后面再提。
用以下命令查看版本号：
``` cmd
node -v
```

### 安装Hexo

Node.js 安装完成后，在电脑任意位置，右键选择GitBash ,执行npm命令

* `npm install -g hexo`

安装完成后，建立一个文件夹（E:\Hexo）,在**建立的文件夹内**右键,选择gitbush,执行以下命令，就在目标文件夹下创建建立博客所需的文件。

* `hexo init`

然后 

*  `hexo install`

初始化完成目录图：
![init](\img\hexo搭建博客\hexo初始化.png)


这是参考了http://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html的教程
```bash
＄hexo g　#生成
$hexo s  #启动服务，本地浏览
```

执行以上命令，hexo会把`public`文件夹里的东西提交到github上，同时在public 文件夹中生成相关`html`文件。

**hexo s** 开启本地服务端口，打开浏览器http://localhost:4000 即可看到内容，啊哈^-^ ,没想到写到这个竟然解决的本地没有css的问题，原来自己一直是点击Index.html打开网页，不是用以上网址打开，所以css样式显示不出来，但是为什么呢，不求甚解，难道是不用那个网址没法渲染，找不到css样式，但自己看了看源代码，觉得应该能找到啊，不解。
css 代码：
```
 <link rel="stylesheet" type="text/css" href="/./main.b3331d.css">
```
顺便记录一下[路径](http://www.5idev.com/p-xhtml_path.shtml)的问题：
> ./ 当前路径
/ 网站根路径
../ 上一层目录，如../../表示上上层目录

当前路径是指和本文件同在一个文件夹下，这是可以用相对路径。

修改端口号：执行命令`hexo s -p 5000`

### 修改主题

[官方主题](https://hexo.io/themes/)
下载了2个主题：
[hexo-them-jekyll](https://github.com/pinggod/hexo-theme-jekyll)和[hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia)

下载主题：
```bash
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```
下载后的主题在`themes`文件夹中，修改`—config.yml`中的`theme: landscape`为`theme: yilia`,然后执行`hexo g`生成，注意**hexo g 每次执行都会把public 文件夹的东西更新一次，还有theme 冒号后面注意有`空格`**。

如果有问题，执行`hexo clean`,清理public 的内容，然后重新生成和发布。

### 上传
  **hexo上传代码会把以前的代码都删掉**，注意备份。
  
首先，配置ssh_key,用ssh key 解决本地与服务器连接的问题。可参考[百度经验](https://jingyan.baidu.com/article/9faa72319cd094473d28cb55.html)。
```bash
$ cd ~/.ssh #检查本机已存在的ssh密钥
```

```bash
 $ ssh-keygen -t -C "github注册邮件地址"
```

会生成一个文件`.ssh\id_rsa.pub`，复制里面的内容到github，个人设置-》SSH and GPG key中-》New SSh key

测试是否成功：
```
$ ssh -T git@github.com
```
然后配置：
```
$ git config --global user.name "**"// 你的github用户名，非昵称
$ git config --global user.email  "xxx@qq.com"// 填写你的github注册邮箱
```
  
配置：`config_yml`中deploy,
```
deploy:
  type: git
  repository: git@github.com:lian/lian.github.io.git
  branch: master
```
后又改成这个，http似乎不能写成https
```
deploy:
  type: git
  repository: http://github.com/lian/lian.github.io.git
  branch: master
```
如果报deployer not found,是因为没有安装插件。
打开 git bash，输入`hexo d`提交改动代码到github。

保留CNAME等文件
把这些文件放到`source`文件夹中，这里的所有文件会原样复制到public文件夹中。
http://blog.liuxianan.com/build-blog-website-by-hexo-github.html 中可下载作者的md文件。

介绍[markdawn 语法](http://syxiaqj.github.io/2014/02/23/write-blog-with-markdown/)
[Hexo文件夹结构](http://www.07net01.com/2016/09/1663616.html)

设置[next](https://github.com/iissnan/hexo-theme-next/)主题,参考[博客](http://joehill.me/2015/05/18/2015-05-18-Hexo-GitHub-Disqus/)。

## 搭建过程中问题



1、生成时hexo 报错 Cannot read property 'replace' of null

解决：
> _config.yml 配置文件中的url 设置错误

```
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://lian.github.io
root: \
permalink: :year/:month/:day/:title/
permalink_defaults:
```
root 后是根路径，与css文件路径有关

2、 ERROR Plugin load failed: hexo-generator-json-content

>升级node.js到最新稳定版
`升级node`，参照[博客](http://blog.csdn.net/u013049553/article/details/52424765),先安装[gnvm](https://github.com/Kenshin/gnvm)，点击exe发现在cmd下找不到，弃之，后直接下载[node](https://nodejs.org/en/download/)安装。

>执行命令  npm i hexo-generator-json-content --save

3、提交时出现错误ERROR Plugin load failed: hexo-deployer-git

解决
> 执行 npm install hexo-deployer-git --save

4、config 中文乱码
 在sublime里打开，保存为GBK-8格式

## 常见hexo命令
```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
缩写：
```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```
组合命令：
```
hexo s -g #生成并本地预览
hexo d -g #生成并上传
```

## markdown 
```
在英文输入法下:
'''
''' 表示 代码块
 #到###### 表示标题
 ** dd**  加粗
 * dd*  斜体
 [ ]（） 链接
<！-- more -->
！[init]（连接） 图片
* 标号
```

>---
title: postName #文章页面上的显示名称，一般是中文
date: 2013-12-02 15:30:16 #文章生成时间，一般不改，当然也可以任意修改
categories: 默认分类 #分类
tags: [tag1,tag2,tag3]#文章标签，可空，多标签请用格式，注意:后面有个空格

---

## 域名解析

用[namecheap](https://www.namecheap.com/)解析域名步骤参考[文章](https://m.baidu.com/from=1000953f/bd_page_type=1/ssid=0/uid=0/pu=usm%401%2Csz%40320_1002%2Cta%40iphone_2_5.1_2_7.4/baiduid=FDA30AEBE0CBCCECA0FB4F6E5B7451E6/w=0_10_/t=iphone/l=3/tc?ref=www_iphone&lid=14024493277834481532&order=4&fm=alop&tj=www_normal_4_0_10_title&vit=osres&m=8&srd=1&cltj=cloud_title&asres=1&nt=wnor&title=NameCheap%E5%90%8E%E5%8F%B0%E6%96%B0%E7%AE%A1%E7%90%86%E9%9D%A2%E6%9D%BF%E7%86%9F%E6%82%89%E5%8F%8A%E5%B8%B8%E8%A7%84%E5%BA%94%E7%94%A8%E5%90%91%E5%AF%BC%7C%E8%80%81%E5%B7%A6%E5%8D%9A%E5%AE%A2&dict=30&w_qd=IlPT2AEptyoA_yirHUqcGCkxvhNSnZsntjgNcerS8Aa&sec=22139&di=154ac76ee42df1d8&bdenc=1&nsrc=IlPT2AEptyoA_yixCFOxXnANedT62v3IEQGG_yJZ0SCboo3saPOaUbAxEmSm0n3CHkm&clk_info=%7B%22srcid%22%3A%221599%22%2C%22tplname%22%3A%22www_normal%22%2C%22t%22%3A1498824747510%2C%22sig%22%3A%22818002%22%2C%22xpath%22%3A%22div-a-h3%22%7D&sfOpen=1)

关于A解析和CNAME解析的区别：
>A解析：只能填IP地址，IP地址如果换了的话就需要换解析记录
CNAME解析：解析到另一个域名，即使被指向的域名的ip发生变化，也不需要更改解析记录。CNAME优先级高于A解析（至少在DNSPOD是这样的）

## 给网站添加favicon

这个和主题有关，默认可能没有，浏览器打开后根据开发者工具里可以看到当前主题下’favicon’的具体路径和要求文件格式，对应做一个就可以了。有时候是’png’但也有时候强制要求’.ico’，可以去[比特虫](http://www.bitbug.net/)等网站在线制作。

## 博客优化
（12月2日更新）
根据[官网](http://theme-next.iissnan.com/theme-settings.html)配置了本地搜索 社交链接 打赏功能 友情链接 百度统计

[文章阅读量统计](https://notes.wanghao.work/2015-10-21-%E4%B8%BANexT%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E9%98%85%E8%AF%BB%E9%87%8F%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD.html#%E9%85%8D%E7%BD%AELeanCloud)配置LeanCloud

[文章【字数统计】、【阅读时长】统计功能](http://www.jianshu.com/p/baea8c95e39b)

安装wordcount插件
>npm i --save hexo-wordcount
>npm install hexo-generator-searchdb --save

显示文字

用 Sublime Text 工具打开 post.swig 文件，路径如下：xxx_blog/themes/next/layout/_macro/post.swig

## [增加网站的浏览次数与访客数量统计功能](http://www.jeyzhang.com/hexo-next-add-post-views.html#)
网站的浏览次数，即pv；网站的访客数为uv。pv的计算方式是，单个用户连续点击n篇文章，记录n次访问量；uv的计算方式是，单个用户连续点击n篇文章，只记录1次访客数。你可以根据需要添加相应的统计功能。
安装busuanzi.js脚本

如果你使用的是NexT主题（其他主题类似），打开/theme/next/layout/_partial/footer.swig文件，拷贝下面的代码至文件的开头。

><script async src="https://dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js">
</script>

显示统计标签

同样编辑/theme/next/layout/_partial/footer.swig文件。

如果你想要显示pv统计量，复制以下代码至你想要放置的位置，

> <span id="busuanzi_container_site_pv">
    本站总访问量<span id="busuanzi_value_site_pv"></span>次
</span>

如果你想要显示uv统计量，复制以下代码至你想要放置的位置，

> <span id="busuanzi_container_site_uv">
  本站访客数<span id="busuanzi_value_site_uv"></span>人次
</span>


## hexo数学公式显示

这个折腾了两天，放弃之后结果莫名其妙可以显示了。

主要使用的命令
>npm install hexo-math --save
hexo math install
npm uninstall hexo-renderer-marked –save
npm install hexo-renderer-kramed –save
npm install hexo-renderer-mathjax --save

kramed是在marked上作了修改。
hexo-renderer-kramed渲染后公式消失了，最终卸载了。

最终的方案：


用编辑器打开marked.js（在./node_modules/marked/lib/中）
Step 1:

 > escape: /^\\([\\`*{}\[\]()# +\-.!_>])/,

   

替换成

  >escape: /^\\([`*\[\]()# +\-.!_>])/,

   

这一步是在原基础上取消了对\\,\{,\}的转义(escape)
Step 2:

  >em: /^\b_((?:[^_]|__)+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,

    

替换成

  >em:/^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,


进入到主题目录，找到_config.yml配置问题，把mathjax默认的false修改为true，具体如下：

># MathJax Support
mathjax:
  enable: true
  per_page: true


参考文献：
http://blog.csdn.net/emptyset110/article/details/50123231

http://masikkk.com/article/hexo-13-MathJax/