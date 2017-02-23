---
title: git
date: 2017-02-20 20:09:26
tags: 
    - git
commit: false

---
### Git
- [git 命令大全](https://gist.github.com/guweigang/9848271)
- git --help
- git init
- git add readme.md
- git commit -m 'readme.md'
- git status
- git branch
- git branch dev
- git checkout dev
- git checkout master
- git merge dev
- git merge --no-ff -m "merge name-1 to name" branch
- git branch -d dev
<!--more-->

### log
- git log
- git log -1
- git log -5
- git reflog

### remote
- 远程仓库
- git remote add origin git@github.com:ic-/code
- 报错的话 ： git remote rm origin
- git push -u origin master //首次

### push pull 
- 本地和远程有冲突的话：
- git pull origin master
- git push origin master
- git psuh origin master //默认
- git push origin dev //推送某个分支
- git push origin :dev //删除远程分支

### alias
- 配置别名
- git config --global alias.st status // 用st 代替 status
- git st
- git config --global aliss.co checkout
- git co
- git config --global alias.ci commit
- git ci
- git config --global alias.br branch
- git br
- 查看别名：
- cat .git/config
- vim .git/config //[alias] 修改

### 文件忘记忽略上传远程服务器问题
解决：编辑 .gitignore 文件添加忽略
git rm -r --cached .
git add .
git commit -m 'repush'
git push