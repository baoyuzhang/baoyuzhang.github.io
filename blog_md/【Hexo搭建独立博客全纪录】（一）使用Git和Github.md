---
title: 【Hexo搭建独立博客全纪录】（一）使用Git和Github
date: 2017-04-28 10:57:39
tags:
- Hexo
- Git
- Github
categories:
- 前端工具
---
从开始着手搭建博客，完整的学习Git，Markdown语法，到用Hexo搭建博客成功，再到后期在原有主题的基础增加功能性和视觉上的优化，折腾了三四天，总算看倒腾出了一个看上去基本满意的博客。由于时间关系，还有很多想法没有实现，后面会不断地改进和优化。今天先来说一说学习使用Git和Github。

<!---more--->

去年十月第一次接触Github，慕名而来，当时觉得这是一个高的触不可及的平台，我等渣渣还是退下吧...直到今年过完年回来二月份才开始真正使用Github，不熟悉命令行的我对Git Bush是绕着走的，在慕课网上看到Github可以使用友好的图形化客户端来操作，心中一阵窃喜。现在看来，当时真是too young too simple，因为命令行真的是好用啊！而且一点都不难，so easy~当初用客户端还把自己搞得晕晕乎乎的，当时在想这东西这么复杂怎么还这么火，还怀疑自己是不是不适合做程序员...本以为自己走了捷径，却害苦了自己！好了，闲话到此为止，进入正题。

结论：拒绝客户端，直接学习Git！

