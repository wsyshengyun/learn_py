

### gitbash命令行显示不了中文？

使用命令：git config --global core.quotepath false

### 解决github打不开的办法

 https://blog.csdn.net/weixin_44411398/article/details/112510646



###  git进行rebase操作报错提示“hint: Waiting for your editor to close the file... ”

​	**解决办法：** 在git bash中使用以下命令修改默认编辑器为`vim`

```bash
git config --global core.editor 'vim'
```



### 怎么把别名应用到所有的本地仓库？

### gitbash中怎么删除非空目录？

rm <目录名> -rf 

### [Git如何fork别人的仓库并作为贡献者提交代码](https://www.cnblogs.com/javaIOException/p/11867988.html)

例如 要fork一份google的MLperf/inference代码，下面介绍具体做法：
预备知识
git里的参考有几种表示，分别是上游仓库，远程仓库和本地仓库，逻辑关系如下
拉取代码的顺序：
别的大牛的代码(上游仓库)---------->你fork的代码(远程仓库)---------->你电脑的代码(本地仓库)
提交代码的顺序：
别的大牛的代码(上游仓库)<----------你fork的代码(远程仓库)<----------你电脑的代码(本地仓库)
每个仓库主分支是master，还可以有其它分支
上游仓库的表示为 upstream，远程仓库表示为origin







##  其它问题（未解决）

为什么 commit 是git的核心？ 为什么有 commit 就不怕代码丢失？分支和 commit 是什么关系？有 git commit 为什么还有 git add ？git reset 危险在哪里 ？



如何加速github的访问速度？

​	 [国内加速Github的几种方案 - 清潭白荡|晓瑞杂志 (qu.js.cn)](https://qu.js.cn/how-to-speed-github/)

关于github 网站 的界面了解？

​	有设置界面的说明：[Git系列之Github基础设置及使用详解 - 简书 (jianshu.com)](https://www.jianshu.com/p/f51062941573)



了解github网站的个人设置各个选项的作用？

了解token和keys的作用？

如果向一个仓库提交更改？



## 其它资源

switchhosts下载

[Releases · oldj/SwitchHosts (github.com)](https://github.com/oldj/SwitchHosts/releases)

​	安装和使用 [(27条消息) SwitchHosts安装使用_是谁笑我太疯癫的博客-CSDN博客_switchhosts](https://blog.csdn.net/weixin_43912774/article/details/110588353)





