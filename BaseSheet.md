# Git 常用命令

`ssh-keygen -t rsa -C "youremail@email.com"`	创建git客户端密钥

`git init`			初始化 git 仓库

`git add <file>`		添加文件到仓库

`git commit`			提交文件到仓库

`git commit -m 'xxx'`		xxx为提交信息

`git status`			查看当前状态

`git diff <file>`		查看修改（不同）

`git log`			查看所有提交日志

`git log --pretty=oneline`	提交日志在一行显示

`git log --graph`		树形显示提交日志

`git reset --hard HEAD^`	回退到上一个版本

`git reflog`			查看每一次命令

`git checkout -- <file>`		回退到最近一次 add 或 commit 的状态

`git reset HEAD <file>`		撤销暂存区的修改

`git rm <file>`			删除版本库中的文件 之后用git commit 提交

`git remote add <remotename> <remoteurl>`	关联远程仓库

`git fetch <remotename>`		拉取远程仓库

`git pull <remotename>`		拉取合并远程仓库

`git push <remotename> <branchname>` 推送分支到远程仓库

`git clone <remoteurl>`		从远程仓库克隆

`git checkout -b <branchname>`	创建并切换分支

`git branch <name`>		创建分支

`git checkout <branchname>`	切换分支

`git branch`			查看当前分支

`git merge <branchname>`	合并分支

`git branch -d <branchname>`	删除分支

`git branch -D <branchname>`	强行删除分支

`git merge --no-ff -m 'xxx' <name>` 禁用Fast forward模式合并

`git stash list`		查看储藏的工作

`git stash`			储藏当前工作现场

`git stash apply`		恢复储藏的工作现场

`git stash drop`		删除储藏的工作现场

`git stash pop`			恢复并删除储藏

`git remote`			查看远程库信息

`git remote -v`			查看远程库的详细信息

`git checkout -b <name> <remotename>/<branchname>` 在本地创建和远程对应的分支

`git branch --set-upstream <branchname> <remotename>/<branchname>` 本地分支和远程分支建立关联

`git tag <name>`		在最新提交上创建一个标签

`git tag`			查看所有标签

`git tag <name> <sha1v>`	在对应的提交上创建标签

`git show <tagname>`		查看标签详细信息

`git tag -a <tagname> -m 'message' <sha1v`> 创建带有说明的标签

`git tag -s <tagname> -m 'message' <sha1v>` 用私钥签名一个标签

`git tag -d <tagname>`		删除标签

`git push origin <tagname>`	推送标签到远程

`git push origin --tags`	推送全部尚未推送的本地标签

`git push origin :refs/tags/<tagname>` 删除一个远程标签

`git config --global user.name "yourname"` 配置个人姓名

`git config --global user.email "youremail"` 配置个人邮箱

`git config --global alias.st status` 配置别名