学习Git和Github，我主要是跟着[Git使用教程](http://www.cnblogs.com/tugenhua0707/p/4050072.html)来做的，文中每一步都有图和解释，超详细，手把手教你使用Git和Github，极力推荐给正在入门的小白！参考该教程、文后的链接和我自己的理解，构成本文的内容。由于目前个人用不到多人协作，因此本文并未提及，如有需要，也请参考[Git使用教程](http://www.cnblogs.com/tugenhua0707/p/4050072.html)。

此处列出了一些我收藏的公认的比较好的Git教程，可以作为深入学习资料

- [Git使用教程](http://www.cnblogs.com/tugenhua0707/p/4050072.html) 本文主要参考

- [Git教程 - 廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 大牛博客，还包含JS，Python等教程，都很棒

- [git 使用简易指南](http://www.bootcss.com/p/git-guide/)

- [图解Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html) 图文并茂，对git工作原理的理解帮助很大

- [Git - Book](https://git-scm.com/book/zh/v2)

- [GitHub Guides](https://guides.github.com/) GitHub官方指南，很多都有中文翻译，可以自己搜一下

- [理解 GitHub Flow · GitHub 指南](http://gitbeijing.com/flow/) 理解Github工作原理，GitHub官方指南中文翻译的一部分


## Git简介

### Git是什么？
Git是目前世界上最先进的分布式版本控制系统。
### SVN（集中式）与Git（分布式）的最主要的区别？

SVN是集中式版本控制系统，版本库集中放在中央服务器。干活的时候用自己的电脑，首先要从中央服务器哪里得到最新的版本，然后干活，干完后把自己做完的活推送到中央服务器。集中式版本控制系统必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就难办了。

Git是分布式版本控制系统，没有中央服务器。每个人的电脑就是一个完整的版本库，工作的时候不需要联网。既然每个人的电脑都有一个完整的版本库，那多个人如何协作呢？比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们俩只需把各自的修改推送给对方，就可以互相看到对方的修改了。

## 安装Git（windows）

### 安装
建议到[Git官网](https://git-scm.com/)下载最新版本，国内访问会很慢，可以到网上搜索下载，然后默认安装即可。安装完成后，在开始菜单里面找到 "Git --> Git Bash"，如下：
!["Git --> Git Bash"](/img/01.jpg)

弹出一个类似的命令窗口的东西，就说明Git安装成功。如下：
!["git安装成功"](/img/2017-04-28_165817.png)

### 设置用户名和邮箱
因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识。在命令行输入如下：
!["设置邮箱和用户名"](/img/2017-04-28_171200.png)

**注意！**`git config  --global` 参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。

查看已设置的用户名和邮箱，在命令行输入如下：
!["查看邮箱和用户名"](/img/2017-04-28_171259.png)

## 使用Git

### 创建版本库repository
版本库：又名仓库，英文名repository。可简单的理解一个目录，这个目录里面的所有文件都会被Git管理，每个文件的修改，删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻还可以将文件“还原”。

命令 | 释义
----|------
**打开所在目录** |
cd folder | 打开文件夹
mkdir folder | 新建文件夹
pwd | 显示当前目录
**初始化：将当前目录变为git仓库** |
git init	 | 当前目录→git可管理仓库
**添加文件到版本库** |
git add file	| 将file文件添加到暂存区
git commit -m "提交说明"	| 将暂存区中所有文件提交到仓库
git status	| 查看当前目录中是否有文件未提交

#### 打开所在目录
创建一个版本库，如在D:/www下 目录下新建一个testgit版本库，在命令行输入如下：
!["创建版本库"](/img/2017-04-28_173436.png)

#### 初始化：将当前目录变为git仓库
!["初始化"](/img/2017-04-28_174138.png)

**注意！** 这时当前testgit目录下会多一个.git的目录，这个目录是Git来跟踪管理版本的，千万不要手动乱改这个目录里面的文件，否则，会把git仓库给破坏了。如下：
![".git"](/img/2017-04-28_174458.png)


#### 添加文件到版本库
作为测试，在当前目录下新建一个readme.txt，并写入11111111保存，之后进行如下3步操作：
!["添加文件到版本库"](/img/2017-04-28_180144.png)

`git status` 结果显示没有任何文件未提交。

### 修改和版本回退
命令 | 释义
----|------
**修改文件内容** |
git diff file	| 查看file文件修改内容
**查看历史记录** |
git log | 查看历史记录
git log --pretty=oneline |查看历史记录（简洁版）
**版本回退** |
git reset --hard HEAD^	 | 退回到上个版本
git reset --hard HEAD^^	 | 退回到上上个版本
git reset --hard HEAD~100	 | 退回到前100个版本
**恢复最新版本** |
git reflog	 | 获取全部版本号
git reset --hard 版本号	 | 退回到版本号的版本
cat file	 | 查看文件内容

#### 修改文件内容
继续，修改readme.txt内容，在下面添加一行22222222内容，继续使用git status查看结果，如下：
!["git status"](/img/2017-04-28_211211.png)

 结果显示，readme.txt文件已被修改，但是未被提交的修改。接下来我想看下readme.txt文件到底改了什么内容，如何查看呢？可以使用如下命令：
 !["git diff"](/img/2017-04-28_211553.png)

 结果显示，readme.txt文件内容从一行11111111改成两行，添加了一行22222222内容。

 知道了对readme.txt文件做了什么修改后，我们可以放心的提交到仓库了，提交修改和提交文件是一样的两步(第一步是git add  第二步是：git commit)。如下：
 !["增加222"](/img/2017-04-28_212240.png)

`git status`：提交文件之前，查看一下状态；提交文件之后，继续查看一下状态，显示没有可提交的文件

**说明：** 所有的版本控制系统，只能跟踪文本文件的改动（如txt文件，网页，所有程序的代码等）。对于图片，视频这些二进制文件，只能把每次改动串起来，无法跟踪文件的变化，即：知道图片从1kb变成2kb，但是到底改了什么，版本控制系统也不知道

#### 查看历史记录
继续对readme.txt文件进行修改，再增加一行
内容为33333333，然后执行命令如下：
!["增加333内容"](/img/2017-04-28_213243.png)

现在我已经对readme.txt文件做了三次修改了，那么我现在想查看下历史记录，如何查看呢？使用命令 `git log` ,如下：
!["git log"](/img/2017-04-28_213915.png)

结果显示，从最近到最远的显示日志，我们可以看到最近三次提交，最近的一次是“增加333内容”，上一次是“增加222内容”。

如果嫌上面显示的信息太多的话，可以用缩减版显示，如下：
!["git log --pretty=oneline"](/img/2017-04-28_214341.png)

#### 版本回退
现在我想使用版本回退操作，我想把当前的版本回退到上一个版本，要使用什么命令呢？可以使用如下2种命令，第一种是`git reset  --hard HEAD^` ；那么如果要回退到上上个版本只需把`HEAD^ 改成 HEAD^^`， 以此类推。那如果要回退到前100个版本的话，使用上面的方法肯定不方便，我们可以使用下面的简便命令操作：`git reset  --hard HEAD~100` 即可。未回退之前的readme.txt内容如下：
!["未回退内容"](/img/2017-04-28_214610.png)

回退到上一个版本，如下
!["回退到上一个版本"](/img/2017-04-28_214824.png)

查看现在readme.txt文件中的内容，如下：
!["查看内容"](/img/2017-04-28_214936.png)

结果显示，"增加333内容"我们没有看到了。

#### 恢复最新版本
现在我想恢复到最新的版本(有333333内容版本)要如何恢复呢？可以通过版本号回退。

但是现在的问题假如我已经关掉过一次git bush，或者333内容的版本号我并不知道呢？要如何知道增加3333内容的版本号呢？如下：
!["查看版本号"](/img/2017-04-28_215744.png)

结果显示，"增加333内容"的版本号是 c83a6bb。现在可以通过版本号回退了，如下：
!["版本号回退"](/img/2017-04-28_220020.png)

结果显示，目前已经是最新的版本。

#### 理解工作区、暂存区、版本库
**工作区：** 你在电脑上看到的目录，比如目录testgit里的文件(.git隐藏目录版本库除外)，以后需要再新建的目录文件等等都属于工作区范畴。

**版本库：** 工作区里的隐藏目录.git，这个不属于工作区，这是版本库。版本库中存了很多东西：
- **暂存区(stage)** ——最重要！（暂存区是版本库的一部分）
- Git为我们自动创建了第一个分支master
- 指向当前分支的指针HEAD

前面说过使用Git提交文件到版本库有两步：

- 第一步：`git add` 把文件添加进去，实际上就是把文件添加到暂存区；

- 第二步：`git commit` 提交更改，实际上就是把暂存区的所有内容提交到当前分支上。

下面来举例说明。

在readme.txt再添加一行内容为4444444，接着在目录下新建一个文件为test.txt 内容为test，我们先用命令`git status`来查看下状态，如下：
!["工作区、暂存区、版本库"](/img/2017-04-28_222758.png)

先使用git add 命令把2个文件都添加到暂存区中，再使用git status来查看下状态，如下：
!["git add"](/img/2017-04-28_223111.png)

接着使用git commit一次性提交到分支上，如下：
!["一次性提交所有文件"](/img/2017-04-28_223236.png)

### 撤销修改、删除和恢复文件
命令 |释义|备注
----|------|------
**撤销修改** ||
git checkout -- file	| 丢弃file文件在工作区的修改（工作区-暂存区-版本库，回到上一阶段的修改）a.工作区修改后没有add到暂存区：回到和版本库一样的状态；b.工作区修改后add到暂存区后又有修改：回到添加暂存区后的状态	|如果没有--，则为创建分支命令
**删除和恢复文件** ||
rm file	|删除工作区中的file文件	|a.想要删除版本库中的file文件：直接commit掉；b.想要从版本库中删除file文件：git checkout -- file
git checkout -- file	| 丢弃file文件在工作区的修改（工作区-暂存区-版本库，回到上一阶段的修改）a.工作区修改后没有add到暂存区：回到和版本库一样的状态；b.工作区修改后add到暂存区后又有修改：回到添加暂存区后的状态	|如果没有--，则为创建分支命令

#### 撤销修改
现在在readme.txt文件里面增加一行内容为55555555，通过命令查看如下：
!["修改555"](/img/2017-04-28_223816.png)

在未提交之前，我发现添加55555555内容有误，得马上恢复以前的版本，现在我可以有如下几种方法可以做修改：

1. 如果知道要删掉哪些内容，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit。

2. 按以前的方法直接恢复到上一个版本。使用 `git reset  --hard HEAD^`

但是现在我不想使用以上两种方法，想直接使用撤销命令该如何操作呢？首先在做撤销之前，我们可以先用 git status 查看下当前的状态，如下：
!["git status"](/img/2017-04-28_224044.png)

可以发现，Git会告诉你，`git checkout  -- file` 可以将工作区做的修改全部撤销，如下:
!["git checkout"](/img/2017-04-28_224304.png)

**注意：** `git checkout -- readme.txt` 中的 `--` 很重要.如果没有 `--` ，则命令变成创建分支了。

结果显示，内容555已结没有了。将工作区做的修改全部撤销有两种情况：
1. 修改后还没有放到暂存区：撤销修改则回到和版本库一模一样的状态；
2. 已经放入暂存区，接着又作了修改：撤销修改则回到添加暂存区后的状态。

对于第2种情况，继续做demo，假如现在对readme.txt添加一行内容为66666666，git add 增加到暂存区，如下：
!["add 666"](/img/2017-04-28_225212.png)

接着添加内容77777777，通过撤销命令让其回到暂存区后的状态。如下：
!["撤销777"](/img/2017-04-28_225241.png)

#### 删除和恢复文件
 假如现在版本库testgit目录添加一个文件a.txt，然后提交。如下：
 !["添加a.txt"](/img/2017-04-28_230315.png)

一般情况下，删除文件有两种方法：
1. 直接在文件目录中删除文件text.txt
2. 使用命令`rm a.txt`

如下：
!["删除a.txt、test.txt"](/img/2017-04-28_230736.png)

当前目录是这样的:
!["当前目录"](/img/2017-04-28_230825.png)

如果想彻底从版本库中删掉了此文件的话，可以再执行commit命令提交掉。没有commit之前，想在版本库中恢复此文件如何操作呢？如下：
!["提交a.txt、test.txt"](/img/2017-04-28_231517.png)

再来看testgit目录，添加了2个文件，如下：
!["当前目录"](/img/2017-04-28_231617.png)

### 创建、合并分支
#### 理解HEAD和master指针
你已经知道，在版本回退里，每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。严格来说，HEAD并不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

**结论：HEAD指向当前分支，master指向提交**

#### 理解分支管理策略


**master主分支：用来发布新版本，应该是非常稳定的。一般情况下不允许在上面干活。**
**一般情况下在新建的dev分支上干活，干完后，要发布，或者说dev分支代码稳定后可以合并到主分支master上来。**

命令 | 释义|备注
----|------|---
**创建、合并分支** ||
git branch	|查看分支|列出所有分支，当前分支前有星号
git branch xxx	|创建分支xxx|
git checkout xxx	|切换到分支xxx|
git checkout -b xxx	|创建 + 切换分支xxx|相当于`git branch xxx`和`git checkout xxx`
git merge xxx	|在主分支上合并xxx分支|"Fast-forward“快进模式”：直接把master指向xxx的当前提交；删除分支后，丢掉分支信息CONFLICT：产生冲突；删除分支后，保留分支信息"
git branch -d xxx	|删除分支xxx|
**解决冲突** ||
git log --graph --pretty=oneline --abbrev-commit	|带参数的git log，查看分支合并图|删除分支后，保留分支信息
**“Fast forward”模式 no-ff** ||
git merge --no-ff -m "merge with no-ff" xxx	|合并分支xxx，--no-ff：禁用Fast-forward“快进模式”|删除分支后，保留分支信息

#### 创建、合并分支

首先，我们来创建并切换到dev分支上，然后查看当前分支，如下：
!["创建并切换到dev分支"](/img/2017-04-29_110228.png)

`git checkout -b xxx`表示创建 + 切换分支，相当于`git branch xxx`和`git checkout xxx`。

`git branch`表示查看分支，列出所有分支，当前分支前有星号。

首先我们来查看下readme.txt内容，接着添加内容77777777，再次查看内容并提交，如下：
!["dev分支增加777"](/img/2017-04-29_111013.png)

dev分支工作已完成，现在切换到主分支master上，继续查看readme.txt内容，如下：
!["切换到主分支"](/img/2017-04-29_111235.png)

我们发现内容777不见了，因为已经由dev分支切换到主分支了，主分支并没有增加777内容。现在我们把dev分支上的内容合并到分支master上，在master分支上，使用`git merge dev`，继续查看内容。如下：
!["合并分支"](/img/2017-04-29_111547.png)

我们发现多了一条777，和dev分支最新的提交完全一样。

**注意！** merge后显示的Fast-forward信息，表示这次合并是“快进模式”，即，直接把master指向dev的当前提交，合并速度非常快。

合并完成后，可以删除dev分支，如下：
!["删除分支"](/img/2017-04-29_112129.png)

查看分支，发现只剩下主分支master了。

#### 解决冲突
那么如何解决冲突呢？我们还是一步一步来，先新建一个新分支fenzhi1，在readme.txt添加一行内容8888888，然后提交，如下：
!["fenzhi1分支添加888"](/img/2017-04-29_112708.png)

接着切换到master分支上，在最后一行添加内容99999999，如下：
!["主分支添加999"](/img/2017-04-29_112957.png)

现在，在master分支上合并fenzhi1，如下：
!["主分支上合并fenzhi1"](/img/2017-04-29_113150.png)

发现发生了冲突CONFLICT，git bush中显示分支的地方也变成了(master|MERGING)。查看状态和readme.txt内容，如下：
!["查看状态和内容"](/img/2017-04-29_113734.png)
!["查看状态和内容"](/img/2017-04-29_114045.png)

Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容。
- `<<<HEAD` ：主分支修改的内容
- `>>>>>fenzhi1` ：fenzhi1上修改的内容

修改readme.txt内容后，保存并提交，如下：
!["修改readme.txt内容"](/img/2017-04-29_114214.png)
!["修改readme.txt内容"](/img/2017-04-29_115156.png)

发现显示分支的地方变回了(master)。如果想要查看分支合并的情况，需要使用命令 `git log`命令，如下：
!["git log"](/img/2017-04-29_115518.png)

`git log`展示的信息量太大，一片文字看不过来，使用`git log --graph --pretty=oneline --abbrev-commit`命令可以显示分支合并图，如下：
!["分支合并图"](/img/2017-04-29_120112.png)

#### "Fast forward"模式 no-ff
通常合并分支时，git一般使用"Fast forward"模式，在这种模式下，删除分支后，会丢掉分支信息。

现在我们来使用带参数 –no-ff来禁用"Fast forward"模式。来做demo演示下：

1. 创建一个dev分支
2. 修改readme.txt内容，增加aaa
3. 添加到暂存区
4. 切换回主分支(master)
5. 合并dev分支，使用命令 `git merge -–no-ff  -m “注释” dev`
6. 删除dev分支
7. 查看分支
8. 查看历史记录

如下：
!["no-ff"](/img/2017-04-29_142402.png)

### bug分支
命令 | b释义
----|------
git stash	|隐藏当前分支的工作现场
git stash list	|查看stash隐藏的内容
git stash apply	|恢复stash隐藏内容
git stash drop	|删除stash内容
git stash pop	|恢复并删除stash隐藏内容

在开发中，会经常碰到bug问题，那么有了bug就需要修复，在Git中，分支是很强大的，每个bug都可以通过一个临时分支来修复，修复完成后，合并分支，然后将临时的分支删除掉。

来做demo演示：新建dev分支，在readme.txt中增加bbb。此时接到一个404 bug，我们可以创建一个404分支来修复它，但是，当前的dev分支上的工作还没有提交。如下：
!["遇到404 bug"](/img/2017-04-29_144313.png)

并不是我不想提交，而是工作进行到一半时候，我们还无法提交，比如我这个分支bug要2天完成，但是我issue-404 bug需要5个小时内完成。怎么办呢？还好，Git还提供了一个stash功能，可以把当前工作现场 ”隐藏起来”，等以后恢复现场后继续工作。如下：
!["stash隐藏工作现场"](/img/2017-04-29_144452.png)

查看状态显示，`nothing to commit, working directory clean`，说明工作现场已被隐藏。现在可以通过创建issue-404分支来修复bug了。

首先要确定在哪个分支上修复bug。假设我现在要在主分支master上修复，那么要切换到主分支master，然后创建一个临时分支issue-404，如下：
!["临时分支issue-404"](/img/2017-04-29_145356.png)

修复404bug：将最后一行aaa改为404fixed，然后提交，如下：
!["修复404bug"](/img/2017-04-29_145603.png)

修复完成，切换到master分支上，并完成合并，最后删除issue-404分支。如下：
!["完成合并，删除issue-404分支"](/img/2017-04-29_145845.png)

现在，可以回到dev分支上干活了。
!["回到dev分支"](/img/2017-04-29_150024.png)

查看状态表明，现在的工作区是干净的。那么我们工作现场去哪里呢？我们可以使用命令 git stash list来查看下。如下：
!["git stash list"](/img/2017-04-29_150228.png)

工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，可以使用如下2个方法：
1. git stash apply恢复。恢复后，stash内容并不删除，你需要使用命令git stash drop来删除
2. 使用git stash pop。恢复的同时把stash内容也删除了

如下：
!["恢复工作区"](/img/2017-04-29_151622.png)

这样就恢复了之前的工作区，可以继续dev分支的工作了。

## Github远程仓库
命令 | b释义 | 备注
----|------|----
**创建SSH Key** ||
ssh-keygen -t rsa –C “youremail@example.com”	|创建SSH Key	|id_rsa是私钥，不能泄露出去;id_rsa.pub是公钥，可以放心地告诉任何人"
**Github中添加SSH Key** ||
**添加远程库** ||
**a.先创建本地git仓库，再创建github仓库，两个仓库同步** ||
git remote add origin https://github.com/xxx/xxx.git |添加github地址 |
git push -u origin master	 |第一次使用时执行该命令，将本地的master分支和远程的master分支关联起来，并把将其推送到远程"	|
git push origin master	|将本地master分支的最新修改推送到github	|
**b.先创建github仓库，再从github仓库** ||
git clone https://github.com/xxx/xxx	||


先注册github账号，由于你的本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要设置SSH Key。

### 创建SSH Key
查看是否已经有ssh密钥：
打开用户主目录"C:\Users\Administrator.hp-PC"，
看看有没有.ssh目录。
- 如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件。如果有，可以直接跳至下一小节
- 如果已经有ssh密钥，想要重新生成ssh密钥，需要清理原有ssh密钥：
```
$ mkdir key_backup
$ cp id_rsa* key_backup
$ rm id_rsa*
```
- 如果没有，打开命令行，输入命令`ssh-keygen  -t rsa –C “youremail@example.com”`。此处的邮箱地址，你可以输入自己的邮箱地址。在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。

 由于我本地此前运行过一次，所以本地有，如下所示：

![".ssh"](/img/2017-04-29_153448.png)

id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。由于之前使用Github客户端，因此还有github_rsa和github_rsa.pub两个文件。known_hosts文件如果没有暂时不管。

验证是否连接成功，连接成功显示`Hi baoyuzhang! You've successfully authenticated, but GitHub does not provide shell access.`。如下：
!["验证是否连接成功"](/img/2017-04-29_160356.png)

### Github中添加SSH Key
登录github，点击个人头像打开"settings"，再打开"SSH and GPG keys"页面，然后点击"New SSH Key"，填上任意title，在"Key"文本框里黏贴id_rsa.pub文件的内容，点击 Add Key，你就应该可以看到已经添加的key。如下：
!["Github中添加SSH Key"](/img/2017-04-29_155435.png)

### 添加远程库
#### 先创建本地git仓库，再创建github仓库，两个仓库同步
现在的情景是：我们已经在本地创建了一个Git仓库后，又想在github创建一个Git仓库，并且希望这两个仓库进行远程同步，这样github的仓库可以作为备份，又可以其他人通过该仓库来协作。

首先，登录github上，然后在右上角点击"+"找到"New repository"创建一个新的仓库。如下：
!["create a new repo"](/img/2017-04-29_161046.png)
!["create a new repo"](/img/2017-04-29_161331.png)

在Repository name填入testgit，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库：
!["new repo"](/img/2017-04-29_161433.png)

目前，在GitHub上的这个testgit仓库还是空的。现在把已有的本地仓库testgit与之关联，然后，把本地仓库的内容推送到GitHub仓库。
!["推送到GitHub仓库"](/img/2017-04-29_162558.png)

把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。

由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。推送成功后，可以立刻在github页面中看到远程库的内容已经和本地一模一样了：
!["一模一样"](/img/2017-04-29_163139.png)

从现在起，只要本地作了提交，通过命令`git push origin master`就可以把本地master分支的最新修改推送到github上了，现在你就拥有了真正的分布式版本库了。

#### 先创建github仓库，再从github仓库克隆
上面我们了解了先有本地库，后有远程库时候，如何关联远程库。现在我们想，假如远程库有新的内容了，我想克隆到本地来 如何克隆呢？

首先，登录github，创建一个新的仓库，名字叫testgit2.如下：
!["create a new repo"](/img/2017-04-29_161046.png)
!["create a new repo"](/img/2017-04-29_163601.png)
!["create a new repo"](/img/2017-04-29_163651.png)

现在，远程库已经准备好了，下一步是使用命令git clone克隆一个本地库了。如下：
!["克隆一个本地库"](/img/2017-04-29_164025.png)
在本地目录就生成了testgit2目录，如下：
!["克隆一个本地库"](/img/2017-04-29_164053.png)

## Git常用指令
命令 | b释义 | 备注
----|------|----
**1.创建版本库repository** ||
**打开所在目录** ||
cd folder | 打开文件夹|
mkdir folder | 新建文件夹|
pwd | 显示当前目录|
**初始化：将当前目录变为git仓库** ||
git init	 | 当前目录→git可管理仓库|
**添加文件到版本库** ||
git add file	| 将file文件添加到暂存区|
git commit -m "提交说明"	| 将暂存区中所有文件提交到仓库|
git status	| 查看当前目录中是否有文件未提交|
**2.修改和版本回退** ||
**修改文件内容** ||
git diff file	| 查看file文件修改内容|
**查看历史记录** ||
git log | 查看历史记录|
git log --pretty=oneline  |查看历史记录（简洁版）|
**版本回退** ||
git reset --hard HEAD^	 | 退回到上个版本|
git reset --hard HEAD^^	 | 退回到上上个版本|
git reset --hard HEAD~100	 | 退回到前100个版本|
**恢复最新版本** ||
git reflog	 | 获取全部版本号|
git reset --hard 版本号	 | 退回到版本号的版本|
cat file	 | 查看文件内容|
**3.撤销修改、删除文件、恢复文件** ||
**撤销修改** ||
git checkout -- file	| 丢弃file文件在工作区的修改（工作区-暂存区-版本库，回到上一阶段的修改）a.工作区修改后没有add到暂存区：回到和版本库一样的状态；b.工作区修改后add到暂存区后又有修改：回到添加暂存区后的状态	|如果没有--，则为创建分支命令
**删除和恢复文件** ||
rm file	|删除工作区中的file文件	|a.想要删除版本库中的file文件：直接commit掉；b.想要从版本库中删除file文件：git checkout -- file
git checkout -- file	| 丢弃file文件在工作区的修改（工作区-暂存区-版本库，回到上一阶段的修改）a.工作区修改后没有add到暂存区：回到和版本库一样的状态；b.工作区修改后add到暂存区后又有修改：回到添加暂存区后的状态	|如果没有--，则为创建分支命令
**4.创建、合并分支** ||
**创建、合并分支** ||
git branch	|查看分支|列出所有分支，当前分支前有星号
git branch xxx	|创建分支xxx|
git checkout xxx	|切换到分支xxx|
git checkout -b xxx	|创建 + 切换分支xxx|相当于`git branch xxx`和`git checkout xxx`
git merge xxx	|在主分支上合并xxx分支|"Fast-forward“快进模式”：直接把master指向xxx的当前提交；删除分支后，丢掉分支信息CONFLICT：产生冲突；删除分支后，保留分支信息"
git branch -d xxx	|删除分支xxx|
**解决冲突** ||
git log --graph --pretty=oneline --abbrev-commit	|带参数的git log，查看分支合并图|删除分支后，保留分支信息
**“Fast forward”模式 no-ff** ||
git merge --no-ff -m "merge with no-ff" xxx	|合并分支xxx，--no-ff：禁用Fast-forward“快进模式”|删除分支后，保留分支信息
**5.bug分支** ||
git stash	|隐藏当前分支的工作现场|
git stash list	|查看stash隐藏的内容|
git stash apply	|恢复stash隐藏内容|
git stash drop	|删除stash内容|
git stash pop	|恢复并删除stash隐藏内容|
**6.Github远程仓库** ||
**创建SSH Key** ||
ssh-keygen -t rsa –C “youremail@example.com”	|创建SSH Key	|id_rsa是私钥，不能泄露出去;id_rsa.pub是公钥，可以放心地告诉任何人"
**Github中添加SSH Key** ||
**添加远程库** ||
**a.先创建本地git仓库，再创建github仓库，两个仓库同步** ||
git remote add origin https://github.com/xxx/xxx.git |添加github地址 |
git push -u origin master	 |第一次使用时执行该命令，将本地的master分支和远程的master分支关联起来，并把将其推送到远程"	|
git push origin master	|将本地master分支的最新修改推送到github	|
**b.先创建github仓库，再从github仓库** ||
git clone https://github.com/xxx/xxx	||
