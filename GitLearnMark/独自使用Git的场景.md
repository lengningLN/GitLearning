

## branch操作
	- 查看所有的分支：git branch -av 
	- 以图形界面的方式查看所有分支：gitk --all
	- 删除分支：git branch -d 分支名 ，如果删除的是没有合并的分支，可以通过git branch -D 分支名 强制删除。

## 修改最近一次commit的message
	- git commit --amend 会打开一个文件，里面会记录上次提交的信息。在上面修改然后保存退出即可。

## 修改任意的commit的message
	- git log -n ：查看最近n次的commit