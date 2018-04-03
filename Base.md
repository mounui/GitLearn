# Git基础教程

![](img/gitlogo.jpg)

### Git配置

```bash
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

`git config`命令的`--global`参数，表明这台机器上的所有Git仓库都会使用这个配置，也可以对某个仓库指定不同的用户名和邮箱地址

### 工作区、暂存区和版本库的区别

- 工作区：在电脑里能看到的目录；
- 版本库：在工作区有一个隐藏目录`.git`，是Git的版本库。  

Git的版本库中存了很多东西，其中最重要的就是称为stage（或者称为index）的**暂存区**，还有Git自动创建的`master`，以及指向`master`的指针`HEAD`。

![理解](img/git.png)

进一步解释一些命令：

- `git add`实际上是把文件添加到暂存区
- `git commit`实际上是把暂存区的所有内容提交到当前分支

### 丢弃工作区的修改

```bash
$ git checkout -- <file>
```

该命令是指将文件在工作区的修改全部撤销，这里有两种情况：

1. 一种是file自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
2. 一种是file已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态。

### 克隆仓库

```bash
$ git clone git@github.com:mounui/GitLearn.git
```

### 删除文件

```bash
$ git rm <file>
```

`git rm <file>`相当于执行

```bash
$ rm <file>
$ git add <file>
$ git commit -m "say something..."
$ git push(optional)
```

#### 删除文件解释

Q：比如执行了`rm text.txt` 误删了怎么恢复？
A：执行`git checkout -- text.txt` 把版本库的东西重新写回工作区就行了
Q：如果执行了`git rm text.txt`我们会发现工作区的text.txt也删除了，怎么恢复？
A：先撤销暂存区修改，重新放回工作区，然后再从版本库写回到工作区

```bash
$ git reset head text.txt
$ git checkout -- text.txt
```

Q：如果真的想从版本库里面删除文件怎么做？
A：执行`git commit -m "delete text.txt"`，提交后最新的版本库将不包含这个文件

### 初始化一个Git仓库

```bash
$ git init
```

### 添加文件到Git仓库

```bash
$ git add <file>
$ git commit -m "description"	# 提交暂存区的文件并添加描述
$ git commit -am "description"	# 添加并提交文件
```

`git add`可以反复多次使用，添加多个文件，`git commit`可以一次提交很多文件，`-m`后面输入的是本次提交说明。

### 添加全部修改到暂存区

```bash
git add -A .
```

- `git add -A`表示添加所有内容
- `git add .` 表示添加新文件和编辑过的文件不包括删除的文件
- `git add -u` 表示添加编辑或者删除的文件，不包括新添加的文件。

### 查看工作区状态

```bash
$ git status
```

### 查看修改内容

- `git diff` 查看工作区(work dict)和暂存区(stage)的区别
- `git diff --cached` 查看暂存区(stage)和分支(master)的区别
- `git diff HEAD -- <file>` 查看工作区和版本库里面最新版本的区别

### 版本回退

```bash
$ git reset --hard HEAD^
```

以上命令是返回上一个版本，在Git中，用`HEAD`表示当前版本，上一个版本就是`HEAD^`，上上一个版本是`HEAD^^`，往上100个版本写成`HEAD~100`。

### 回退指定版本号

```bash
$ git reset --hard commit_id
```

commit_id是版本号，是一个用SHA1计算出的序列

### 放弃暂存区修改

1. 退回工作区

```bash
$ git reset HEAD <file>
```

2. 撤销工作区的修改

```bash
$ git checkout -- <file>
```

Tip：

1. 当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- <file>`。
2. 当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了第一步，第二步按第一步操作。
3. 已经提交了不合适的修改到版本库时，想要撤销本次提交，进行版本回退，前提是没有推送到远程库。

