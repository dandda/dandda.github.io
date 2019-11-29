git 常用命令

git branch -d '分支名' （删除本地分支）

git push --delete origin '分支名' (删除远程分支)

git checkout -b new_branch origin/new_branch (拉取本地上不存在的远程分支)

git checkout --filename (撤销单个文件的修改)

git checkout . (撤销所有的修改)

git status (查看有没有要提交的更改)

> git commit --amend(修改最新的，还未 push 上去的提交信息)
>
> git rebase -i HEAD~X (修改你任何你想改的提交信息)
>
> 暂时是这样理解。我现在还是不清楚这两个命令，以后再来弄懂。

---

git remote rm origin

git remote add origin [url]

这两个命令是修改远程仓库地址（首次要 git 的账号和密码）

---

git diff (查看作了哪些操作)

### 学习 git:

[git 教程-廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600)

[通过挑战关卡的方式学习 git](https://learngitbranching.js.org/)

[git 的书](https://git-scm.com/book/zh/v2)

[使用 git 时出问题的应对之法（飞行规则）](https://github.com/k88hudson/git-flight-rules/blob/master/README_zh-CN.md)

[个人 git 笔记](https://github.com/jaywcjlove/git-tips)

[git 备忘单](http://ndpsoftware.com/git-cheatsheet.html#loc=stash;)
