
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


## git remote 命令 (处理本地和远端的桥梁，[shortname]是指远程仓库的别名)
	- git remote -h : 查看所有支持的remote的子命令
	- git remote -v : 显示所有远端仓库（-v的意思是列出详细信息）
	- git remote add [shortname] [url] : 添加一个新的远程仓库url，并起了一个别名shortname
	- git fetch [shortname] [分支名]: 从远程仓库进行拉取操作
	- git pull [shortname] [分支名] --allow-unrelated-histories: 是git fetch 和 git merge 的组合体，（--allow-unrelated-histories该选项可以合并两个独立启动仓库的历史）。
	- git push [shortname]  [分支名]: 向远程仓库进行push操作
	


## git多人在同一分支协作（[shortname]是远程仓库的别名）
	- 如果多人在不同的文件中操作，是不会出现冲突的。只要遵循push之前先pull的早做就没有问题。
	- pull的命令可以分解成fetch 和 merge 两个命令
		- git fetch [远程仓库shortname] [远程分支名] : 将远程分支下的最新文件下载到当前分支中
		- git log -p master [shortname/远程分支名] : 比较本地master分支和shortname/远程分支名的差别
		- git merge [分支名] : 合并分支

	- 在github上新建一个分支add_git_commandsfeature/
	- 从github上把feature/add_git_commands分支上的代码克隆到本地当前位置，并放当前未知的GitLearning_02中，并且把本地git切换到add_git_commands分支：
	 $ git clone -b feature/add_git_commands https://github.com/lengningLN/GitLearning.git GitLearning_02
	- 如果本地没有发现在本地创建的远端分支，在本地执行git fetch [shortname],如果不知道shortname，可以执行 git remote -v 来查看详细的远程分支。

## 查看某个文件的某几行代码是谁修改的
	- git blame -L 1,5 filename 



## 让master分支强制会退到某个commit
	- 用来测试的，团队开发不能这么做
	- 客户端往远端做强制的回退操作：
	- 在本地让远端master回退
	- $ git push -f origin b3f033:master
	- 在本地让远端的branch_01回退
	- $ git push -f origin b3f033:branch_01

 
## 分支操作
### 本地分支操作
	- 新建本地分支：$ git branch newBranchName
	- 切换本地分支: $ git checkout  newBranchName
	- 新建并切换本地分支：$ git checkout -b newBranchName
	- 将本地分支推送到远程：$ git push origin serverfix:awesomebranch ；  来将本地的 serverfix 分支推送到远程仓库上的 awesomebranch 分支。
	- 合并分支: 先切换到要合并的最终分支，$ git merge otherBranchName
	- 删除本地分支：$ git branch -d 分支名

### 远程分支操作

	- 新建并切换远程分支：git checkout -b dev origin/dev
	作用是checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
	- 删除远程分支：$ git push origin -d 分支名

### 如何创建远程分支？
	- 这本身就是一个有问题的问题。如果想在远程产生新分支的逻辑如下
	1. 首先本地要有一个分支，如果没有可以创建一个，通过git checkout -b dev origin/remoteBranchName ， 这就根据远程分支origin/remoteBranchName（或者一个commit）拉取代码在本地，并在本地创建dev分支，本地并且切换到dev分支上。

	2. 执行git push origin dev:newRemoteBranchName:这样就把本地分支push到远程newRemoteBranchName分支上，如果远程没有newRemoteBranchName分支，则会创建一个。



## tag的使用
	1. 查看所有的本地标签tag：git tag
	   查看所有的远程分支和标签：git ls-remote
	   查看某个标签信息：git show 2.0.0
	2. 给目前代码打标签（推荐使用附注标签）
		2.1 附注标签：git tag -a 3.0.0 -m '3.0.0封版'
		2.2 轻量标签：git tag 3.0.0
	3. 后期给之前的提交打标签
		git tag -a 2.0.1  [某次提交的校验和]

	4. 将本地标签推到远程
		- 这个过程就像工程远程分支一样
		- git push origin 3.0.0

		如果想要本地的标签一次性推送到到远程，如下会把所有不在远程仓库服务器上的标签全部传送到那里。
		- git push origin --tags

	5. 删除标签
		git版本如果是1.7.0以前可以这样
		- 删除本地标签：git tag -d 2.0.2
		- 删除远程仓库中的标签：git push origin :refs/tags/2.0.2
		git版本如果是1.7.0之后
		- git push origin -d tag 2.0.2

	6. 检出标签
		- git checkout 2.0.0 
		- 以上的做法会使你的仓库处在分离头指针的状态，如果处在这个状态，如果你做了某些修改然后提交他们，标签不会发生变化，你的新提交将不属于任何分支，并且无法访问，只能通过确切的提交哈希访问。

		- 如果需要修复旧版本的bug，通常是在这个版本的位置创建一个新分支
		- git checkout -b newBranch 2.0.0 


## 忽略代码
	1. 忽略暂存区某个文件的修改：git checkout -- filepathname
	   忽略缓存区所有文件的修改：git checkout . 
	2. 忽略缓存区（已经使用了git add ）
		忽略某个文件：git reset HEAD filepathname
		忽略所有文件：git reset HEAD .
	  注意：执行完这个操作后，本地的修改并不会消失，而是回到了1所在的状态，可以继续执行1的逻辑
	3. 已经git commit 提交代码了，还要忽略修改，输入回退
		回退到上一次commit的状态：git reset --hard HEAD^
		回退到任意版本：git reset --hard commitID











