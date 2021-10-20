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

 

### 分支

创建分支 git branch dev(分支名字)

切换分支 git checkout name(master or dev) 

​        另外一种方式： git switch name 

删除分支 git branch –d name 

合并分支 git merge name 

​        把分支dev合并到主分支上需要先切换到主分支上再合并，如下

​        git checkout master ;  git checkout –d dev 

 

创建并切换到新的分机

1， git checkout –b name 

2， git switch –c name 

 

一、     如果两个分支是完全相同时，即最后一次commit完全相同，才可以在不add commit新修改的情况下切换分支；

二、     切换分支后工作区的文件内容就会变为这个分支最后一次commit的内容。

 

**Fast****模式**

​    通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。

 

**禁用Fast****模式**

如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。禁用Fast forward模式 ，使用--no-ff参数，表示禁用Fast forward：

$ git merge --no-ff -m "merge with no-ff" dev

 

#### Bug分支

#### git stash

stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作

工作区是干净的，刚才的工作现场存到哪去了？用

git stash list

命令看看：

$ git stash list

stash@{0}: WIP on dev: f52c633 add merge

 

一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；

 

另一种方式是用git stash pop，恢复的同时把stash内容也删了：

 

 

你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令：

 

$ git stash apply stash@{0}

 

#### cherry-pick命令

复制一个特定的提交到当前分支：

$ git cherry-pick 4c805e2

​    cherry-pick *选出最佳项目；做出最佳选择*

#### feature分支

开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。

#### rebase 变基操作、、、

 

 

 

### 远程仓库

1、新建一个远程仓库为空

2、本地与远程仓库关联

3、从本地第一次推送 

​    -u 参数 

​    1， 把本地的内容推送到远程

2，把本地的master与远程的master关联

 

1、 --- 

2、 git remote add [仓库的名字:origin]  git@ github.com:michaeliao/learngit.git

3、 git push –u origin master 

 

git clone [git@github.com:hirocastest/first-pr.git](mailto:git@github.com:hirocastest/first-pr.git)

 

 

 

 

### 忽略

【大家一定要养成在项目开始就创建.gitignore文件的习惯，否则一旦push，处理起来会非常麻烦】

在主目录下建立".gitignore"文件，此文件有如下规则：

 

忽略文件中的空行或以井号（#）开始的行将会被忽略。

可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。

如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。

如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。

如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

### 命令

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

git reflog 

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

 

### 其它

在cmd命令行上更新windows下的git（git的版本>2.16.1）

​    git update-git-for-windows

 

distributed 分布式

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

#### git log

**git log --graph**

以图形化的方式显示提交历史的关系 

 

**git log -1**

则表示显示1行。

 

git log（reflog） master(分支名)

​    仅显示该分支的记录

 

$git log --graph --pretty=oneline --abbrev-commit

![img](file:///C:/Users/w3986/AppData/Local/Temp/msohtmlclip1/02/clip_image002.jpg)

##### 查看所有分支日志

"git reflog"中会记录这个仓库中所有的分支的所有更新记录，包括已经撤销的更新。

![https://images2017.cnblogs.com/blog/63651/201709/63651-20170906213836397-1160093052.png](file:///C:/Users/w3986/AppData/Local/Temp/msohtmlclip1/02/clip_image004.png)

 

 

 

### 解决

解决github打不开的办法 https://blog.csdn.net/weixin_44411398/article/details/112510646

 

 