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
