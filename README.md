
### 撤消操作
```
git commit --amend
```

#### 取消已经暂存的文件
```
git reset HEAD <file>
git reset HEAD file.md
```
#### 取消对文件的修改
```
git checkout -- <file>
git checkout -- file.md

git checkout . 放弃所有的文件修改
```

#### 删除新增
```
git clean -df  只删除所有untracked的文件，如果文件已经被tracked, 修改过的文件不会被回退。
```

#### 取消commit
```
git reset [id] 回到id时
完成Commit命令的撤销，但是不对代码修改进行撤销，可以直接通过git commit 重新提交对本地代码的修改

git reset --hard 只把tracked的文件revert到前一个版本，对于untracked的文件(比如编译的临时文件)都不会被删除。
```

### 远程仓库
```
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
```

### 分支 branch

新建分支
```
git checkout -b [branch-name]

git branch [branch-name] [远程分支名] 不加远程分支 默认从master拉一个分支
```
切换分支
```
git checkout [branch-name]
```

合并分支
```
在checkout的分支进行git merge 将分支合并到当前分支
**git merge** [branch-name]
```

删除分支
```
git branch -d [branch-name]
git branch -D [branch-name] -D强制删除
```

```
git branch --merged 查看哪些分支已被并入当前分支
git branch --no-merged 查看尚未合并的工作
```

```
**git fetch** origin 来同步远程服务器上的数据到本地。
该命令首先找到 origin 是哪个服务器，从上面获取你尚未拥有的数据，更新你本地的数据库。
```

删除远程分支
```
git push origin :serverfix
```

远程回退
```
查看需要回退的commitID
git reflog 
1
接着回退版本:
git reset --hard Obfafd
紧接着强制推送到远程分支：
git push -f
```

刷新远程分支
```
git remote update origin --prune，这里要注意下，如果你的remote branch不是在origin下，按你得把origin换成你的名字。
```

### 标签 tag
查看标签
```
打印所有标签
git tag
打印符合检索条件的标签
git tag -l 1.*.*
查看对应标签状态
git checkout 1.0.0
```
创建标签(本地)
```
创建轻量标签
git tag 1.0.0-light
创建带备注标签(推荐)
git tag -a 1.0.0 -m "这是备注信息"
针对特定commit版本SHA创建标签
git tag -a 1.0.0 0c3b62d -m "这是备注信息"
```
删除标签(本地)
```
git tag -d 1.0.0
将本地标签发布到远程仓库
发送所有
git push origin --tags
指定版本发送
git push origin 1.0.0
```
删除远程仓库对应标签
```
Git版本 > V1.7.0
git push origin --delete 1.0.0
旧版本Git
git push origin :refs/tags/1.0.0
```