# Git教程

![](img/gitlogo.jpg)

​	本教程是面向初学者的基础教程，即使你没有接触过版本控制器也可以轻松起步。这里将为你介绍 git 基础知识和常用命令，边学边练，轻松入门。

## git简介

​	git 是目前世界上最先进的分布式版本控制系统。为什么说它先进，是因为它和其他版本控制系统的主要差别在于Git只关心文件数据的整体是否发生变化，而大多数版本其他系统只关心文件内容的具体差异，这类系统（CVS，Subversion，Perforce，Bazaar 等等）每次记录有哪些文件作了更新，以及都更新了哪些行的什么内容。

​	Git另一个比较好的地方在于绝大多数操作都可以在本地执行，而每个本地都可以从服务器获取一份完整的仓库代码，而且在没网的时候仍然可以修改和使用大部分命令，在方便的时候再跟服务器进行同步，这样可以更好的实现多人联合编程。

集中式和分布式版本控制器有什么区别呢

​	先说集中式版本控制系统，版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器。中央服务器就好比是一个图书馆，你要改一本书，必须先从图书馆借出来，然后回到家自己改，改完了，再放回图书馆。

​	集中式版本控制系统最大的毛病就是必须联网才能工作，如果在局域网内还好，带宽够大，速度够快，可如果在互联网上，遇到网速慢的话，可能提交一个10M的文件就需要5分钟，这还不得把人给憋死啊。

​	分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。

​	和集中式版本控制系统相比，分布式版本控制系统的安全性要高很多，因为每个人电脑里都有完整的版本库，某一个人的电脑坏掉了不要紧，随便从其他人那里复制一个就可以了。而集中式版本控制系统的中央服务器要是出了问题，所有人都没法干活了。

​	在实际使用分布式版本控制系统的时候，其实很少在两人之间的电脑上推送版本库的修改，因为可能你们俩不在一个局域网内，两台电脑互相访问不了，也可能今天你的同事病了，他的电脑压根没有开机。因此，分布式版本控制系统通常也有一台充当“中央服务器”的电脑，但这个服务器的作用仅仅是用来方便“交换”大家的修改，没有它大家也一样干活，只是交换修改不方便而已。

## git安装
