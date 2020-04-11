
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

### 重新应用缓存的stash https://www.cnblogs.com/tocy/p/git-stash-reference.html
```
git stash 会把所有未提交的修改（包括暂存的和非暂存的）都保存起来，用于后续恢复当前工作目录。比如下面的中间状态，通过git stash命令推送一个新的储藏，当前的工作目录就干净了。
git stash apply 将缓存堆栈中的stash多次应用到工作目录中，但并不删除stash拷贝
git stash pop 缓存堆栈中的第一个stash删除，并将对应修改应用到当前的工作目录下
git stash list 查看现有stash
git stash drop 移除stash
git stash clear 删除所有缓存的stash。
git stash show 查看指定stash的diff
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

#### 修改commit描述
```
git commit --amend
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

**常用**
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

指定cimmit id 提交到本分支
```
git cherry-pick 某个commit id   // 把某个commit id的提交合并到当前分支.
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

### mac终端下自动提示 自动补全
```
1. curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash
2. vi ~/.bash_profile
3. 追加
if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi
function git_branch {
  branch="`git branch 2>/dev/null | grep "^\*" | sed -e "s/^\*\ //"`"
  if [ "${branch}" != "" ];then
      if [ "${branch}" = "(no branch)" ];then
          branch="(`git rev-parse --short HEAD`...)"
      fi
      echo " ($branch)"
  fi
}
export PS1='\u@\h \[\033[01;36m\]\W\[\033[01;32m\]$(git_branch)\[\033[00m\] \$ '
4. source ~/.bash_profile
```

### 配置
#### 查看
git config user.name
git config user.email

#### 修改
git config --global user.name  “用户名”
git config --global user.email   “邮箱”


### 版本号规则
特性分支
feature

feature_YYYYMMDD_功能名

发布分支
release

### 拉去指定commit
git cherry-pick commit-id  (github 上的短号)
