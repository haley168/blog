#### git学习笔记 [返回首页](/haley168)
>1. git托管平台
coding  github gitlab 码云 gogs
>2. 来源 [廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

#### 基本概念
1. 工作区（Working Directory）--电脑的文件夹
1. 版本库（Repository）--其实就是那个隐藏的.git文件夹
1. 最重要的就是称为stage（或者叫index）的暂存区

#### 基本操作
>创建文件夹，进入文件夹，查看文件夹的路径是否含中文
```
mkdir learngit
cd learngit
pwd
```

#### 初始化仓库
```
git init
```
#### 将文件放于文件夹，并添加到仓库
```
git add readme.txt
```

#### 将文件提交到仓库
```
git commit -m "wrote a readme file"
```

#### 查看仓库状态
```
git status
```
#### 查看文件变化情况
```
git diff
```
#### 显示从最近到最远的提交日志
```
git log
```
#### 简化输出提交日志
```
git log --pretty=oneline
```

#### 版本回退
1. HEAD 当前版本
1. HEAD^ 上一个版本
1. HEAD^^ 上上一个版本
1. HEAD~100 往上100个版本

#### 回退到上一版本
```
git reset --hard HEAD^
```
#### 查看文件内容
```
cat readme.txt
```
#### 记录你的每一次命令
```
git reflog
```
#### 丢弃工作区的修改
```
git checkout -- readme.txt
```
>一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

#### 切换分支
```
git checkout name
git checkout -- test.txt
```
#### 添加远程库
```
git remote add origin git@github.com:haley/learngit.git
```
#### 本地推送到远程
```
git push -u origin master
```
>由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

#### 之后提交到远程
```
git push origin master
```
#### 克隆远程库
```
git clone git@github.com:b110/gitskills.git
git clone git@github.com:b110/learngit.git
```
>以下2个地址都可以，但是https会更慢一些
git@github.com:b110/learngit.git
https://github.com/b110/gitskills.git

#### 创建并切换分支，带-b
```
git checkout -b dev
```
#### 创建分支
```
git branch dev
```
#### 切换分支
```
git checkout dev
```
#### 查看当前分支，带*的为当前分支
```
git branch
```

#### 合并指定分支到当前分支
```
git merge dev
```

#### 删除分支
```
git branch -d feature1
```

#### 储藏当前状态，先改bug
```
git stash
```

#### 创建临时分支
```
git checkout -b issue-101
```

#### 回到工作现场
```
git stash pop
```

#### 强行删除未提交的分支
```
git branch -D feature-vulcan
```

#### 查看远程库名称
```
git remote
```

#### 打标签
```
git tag v1.0
```

#### 查看标签信息
```
git show v0.9
```

#### 删除标签
```
git tag -d v0.1
```

#### 推送标签到远程
```
git push origin v1.0
```

#### 一次性推送全部尚未推送到远程的本地标签
```
git push origin --tags
```

#### 配置别名，配置st为status
```
git config --global alias.st status
```
>很多人都用co表示checkout，ci表示commit，br表示branch

#### 配置一个git last，让其显示最后一次提交信息：
```
git config --global alias.last 'log -1'
```
#### 丧心病狂地把lg配置成了
```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```