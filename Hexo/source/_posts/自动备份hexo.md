
#title

title: 自动备份Hexo博客源文件
# 所属分类

categories:

- Web

# 标签(多个标签如下所示)

tags:

- Hexo

- GitHub


------

原文出自：http://zhujiegao.com/2015/12/06/automatic-backup/

先安装git和node

# 原理

通过通过监听Hexo的其它事件来完成自动执行Git命令完成自动备份。
通过查阅Hexo文档，找到了Hexo的主要事件，见下表：

<!-- more -->
| 事件名          |   事件发生时间 | 
|- | -:|
| deployBefore  |	在部署完成前发布 |
| deployAfter   |	在部署成功后发布 |
| exit 	       | 在 Hexo 结束前发布 |
| generateBefore |	在静态文件生成前发布 |
| generateAfter  | 在静态文件生成后发布 |
| new        	   | 在文章文件建立后发布 |


# 实现

1. 在Github下创建新的仓库，取名hexo
2. 进入本地hexo文件夹，执行以下命令

```
git init
git remote add origin git@github.com:XXX/XXX.git
git pull -u origin master
git add .
git commit -m "添加hexo源码文件备份"
git pull -u origin master
```

3.安装shelljs模块
要实现这个自动备份功能，需要依赖Node.js的一个shelljs模块,该模块重新包装了child_process,调用系统命令更加的方便。该模块需要安装后使用

```
npm install --save shelljs
```

4 自动备份脚本

待到模块安装完成，在Hexo根目录的scripts文件夹下新建一个js文件，文件名随意取。

ps: 如果没有scripts目录，请新建一个。

然后在脚本中，写入以下内容：


```
require('shelljs/global');
try {
	hexo.on('deployAfter', function() {//当deploy完成后执行备份
		run();
	});
} catch (e) {
	console.log("产生了一个错误<(￣3￣)> !，错误详情为：" + e.toString());
}
function run() {
	if (!which('git')) {
		echo('Sorry, this script requires git');
		exit(1);
	} else {
		echo("======================Auto Backup Begin===========================");
		cd('D:/hexo');    //此处修改为Hexo根目录路径
		if (exec('git add --all').code !== 0) {
			echo('Error: Git add failed');
			exit(1);
		}
		if (exec('git commit -am "Form auto backup script\'s commit"').code !== 0) {
			echo('Error: Git commit failed');
			exit(1);
		}
		if (exec('git push origin master').code !== 0) {
			echo('Error: Git push failed');
			exit(1);
		}
		echo("==================Auto Backup Complete============================")
	}
}
```

