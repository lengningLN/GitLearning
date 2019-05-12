

## branch操作
	- 查看所有的分支：git branch -av 
	- 以图形界面的方式查看所有分支：gitk --all
	- 删除分支：git branch -d 分支名 ，如果删除的是没有合并的分支，可以通过git branch -D 分支名 强制删除。

## 修改最近一次commit的message
	- git commit --amend 会打开一个文件，里面会记录上次提交的信息。在上面修改然后保存退出即可。

## 修改任意的commit的message
	- git log -n ：查看最近n次的commit
	- git rebase -i 父commit的哈希值

## 合并多个commit为一个commit
	- git rebase -i 要合并的最早的commit的父commit的哈希值

## 暂存区和HEAD的比较
	- 在commit之前可以对比这次更改的内容，做一次检查，如果有不对的地方，还可以改，改完之后，再commit
	- git diff --cached

## 工作区和暂存区的比较
	- git diff : 默认比较所有文件的差异
	- git diff -- 文件一 文件二 : 只对比文件一、文件二在工作区和暂存区的区别
	- -- 标识后面要加文件

## 忽略暂存区(让暂存区所有的变更都恢复成和HEAD一致)
	- git reset HEAD  ： 忽略所有的
	- git reset HEAD 文件一 文件二  ： 忽略指定的文件

## 工作区恢复到暂存区（-- 后面跟文件）
	- git checkout -- 文件 

## 消除最近的几次提交 （代码回滚到指定的commit,）
	- git reset --hard commit_id
	- git reset --hard HEAD : 忽略工作区和暂存区，恢复到和最近的commit一致

## 正确删除文件
	- git rm 文件

## 处理临时加塞的紧急任务
	- git stash : 保存临时的变更
	- 执行完紧急的操作之后
	- git stash list : 查看临时存放的列表
	- git stash apply : 恢复到临时变更的内容,保留临时变更的记录在list中
	- git stash pop : 恢复到临时变更的内容，顺便从list删除这个临时变更的记录

## 指定不需要Git管理的文件
	- 创建 .gitigore文件，在里面写入文件名或者文件夹
	- abc ：忽略abc文件
	- abc/ ： 忽略abc文件夹下的所有文件




























