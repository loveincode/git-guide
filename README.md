
### 撤消操作
git commit --amend

取消已经暂存的文件
git reset HEAD <file>
git reset HEAD file.md

取消对文件的修改
git checkout -- <file>
git checkout -- file.md

取消commit
git reset [id] 
完成Commit命令的撤销，但是不对代码修改进行撤销，可以直接通过git commit 重新提交对本地代码的修改


### 远程仓库
查看当前的远程库
git remote

 -v 选项 为 --verbose 的简写，显示对应的克隆地址
git remote -v

从远程仓库抓取数据
git fetch [remote-name]

推送数据到远程仓库

git push <远程主机名> <本地分支名>:<远程分支名>  git pull是 <远程主机名> <远程分支名>:<本地分支名>
git push origin master:master



git remote rename

git remote rm

标签

### 分支

新建分支
git checkout -b [branch-name]
=
git branch [branch-name] [远程分支名] 不加远程分支 默认从master拉一个分支
git checkout [branch-name]

合并分支

在checkout的分支进行git merge 将分支合并到当前分支
**git merge** [branch-name]

删除分支
git branch -d [branch-name]
git branch -D [branch-name] -D强制删除


git branch --merged 查看哪些分支已被并入当前分支
git branch --no-merged 查看尚未合并的工作



**git fetch** origin 来同步远程服务器上的数据到本地。
该命令首先找到 origin 是哪个服务器，从上面获取你尚未拥有的数据，更新你本地的数据库。

删除远程分支
git push origin :serverfix
git push origin --delete <BranchName>
