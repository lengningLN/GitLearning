## 工作区、暂存区、HEAD

	- 工作区：是add之前的内容
	- 暂存区：是add之后commit之前的内容
	- HEAD： 是最近的commit的内容

## Git的三大类型对象
	1. commit : 每次提交都会生成一个commit对象
	2. tree   : 指文件夹对象
	3. blob	  : 指具体的某个文件，blob和文件名没有关系，只要文件名相同，就是同一个blob


## .git目录详解
	- HEAD :  指向当前分支的引用
	- config : git仓库的配置文件，local用户信息存在在此
	- refs : 引用，里面存放tags （用户设置的里程碑）和 heads（分支信息）
	- objects : 存放所有的git对象


## HEAD 、master、origin的区别