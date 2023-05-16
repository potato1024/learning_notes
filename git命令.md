```shell
#配置用户名和邮箱
git config --global user.name "root"
git config --global user.email "root@root.cn"
#查看用户名和邮箱
git config --global user.email  
git config --global user.name

#初始化仓库
git init

#查看修改的状态
git status 
#添加工作区到暂存区
git add .
#提交暂存区到本地仓库
git commit -m"提交日志"
#查看提交日志
git log
git log --pretty=oneline --abbrev-commit --all --graph

#为命令设置别名
vim ~/.zshrc
#添加以下内容
alias git-log='git log --pretty=oneline --abbrev-commit --all --graph'
alias ll='ls -al'
###########
source ~/.zshrc

#版本回退
git reset --hard a9fb6f0
git reset a9fb6f0 --hard

#查看已经删除的记录
git reflog

#添加忽略模板
touch .gitignore

#查看本地分支
git branch

#创建本地分支
git branch dev01

#切换分支
git checkout dev01

#创建并切换
git checkout -b dev02

#合并分支到master(先切换到master)
git merge dev01

#删除分支，需要做各种检查
git branch -d dev02
#删除分支，强制删除
git branch -D dev02

#生成SSH公钥
ssh-keygen -t rsa

#获取公钥
cat ~/.ssh/id_rsa.pub
#####在gitee设置中配置#####

#测试连接
ssh -T git@gitee.com

#添加远程仓库（起名为origin，约定）
git remote add origin git@gitee.com:potato2048/git_test.git

#查看远程仓库
git remote 

#将本地的master分支推送到远程仓库origin
git push origin master
#远程分支名，一样可以省略
git push origin master:master
#不解决冲突，强制覆盖，一般禁用此权限
git push -f origin master
#推送到远程的同时建立和远端分支的关系
git push --set-upstream origin master
#如果当前分支和远端分支已经关联，可以省略分支名和远端名
git push

#查看本地分支和远端的关系
git branch -vv

#从远程仓库克隆，本地目录为hello_git
git clone git@gitee.com:potato2048/git_test.git hello_git

#抓取：将仓库的更新都抓取到本地，不进行合并
git fetch
####如果不指定远端名称和分支名，则抓取所有分支
#拉取：将仓库的更新都拉到本地，并自动合并，等同于fetch + merge
git pull 
####如果不指定远端名称和分支名，则拉取所有分支
```





