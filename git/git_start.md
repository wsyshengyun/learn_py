## GIT

 

 

### 安装git

直接下载再安装，成功后在开始菜单可以找到Git Bash命令行窗口。

 

配置本机的git

$ git config -- global user.name “Your Name” 

$ git config – global user.email [email@example.com](mailto:email@example.com) 

 

查看本机的配置

$ git config –global –list 

​    查看某一项的配置

$ git config –global user.name 

$ git config –global user.email

 

分布式版本控制系统

每个机器自报家门：名字和email

 

### 工作区 working Directory 

就是你电脑里能看到的目录

 

### 版本库 Repository 也叫仓库  

创建一个空目录 -> 进入 目录  -- > git init 

目录里面多了一个.git 目录，默认是隐藏的， 用命令ls -ah 可以看见  

 

添加一个文件 ： readme.txt 

第一步 命令git add readme.txt 

第二步 git commit 把文件提交到仓库 

​    git commit –m “wrote a readme file” 

 

版本库就是工作区的一个隐藏目录.git

**版本库的东西**

最重要的就是【暂存区】了-stage（或者叫index）

Git为我们新建的一个【分支】-master，以及指向分支的一个指针叫HEAD

 

git add ------ 把文件提交到暂存区

git commit --- 把文件提交到当前分支，只负责提交暂存区（index）

可以多次暂存一次提交分支 

多次提交就是多次add，然后保存一个快照，即commit；

commit: 对应快照，对应一个新的版本；

恢复：从最近的一次commit恢复

版本号：1094adb7b9b3807259d8cb349e7df1d4d6477073



### 问题

commit有价值的提交：

如何把暂存区的某个文件的改动撤消退到工作区？

##  名词

### 分支

合并分支时文件内容也会相应的融合。

### git stash

作用就是将目前还不想提交的蛤是已经修改的内容进行保存至堆栈中，后续可以在某个分支上恢复出堆栈的内容。

stash中的内容不仅可以恢复到原先开发的分支，还可以恢复到其他任意的分支。



git stash的作用范围包括工作区和暂存区中的内容，也就是没有提交的内容都会保存 堆栈。



git add 只是把文件添加到git版本控制里，并不等于就被stash起来了，git add和git  stash并没有必然的关系，但是执行git stash的前提必须在git版本控制中才行。



 

 

 

###  远程仓库

权限控制

​	比如所有人都不准直接 git push origin master ，只有 admin 能 merge develop 或 master 分支；

和远端相关的Git 指令，我认为最基础的就是 **fetch** 和 **push** 



### 变基

merge的结果是生成一个新的快照并提交。

变基就是把提交到某一分支上的所有修改都移到另一个分支上。



## 命令

#### 配置

git config –global user.name “”

git config –global user.email “”

 

#### 添加文件或修改

git add 文件名

git add . 

​    git add –a 

git commit –m “” 

​    git commit –am “” 直接提交；

 

#### 标签

git tag –a  tagname –m “”  附注标签

git tag 标签名  创建轻量标签

 

git tag  查看标签

git show tagname 查看标签 

git tag –a tagname 9fceb02  #后期打标签

​       git tag  -a tagname 9fcebo2 # 

git push origin - - tags 把不在远仓的标签推上去 

git push origin v1.5 显示推 

 

git tag -d v1.4 删除标签 

​    git push <remote> :refs/tags/<tagname> 删除远仓标签

​    git push <remote> - - delete <tagname> 同上

 

 

#### 分支

​    git branch 查看分支

​    git checkout name 切换分支

​       git checkout – 切换上一次的分支

​    git checkout –b name 新建分支并切换

​    git switch –c name 同上

​    git switch name 切换分支

​    

​    git merge name 快速合并；合并分支（主分支 git merge 子分支name） 

​    git merge –no-ff name  -m“”

 

​    git checkout –d name 删除分支

​       git branch –d name 

 

#### 查看

git log  

git log -1 

git log --pretty=oneline

git log --graph --pretty=oneline --abbrev-commit

git reflog 

git log <分支名>  查看分支的提交

​      

 

git diff：是查看working tree与index的差别的。

git diff --cached：是查看index与repository的差别的。

git diff HEAD：是查看working tree和repository的差别的。其中：HEAD代表的是最近的一次commit的信息。

 

​     

#### 版本回退

git reset - - hard HEAD 

​    gir reset - - hard 版本号

git reset HEAD filename 暂存区的修改撤销掉（unstage），重新放回工作区

git reset --hard HEAD^

git reset --hard HEAD~1

git reset – 59cf9334cf957535cb328f22a1579b84db0911e5 

git checkout -- 文件名  （--左右要有空格）

git revert <commit-id >

这条命令会把指定的提交的所有修改回滚，并同时生成一个新的提交。

 

 

#### 远程仓库

1    git remote add [仓库的名字:origin]  git@ github.com:michaeliao/learngit.git

2    git push –u origin master 

3    git clone git@github.com:hirocastest/first-pr.git

 

#### **git  stash**

git stash   #执行存储

​	**git stash save** "save message"    并添加备注  



git stash list   # 查看stash了哪些存储  

git stash show ；查看堆栈中最新保存的stash与当前目录的差异，默认show第一个存储，如果要显示其他存贮，后面加stash@{$num}，

git stash show -p ; 显示第一个存储的改动  

git stash apply  @{0}; 应用某个存储，但不会把存储从列表中删除。

git stash pop 参数同上; 应用并删除

git stash drop stash@{$num}; 丢弃存储，从列表中删除。

git stash clear; 删除所有缓存的stash  



​	

#### 变基

在一个分支上合并多个commit为一个完整commit

git rebase -i  [startpoint] [endpoint]  ; endpoint 默认值是当前HEAD；合并startpoint到	endpoint,且该区间是前开后闭即(startpoint, endpoint] 







## 其它

在cmd命令行上更新windows下的git（git的版本>2.16.1）

​    git update-git-for-windows

 

distributed 分布式

#### 忽略

【大家一定要养成在项目开始就创建.gitignore文件的习惯，否则一旦push，处理起来会非常麻烦】

在主目录下建立".gitignore"文件，此文件有如下规则：

 

忽略文件中的空行或以井号（#）开始的行将会被忽略。

可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。

如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。

如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。

如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

#### 别名

git config –global alias.st status 

git config –global alias.co checkout 

git config –global alias.ci cimmit 

git comfig –global alias.br branch 

git config –global alias.unstage “reset HEAD”  # 可以把暂存区的内容撤消掉

git config –global alias.last ‘log -1’# 显示最后一次提交的信息

疯狂的lg 

git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

 

配置时加了global是对当前用户起作用，如果不加只对当前仓库起作用。

每个仓库的配置文件放在.git/config文件中





#### 使用git的一些原则

1. 永远记得 git st 和 git logl 来确认当前分支的状态
2. 宁愿临时制造一些无用的 commit 来保证代码不会丢失，也不要轻信自己的记忆力
3. 谨慎（最好能避免）使用 git stash ，极易造成代码丢失
4. 认真对待、编写每次的 commit message —— 它们能在关键时刻救你一命
5. 必要的时候可以创建一些临时的分支写实验性的代码，而不是依赖 git reset 撤销 commit —— 大多数人在 git reset 的时候容易犯错误



#### 查看所有分支日志

"git reflog"中会记录这个仓库中所有的分支的所有更新记录，包括已经撤销的更新。

![https://images2017.cnblogs.com/blog/63651/201709/63651-20170906213836397-1160093052.png](file:///C:/Users/w3986/AppData/Local/Temp/msohtmlclip1/02/clip_image004.png)

 

 

 



