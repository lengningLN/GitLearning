
## 常用linux命令
	1. mkdir ：创建文件夹
	2. mv 原地址/文件名 新地址/文件名 ：移动文件
	3. pwd ： 查看当前目录的路径
	4. ls -al ： 查看当前路径下所有文件（包括隐藏文件）的详细信息
	5. echo '文件内容' > 文件名 ：将文件内容写入文件，如果文件不存在则创建一个新文件
	6. 产看git某个命令的详细介绍：git 命令 -h （比如：git merge -h）

## 配置git的用户信息
	- git config --local/global/system user.name 'liuning'
	- git config --local/global/system user.email 'ning@163.com'

	- git config --unset --local/global/system user.name //清除用户名
	- git config --list --local/global/system //查看配置信息

## 创建Git仓库
	1. 用Git之前已经有项目代码
		$ cd 项目代码所在文件夹
		$ git init
	2. 用Git之前没有项目代码
		$ cd 某个文件夹
		$ git init yout_project_name #会在当前路径下创建和项目名称同名的文件夹
		$ cd your_project


## 基本操作
	- git status ： 查看工作区、暂存区的状态，包括合并分支时或者合并代码时出现冲突，显示冲突文件
	- git add 文件名 ：将工作区新建/修改的内容添加到暂存区
	- git commit -m 'message' : 提交到本地库
	- git branch newBranchName : 创建新分支
	- git branch -d branchName : 删除分支
	- git checkout otherBranchName : 切换到其他分支
	- git marge otherBranchName :  将其他分支合并到当前分支

## 查看历史（log之后的限定词命令没有先后顺序，可任意排序）
	- git log --all : 查看所有分支历史
	- git log --all --graph : 以图像化的形式显示历史
	- git log --oneline : 查看单行的简洁历史
	- git log --oneline -n3 : 查看最近三条简洁历史
	- git log --oneline - all -n3 --graph : 查看所有分支最近4条单行的图形化历史

## 查看对象
	- git cat-file 对象的哈希值 ：显示版本库对象的内容、类型以及大小信息
	- git cat-file -p 对象的哈希值 ： 根据对象的类型，以优雅的方式显示对象的内容
	- git cat-file -t 对象的哈希值 ： 显示对象类型
	- git cat-file -s 对象的哈希值 ： 显示对象的大小

## 文件比较操作
	- git diff 文件名 ： 将工作区的文件和暂存区的进行比较
	- git diff 本地库历史版本commit的哈希值 文件名 ：将工作区的文件和本地库历史记录比较，不带文件名会比较多个文件
	- git diff 一个commit的哈希值 另一个commit的哈希值 ： 比较两个版本的不同之处
	- git diff HEAD HEAD~1 (git diff HEAD HEAD^) : 比较最近两个版本的异同
	- ^ 和 ~ 都标识父节点，区别是在跟数字的时候，^2是第二个父节点，~2是父节点的父节点。^和~可以组合使用，比如：HEAD~2^2 表示当前节点的父节点的父节点的第二个父节点

## 解决冲突
	- 编辑文件，删除特殊符号，删除重复内容或者保留内容
	- 将文件修改完毕后，保存退出。
	- git add [文件名]
	- git commit -m"日志信息" (注意此时commit时不能带文件名)








