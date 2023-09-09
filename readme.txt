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
