# GitLearn
## 安装

- git OSX：http://git-scm.com/download/mac
- git Windows：http://git-for-windows.github.io/
- git Linux：http://book.git-scm.com/2_installing_git.html

## 多个客户端共用SSH私钥

首先把旧的SSH Public/Private Key文件id_rsa和id_rsa.pub文件拷贝到U盘中，然后在新的客户端执行下面命令
```
git config --global user.name "your name"	// 尽量保持和以前一致
git config --global user.email "your email"
ssh-keygen
```
这样会在新的~/.ssh/中生成新的id_rsa和id_rsa.pub，然后用备份好的id_rsa和id_rsa.pub文件覆盖新的文件，确保上面的两个文件的权限是正确的，id_rsa是600，id_rsa.pub是644

## 创建新仓库

创建新文件夹，打开，然后执行`git init`以创建新的 git 仓库

## 检出仓库

执行如下命令创建一个本地仓库的克隆版本：

```shell
git clone /path/to/repository
```

如果是远端服务器上的仓库，你的命令会是这个样子：

```shell
git clone username@host:/path/to/repository
```

## 工作流

你的本地仓库由 git 维护的三棵“树”组成。第一个是你的**工作目录**，它持有实际文件；第二个是**暂存区（Index)**，它像个缓存区域，临时保存你的改动；最后是**HEAD**，它指向你最后一次提交的结果。

![](img/git.png)

## 添加和提交

你可以提出更改（把它们添加到暂存区），使用如下命令：

```shell
git add <filename>
git add *
```

这是git基本工作流程的第一步；使用如下命令以实际提交改动：

```shell
git commit -m "代码提交的信息"
```

现在，你的改动已经提交到了HEAD，但是还没到你的远程仓库。

## 推送改动

执行如下命令可以将本地的改动推送到远程库：

```shell
git push or origin master	// origin:remote name	master:local branch
```

可以把master换成你想要推送的任何分支。

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，可以用如下命令添加：

```shell
git remote add origin <server>
```

如此你就能够将你的改动推送到所添加的服务器上去了。

## 分支

分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master是“默认的”的分支。在其他分支上进行开发，完成后再将它们合并到主分支上。

![](img/brand.png)

```shell
git checkout -b feature	// 创建一个叫做feature的分支，并切换过去
git checkout master		// 切换回主分支
git branch -d feature	// 删除feature分支
git push origin <branch>// 将分支推送到远程仓库，不然其他人是看不到的
```

## 更新与合并

更新你的本地仓库至最新改动：

```shell
git pull
```

以在你的工作目录中 获取（fetch） 并 合并（merge） 远端的改动。

要合并其他分支到你的当前分支（例如 master），执行：

```shell
git merge <branch>
```

在这两种情况下，git 都会尝试去自动合并改动。遗憾的是，这可能并非每次都成功，并可能出现冲突（conflicts）。 这时候就需要你修改这些文件来手动合并这些冲突（conflicts）。改完之后，你需要执行如下命令以将它们标记为合并成功：

```shell
git add <filename>
```

在合并改动之前，你可以使用如下命令预览差异：

```shell
git diff <sourch_branch> <target_branch>
```

## 标签

为软件发布创建标签是推荐的。这个概念早已存在，在 SVN 中也有。你可以执行如下命令创建一个叫做 1.0.0 的标签：

```shell
git tag 1.0.0 1b2e1d63ff
```

1b2e1d63ff 是你想要标记的提交 ID 的前 10 位字符。可以使用下列命令获取提交 ID：

```shell
git log
```

你也可以使用少一点的提交 ID 前几位，只要它的指向具有唯一性。

## 日志

如果你想了解本地仓库的历史记录，最简单的命令就是使用: 

```shell
git log
```

你可以添加一些参数来修改他的输出，从而得到自己想要的结果。 只看某一个人的提交记录:

```shell
git log --author=mounui
```

一个压缩后的每一条提交记录只占一行的输出:

```shell
git log --pretty=oneline
```

或者你想通过 ASCII 艺术的树形结构来展示所有的分支, 每个分支都标示了他的名字和标签: 

```shell
git log --graph --oneline --decorate --all
```

看看哪些文件改变了: 

```shell
git log --name-status
```

这些只是你可以使用的参数中很小的一部分。更多的信息，参考：

```shell
git log --help
```

## 撤销本地改动

假如你操作失误，你可以使用如下命令替换掉本地改动：

```shell
git checkout -- <filename>
```

此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到暂存区的改动以及新文件都不会受到影响。

假如你想丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版本历史，并将你本地主分支指向它：

```shell
git fetch origin
git reset --hard origin/master
```

## 实用小贴士

内建的图形化 git：

```shell
gitk
```

彩色的 git 输出：

```shell
git config color.ui true
```

显示历史记录时，每个提交的信息只显示一行：

```shell
git config format.pretty oneline
```

交互式添加文件到暂存区：

```shell
git add -i
```

## 其他资源

- [Git官网](http://git-scm.com/)
- [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [蒋鑫老师带你入github的大门](http://www.worldhello.net/gotgithub/)
- [Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/)
- [Git 忽略规则gitignore](https://github.com/github/gitignore)
- [GitHub 帮助](http://help.github.com/)
- [图解 Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)
- [Git简明手册](http://www.mceiba.com/tool/git-cheat-sheet.html)
- [Git Community Book 中文版](http://gitbook.liuhui998.com/index.html)
- [Pro Git](http://git-scm.com/book/en/v2)
- [git-简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)
- [learnGitBranching 在线学习工具](http://pcottle.github.io/learnGitBranching/)
- [Pro Git中文版](http://www.open-open.com/lib/view/open1328069609436.html)
- [oschina教程](http://git.oschina.net/progit/)
- [How to undo (almost) anything with Git撤销一切，汇总各种回滚撤销的场景，加强学习。](https://github.com/blog/2019-how-to-undo-almost-anything-with-git)
- [Github 15分钟学习Git](https://try.github.io)
- [Git 教程 | 菜鸟教程runoob.com](http://www.runoob.com/git/git-tutorial.html)
- [Git 本地仓库和裸仓库](https://gold.xitu.io/post/5842f9b861ff4b005889ade6)
- [沉浸式学 Git](http://www.kancloud.cn/kancloud/igit/46710)
- [Git进阶用法，主要是rebase高级用法](http://way.oschina.io/2016/12/15/notes/GitAdvance/?utm_source=gank.io&utm_medium=email)
- [成为一个git大师](https://www.atlassian.com/git/tutorials)
- [高质量的Git中文教程](https://github.com/geeeeeeeeek/git-recipes)
