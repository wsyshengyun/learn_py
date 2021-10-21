

### gitbash命令行显示不了中文？

使用命令：git config --global core.quotepath false

### 解决github打不开的办法

 https://blog.csdn.net/weixin_44411398/article/details/112510646



###  git进行rebase操作报错提示“hint: Waiting for your editor to close the file... ”

​	**解决办法：** 在git bash中使用以下命令修改默认编辑器为`vim`

```bash
git config --global core.editor 'vim'
```





##  其它问题（未解决）

为什么 commit 是git的核心？ 为什么有 commit 就不怕代码丢失？分支和 commit 是什么关系？有 git commit 为什么还有 git add ？git reset 危险在哪里 ？