Git is a version control system.
Git is free software.
git init 初始化一个git仓库
git add <file>添加文件
git commit -m <message>完成

穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。一般使用git log --pretty=oneline
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
回退使用 git reset --hard HEAD^ ，多个版本使用HEAD~100
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

暂存区是git非常重要的概念，利用git status来进行追踪

提交后，用git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别

git checkout -- file可以丢弃工作区的修改
这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

用命令git reset HEAD <file>可以把暂存区的修改撤销掉（unstage），重新放回工作区

小结：
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
场景3：已经上传到版本库，可以使用前面的版本回退，前提是没有上传到远程库。

rm test.txt 在文件管理器删除文件，git status可以检查这一变化
现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit
另一种情况是删错了，因为版本库里还有呢，误删的文件恢复到最新版本：$ git checkout -- test.txt
git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

ls -ah 显示隐藏文件

在github通过create a new repo来新建一个仓库
要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名；
关联后使用命令git push -u origin master第一次推送master分支的所有内容，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
从现在起，只要本地作了提交，就可以通过命令：
$ git push origin master
把本地master分支的最新修改推送至GitHub。此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

如果添加的时候地址写错了，或者就是想删除远程库，可以用git remote rm <name>命令。使用前，建议先用git remote -v查看远程库信息：
$ git remote -v
然后，根据名字删除，比如删除origin
实际上只是删除了联系，删除需要登陆github

从零开发，最好的方式是先创建远程库，然后，从远程库克隆
首先，登陆GitHub，创建一个新的仓库，名字叫gitskills，并且设置README文件
下一步是用命令git clone克隆一个本地库：
$ git clone git@github.com:michaelliao/gitskills.git
注意把Git库的地址换成你自己的，然后进入gitskills目录看看，已经有README.md文件了：
还可以用https://github.com/michaelliao/gitskills.git这样的地址
使用https除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用ssh协议而只能用https。
