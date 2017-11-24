clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/樱花.JPG
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大的樱花.jpg
coverCaption: "工大的樱花"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大的樱花.jpg
comments: false
title: Git&&Github学习资料
date: 2015-07-17 18:38:44
tags: [Github]
categories: [工具]

---
如果你是一名程序员，然后你不会使用Github。好吧，一看就是一个不专业的程序员，Github相当于码农标配。其实，找工作的时候，Github 就是一份简历。实际的项目，详细的改版历史中都可以看到心思和汗水，这个要比简历上空洞的写“我精通xxx”要有说服力。
<!-- more -->

 ***
 
# 学习网站
  
  因为这些学习资料都是我看过的干货，所以整理到这里，方便以后遗忘了一些东西，可以查找，具体的细节操作就不再赘述了。
  
 
## [Pro git 电子书](http://git-scm.com/book)（重点推荐）
  
## [廖雪峰Github的学习网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)(通俗易懂)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;廖雪峰Github的学习网站偏向在终端中写代码，没有图形化的工具，但是Git的原理呢，讲得还是非常不错的，非常通俗易懂。
 
## [慕课网-版本控制入门（视频）](http://www.imooc.com/view/390)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;慕课网的视频教程呢，是偏向Github客户端的使用，如果你是一个喜欢图形化操作的码农，那可以选择使用客户端。如果你是一个喜欢在终端里面敲代码的码农，那还是选择[廖雪峰Github的学习网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)吧，当然，理论的知识，讲得都很不错的。

## [慕课网-版本控制入门（电子书）](http://book.haoduoshipin.com/gitbeijing/)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这本电子书，就是[慕课网-版本控制入门（视频）](http://www.imooc.com/view/390)的电子书，方便查阅。

## [Code School的GIT入门课程](https://try.github.io/levels/1/challenges/1)


## [Github官方推出的教学视频](http://www.stuq.org/course/detail/969)

## [常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

## [常用 Git alias](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git)


# 设置用户名和密码
``` markdown
git config --local/global/system <用户名>
git config --local/global/system <邮箱>
```
# 查看用户名和密码
``` markdown
git config user.name
git config user.email
```

# 查看npm，tnpm等各类源

``` markdown
//查看源
tnpm config get registry
//临时设置源
tnpm --registry 源的网址 i -S 包名
```

# 生成SSH
``` markdown
ssh-keygen -t -C "your email"
```

# .gitconfig
``` markdown
//配置文件
[alias]
        br = branch
        st = status
        co = checkout
        ci = commit
        lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

```

# Git 命令详解

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/git-status.png "git status" %}

| 命令       | 说明           | 
| ------------- |:-------------:| 
| git help     | 查看帮助文档 | 
| git init     | 初始化仓库 | 
| rm -rf .git     | 删除.git | 
| git status     | 查看当前仓库信息     |  
| git add <文件名1> <文件名2>|添加文件内容到暂存区(同时文件被跟踪)|   
| git add .|添加当前目录下的所有文件|   
| git rm  -&nbsp;-cached <文件名>  | 从暂存区删除文件|  
| git rm   <文件名>  | 从暂存区与工作目录中同时删除 |  
| git rm  $(git ls-files -&nbsp;-deleted)| 删除所有被跟踪，但是在工作目录被删除的文件| 
| git commit  -m '注释内容'   | 把暂存区的所有内容提交到当前分支   |  
| git commit -a -m '注释内容'     | 直接提交,从工作目录到提交区     | 
| git diff   <文件名>  | 显示该文件在工作目录与暂存区的差异 | 
| git diff   HEAD -&nbsp;- <文件名>  | 查看该文件工作区和版本库里面最新版本的区别 | 
| git diff  -&nbsp;-cached <默认HEAD>| 显示暂存区与某次提交的差异 | 
| git diff  aa4988 aa4989 | 显示aa4988与aa4989之间的差异 | 
| git checkout -&nbsp;- <文件名>|把文件在工作区的修改全部撤销,这个文件回到最近一次git commit或git add时的状态| 
| git checkout HEAD-- <文件名>| 将文件从上次提交复制到工作目录     | 
| git log     | 查看提交历史记录      | 
| git reflog     |查看命令历史，commitid| 
| git reset HEAD  <文件名>     | 把文件在暂存区的修改撤销掉（unstage），重新放回工作区| 
| git reset -&nbsp;-hard  HEAD^ | git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区,把当前版本回退到上一个版本  | 
| git reset -&nbsp;-hard  <提交ID>  | 回到某个commitid的版本  |

# 分支相关操作

