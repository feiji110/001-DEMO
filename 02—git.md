<span style="color:rgb(102,102,102);"><span style="font-size:18px;"><video id="video" controls="controls" preload="preload" poster="http://media.w3.org/2010/05/sintel/poster.png" >
		<source id="mp4" src="http://media.w3.org/2010/05/sintel/trailer.mp4" type="video/mp4">
		<source id="webm" src="http://media.w3.org/2010/05/sintel/trailer.webm" type="video/webm">
		<source id="ogv" src="http://media.w3.org/2010/05/sintel/trailer.ogv" type="video/ogg">
		Your user agent does not support the HTML5 Video element.
</video>
<audio controls="controls" preload="preload" autoplay="autoplay">
		<source src="http://other.web.ra01.sycdn.kuwo.cn/resource/n3/128/17/55/3616442357.mp3" type="audio/mp3" >
		您所用的浏览器不支持HTML5 audio标签。

1.世界上最先进的版本控制系统
# 创建空目录

```
	$ mkdir learngit
	$ cd learngit	
	$ pwd      **显示当前目录**
```
# 将目录变为git可管理的仓库
```
	$ git init 
```
# 将文件添加到仓库 
    $ git add readme.md
> tips : 可以多次add file
# 将文件提交到仓库
    $ git commit -m"wrote a readme file "
> tios commit 可以一次提交多个文件
# 仓库当前状态
	$ git status
# 查看具体修改内容
    $ git diff
# 查看版本
	$ git log   [--pretty=oneline]
# 版本回退
	$ git reset --hard HEAD^    /*commit_id */
# 查看记录的每一次git命令
    $ git reflog
 # Working Directory and Index
1. Working Directory:电脑里能看到的目录
2. Repository:工作区的一个隐藏目录**“ .git ”**版本库里有很多东西
	+ 最重要的就是称为Stage (index)的暂存区
	+ Git自动为我们创建的第一个分支master
	+ 指向master的一个指针交HEAD
![示意图](https://img-blog.csdnimg.cn/20190125225645216.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQzNDE0MTE0,size_16,color_FFFFFF,t_70)
# 管理修改
