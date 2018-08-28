
### 撤消操作
git commit --amend

取消已经暂存的文件
git reset HEAD <file>
git reset HEAD file.md

取消对文件的修改
git checkout -- <file>
git checkout -- file.md



查看当前的远程库
git remote

 -v 选项 为 --verbose 的简写，显示对应的克隆地址
git remote -v

从远程仓库抓取数据
git fetch [remote-name]

推送数据到远程仓库
git push [remote-name] [branch-name]
git push origin master

git remote rename

git remote rm

标签