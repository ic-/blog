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

### clone
- git clone xxxx.git newfilename

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
- git remote -v 远端仓库实际链接
- git remote rm 别名[alias]
- git remote add [alias] git@gitxxx.git
### fetch 
- 从远端仓库下载新分支与数据
### push pull 
- 从远端仓库提取数据并尝试合并到当前分支
- 本地和远程有冲突的话：
- git pull origin master
- git push origin master
- git psuh origin master //默认
- git push origin dev //推送某个分支
- git push origin :dev //删除远程分支
- git push origin -f 强制覆盖

### Reset checkout revert
- reset checkout (指定文件或所有文件) revert 不能指定文件
- git reset HEAD@{2}/git checkout hotfixbranch 
    - --soft 缓存区和工作目录都不会被改变
    - --mixed 默认选项。缓存区和你指定的提交同步，但工作目录不受影响
    - --hard 缓存区和工作目录都同步到你指定的提交 

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

### gitlab master 代码分支有问题
问题：基础框架最新版本有问题，不知道的情况下提交了gitlab
解决：
    - 方法1：
        - 获取gitlab owner权限
        - 本地master分支代码reset到正确节点
        - git push -f 强制覆盖
    - 方法2：
        - 本地拉个dev分支 分支代码reset到正确节点 备用
        - git 删除master 代码 提交远程
        - git merge dev  
            - merge 代码没过来。。
            - 用了拷贝
        - git push 到远程
    