| 命令       | 说明           | 
| ------------- |:-------------:| 
| git branch  <分支名>   | 创建一个分支 | 
| git branch -v   | 显示当前有多少分支及每个分支的最后一次提交 | 
| git checkout  <分支名> | 切换到该分支 | 
| git checkout -b <分支名> | 先创建该分支，切换到该分支 | 
| git checkout -b dev origin/dev| 创建远程origin的dev分支到本地 | 
| git fetch origin,git checkout 分支名| 创建远程origin的dev分支到本地 |
| git checkout  -| 回到上一个分支 | 
| git reset  -&nbsp;-mixed(默认) <提交ID> | 将当前分支回退到历史某个版本,同步提交区内容到暂存区 | 
| git reset  -&nbsp;-hard <提交ID> | 将当前分支回退到历史某个版本,同步提交区内容到暂存区和工作目录 | 
| git reset  -&nbsp;-soft  <提交ID> | 将当前分支回退到历史某个版本,暂存区和工作目录内容不会变化 | 
| git stash save "注释" | 保存目前的工作目录和暂存区状态，并返回到干净的工作空间 | 
| git stash list  | 查看stash栈中都有哪些保存的记录 | 
| git stash apply  | 还原保存的内容到工作目录 | 
| git stash drop  | 删除在stash栈中的记录| 
| git stash pop  | stash apply+stash drop| 
| git merge  |  合并分支| 
| git merge  next -&nbsp;-no-ff|  不要使用fast-forward方式来合并| 
| git rebase  |  修改提交历史基线，变基| 
| git rebase  -&nbsp;-onto master  <提交ID>| <提交ID>以后的提交对象在master上进行重演 | 
| git branch -d 分支名| 删除本地的一个分支 | 

# 远程操作
| 命令       | 说明           | 
| ------------- |:-------------:| 
| git remote -v  | 查看远程库的信息 | 
| git remote add origin 仓库地址 | 关联本地仓库到远程仓库 | 
| git push  origin 分支名   | 提交本地分支名到服务器 | 
| git fetch  origin   | 从远程抓取本地没有的数据，并且更新本地数据库，移动 origin/master 指针指向新的、更新后的位置。 | 
| git pull    | git fetch +git merge | 
| git clone git@github.com:用户名/仓库名.git  | 克隆一个远程仓库作为本地仓库 | 


# 删除本地及远程无用的分支
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当我们创建特性分支提MR后，远程还会存在我们之前push上去的特性分支。

| 命令       | 说明           | 
| ------------- |:-------------:| 
| git fetch - - prune origin |先刷新本地仓库与远程仓库，保持同步 | 
| git branch -a  | 查看远程有哪些分支 | 
| git push origin - -delete <分支名>  |删除已经提交在远程的一个分支 | 
| git branch -d <分支名>   | 删除本地的特性分支 | 


# tag
| 命令       | 说明           | 
| ------------- |:-------------:| 
| git fetch - - prune origin |先刷新本地仓库与远程仓库，保持同步 | 
| git tag |查看当前分支下的tag,如果你执行这条命令没反应，先执行上面这条命令 | 
| git tag -d tag名称 |删除本地的tag | 
| git push origin v1.2| 将tag名称为v1.2的tag 推送到远程 | 
| git tag V0.1 commitid| 对某个提交设置一个不变的别名 | 
| git checkout -b branch_name tag_name| 根据tag_name创建分支到本地 | 
| git push origin --delete tag tag_name | 删除远程的tag | 





# Tips

####  查看SSH。
``` markdown
在用户所在的根目录下输入如下命令，查看.ssh目录是否存在：
ls -ah
cd .ssh
//显示.ssh目录下的所有文件
github_rsa     github_rsa.pub id_rsa         id_rsa.pub     known_hosts
//查看SSH
cat id_rsa.pub
```
//_login.sass把这个文件从提交区撤销回来
git checkout 98f936f575 -- app/sass/_login.sass

####  使用`git lg`来替代`git log`了。

