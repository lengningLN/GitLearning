## 工作区、暂存区、HEAD

	- 工作区：是add之前的内容
	- 暂存区：是add之后commit之前的内容
	- HEAD： 本地是最近的commit的内容,远程默认标识master分支，在clone项目是，默认在本地创建master和origin的引用。

## Git的三大类型对象
	1. commit : 每次提交都会生成一个commit对象
	2. tree   : 指文件夹对象
	3. blob	  : 指具体的某个文件，blob和文件名没有关系，只要文件名相同，就是同一个blob


## .git目录详解
	- HEAD :  指向当前分支的引用
	- config : git仓库的配置文件，local用户信息存在在此
	- refs : 引用，里面存放tags （用户设置的里程碑）和 heads（分支信息）
	- objects : 存放所有的git对象


## 跟踪分支
- 从一个远程跟踪分支检出一个本地分支会自动创建所谓的 “跟踪分支”（它跟踪的分支叫做 “上游分支”）。 跟踪分支是与远程分支有直接关系的本地分支。如果在一个跟踪分支上输入 git pull，Git 能自动地识别去哪个服务器上抓取、合并到哪个分支。


## HEAD 、master、origin的区别
- 当克隆一个仓库时，它通常会自动地创建一个跟踪 origin/master 的 master 分支。 
origin ：表示远端仓库服务器的默认名字，执行git remote 可以查看远程服务器的简写
master：表示分支名称
HEAD：当前活跃分支，可以使用checkout 命令改变本地HEAD执行的位置







