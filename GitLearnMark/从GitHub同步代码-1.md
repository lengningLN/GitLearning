## github和本地仓库同步的例子
1. 本地通过git init 创建了一个本地仓库，并且在本地创建了很多文件。
2. github上也创建了一个名为GitLearning的仓库，并且添加了.gitignore和LICENSE文件。
3. 同步本地和远程仓库
	- 通过ssh-keygen命令创建id_rsa.pub和id_rsa文件，并上传id_rsa.pub到github的SSH and GPG keys位置。
	- 在本地仓库执行 git remote add gitlearn https://github.com/lengningLN/GitLearning.git 命令，添加远程仓库
	- 通过git pull gitlearn master --allow-unrelated-histories 将远程和本地这两个独立的仓库合并成一个仓库。
	- git push gitlearn master 将本地仓库的内容推送到github