``` markdown
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

#### 创建一个readme文件：
``` markdown
touch readme.md
```
#### 查看`.git`文件：
``` markdown
cat .git/refs/heads/master
```
#### 查看当前HEAD指针信息
``` markdown
git cat-file -p HEAD
```
#### 强行删除一个分支
``` markdown
git branch -D 分支名
```

#### 查看隐藏的git目录
如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见。

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E7%82%B9git%E6%96%87%E4%BB%B6.png "git文件目录" %}

#### 关于分支同步
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;master分支是主分支，因此要时刻与远程同步；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

#### 每次修改注意事项
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每次工作区的修改，如果不add到暂存区，那就不会加入到commit中。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;第一次修改 -> git add -> 第二次修改 -> git add -> git commit



``` markdown
//第1步：先从feature分支上切换到主分支：
web git:(showGraphicInfoOnPC) git checkout daily/2.19.0
//第2步：更新主分支：
git pull origin daily/2.19.0
//第3步：再切换回feature分支
git checkout showGraphicInfoOnPC
//第4步：在特性分支上进行rebase操作
git rebase daily/2.19.0,会生成一个新的commitID
//第5步：解决相关冲突文件
和发生冲突的项目人员交流,讨论如何解决这个冲突并修改
//第6步：将冲突文件提交到暂存区
git add .
//第7步：fix conflicts and then run "git rebase --continue"
git rebase --continue
//第8步：
web git:(showGraphicInfoOnPC) git push origin showGraphicInfoOnPC --force
```

#### detached head
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当一个HEAD变为detached head的时候，不要进行写操作，只能用来读取内容
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/detachedhead.png "detached head" %}
####  Merge冲突
``` markdown
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
michaelovedeMBP:git michaeljunlove$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   readme.txt
no changes added to commit (use "git add" and/or "git commit -a")
```

{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/merge.png "修复合并冲突后的git status" %}

####  Merge fast-forword
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;快进模式合并，也就是直接把master指向next的当前提交，所以合并速度非常快。通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。
```
git merge --no-ff -m "merge with no-ff" feature分支
```
{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/fast-forword.png "fast-forword" %}



####  reset&&checkout


{% image  center clear http://7xid80.com1.z0.glb.clouddn.com/reset&&checkout.png
 "reset&&checkout" %}
 
<h1 style="color:red">记住git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区</h1>
 
## 场景：在本地回退到某个版本用git reset --hard 版本号

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在Git中，用HEAD表示当前版本，也就是最新的提交.上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写成HEAD~100.Git的版本回退速度非常快，因为Git在内部有个指向当前版本的HEAD指针，当你回退版本的时候，Git仅仅是把HEAD从当前分支指向要回退的分支上即可。--hard 的作用是：
``` markdown
//回退到上一个版本
git reset --hard HEAD^
//会退到某个版本号
git reset --hard 986b9e3
```
## 场景：工作区文件readme.txt自修改后已经被放到暂存区，但是你想把这个文件放入暂存区的操作撤销掉

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。
``` markdown
//这时候，暂存区的内容会回到工作区，是属于修改后的.
//要想恢复到工作区未修改的状态，执行git checkout -- 文件名
git reset HEAD 文件名
```

<h1 style="color:red">记住git checkout让这个文件回到最近一次git commit或git add时的状态</h1>

## 场景：工作区文件readme.txt自修改后还没有被放到暂存区，要想恢复readme.txt到工作区之前没有修改过的原貌
``` markdown
git checkout -- readme.txt
```
## 场景：工作区文件readme.txt自修改后已经被放到暂存区后又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
``` markdown
git checkout -- readme.txt
```

## 场景：工作区文件readme.txt被你不小心删掉了，但是之前有提交到暂存区或提交区，以下命令还原该文件。
``` markdown
git checkout -- readme.txt
```

<h1 style="color:red">git stash与git stash pop用来保存和还原工作环境<h1>

## 场景：当你正在当前分支上开发，突然接到要修复某个BUG的需求，但是目前的工作还没有完成，这时就需要保存工作
``` markdown
//先在当前分支上执行git stash保存当前的工作环境
git stash
//去创建一个新的分支，来修复BUG并提交
//BUG修复后，回到之前在修改的分支
//执行git stash pop还原之前保存的工作环境
git stash pop
```

# git rebase (重要!!!)

## 1.[参考资料1](http://gitbook.liuhui998.com/4_2.html)


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;什么样的情况需要进行rebase操作？

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git rebase命令用来修剪提交历史基线，俗称“变基”,。如下图所示：有2个分支，分别是master分支和feature分支，当我们在feature分支上使用命令`git rebase master`时，首先，git会找到三个提交节点，分别是2个分支节点`c4fe238`，`0420486`及他们共同的祖先节点`c4006ec`，然后git会找到分支节点`0420486`与共同节点`c4006ec`之间的提交记录，让这段提交记录在master分支上进行重演。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;千万不要在master分支上使用rebase
{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/git-rebase.png "git-rebase" %}
``` markdown
git rebase --onto
```
## 回退git rebase操作
``` markdown
git reflog找到还未进行rebase之前的操作的ID号
git reset  --hard <提交ID>
```
# clone远程的一个分支到本地
``` markdown
//先查看远程服务器上有哪些分支
git fetch origin 
//然后拉取需要的远程分支到本地
git co -b v2.2 origin/v2.2

git reset --hard 1a1814bd
```

# 出了BUG,是谁干的？
``` markdown
git blame filename
```

