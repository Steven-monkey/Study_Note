1. ### git基本使用方式

```markdown
----------初始化一下仓库
git init 
输出--	
	Initialized empty Git repository in /Users/monkey/Documents/python/python-AI/.git/	


----------查看隐藏文件
ls -ah
输出--
 	 	.			.git
  	..			1持续集成系统.py


---------获取当前文件夹位置
pwd
输出--
	/Users/monkey



----------查看git库的状态
git status
输出--
  	On branch master

  	No commits yet

  	Untracked files:
    (use "git add <file>..." to include in what will be committed)
    .DS_Store
    1.matplotlib.py
    matplotlib.png
    test.png
    "\346\200\273\347\273\223.xmind"
    "\346\234\272\345\231\250\345\255\246\344\271\240.md"

  	nothing added to commit but untracked files present (use "git add" to track)
 ------------------------------------------------------------


----------提交文件到仓库——>把文件添加暂存区
git add [文件名]
	可以多次反复提交使用，add一次只能提交一个文件
输出--
	没有消息就是好消息


----------提交文件到仓库——>把文件提交到当前分支
git commit -m "添加库的描述信息"
输出--
	[master (root-commit) 7c6ac19] 这是一个python练习
 	Committer: Monkey <monkey@MonkeydeMacBook-Air.local>
	Your name and email address were configured automatically based
	on your username and hostname. Please check that they are accurate.
	You can suppress this message by setting them explicitly. Run the
	following command and follow the instructions in your editor to edit
	your configuration file:

    git config --global --edit

	After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 	1 file changed, 1 insertion(+)
	 create mode 100644 "1\346\214\201\347\273\255\351\233\206\346\210\220\347\263\273\347\273\237.py"
-------------------------------------------------------------
上面两步就是：
					1.先将文件添加到暂存区
					2.再一次性将文件全部添加到分支


随后还可以执行一次 git status 查看一下仓库的信息。


----------查看文件的修改内容
git diff
输入--
  	diff --git 			"a/1\346\214\201\347\273\255\351\233\206\346\210\220\347\263\273\347\273\237.py" "b/1\346\214\201\347\273\255\351\233\206\346\210\220\347\263\273\347\273\237.py"
  	index 297d411..71797f2 100644
  	--- "a/1\346\214\201\347\273\255\351\233\206\346\210\220\347\263\273\347\273\237.py"
  	+++ "b/1\346\214\201\347\273\255\351\233\206\346\210\220\347\263\273\347\273\237.py"
  	@@ -1 +1 @@
 		 -        
  	\ No newline at end of file
 	 +import random【查看修改的地方】
  	\ No newline at end of file

----------然后再次执行 git add
----------然后再次执行 git commit -m [解释文本]


---------查看版本文件
git log
输出--

    commit 1bb922cd906d0003eddf6731853df4bd35f68adc (HEAD -> master)
    Author: Monkey <monkey@MonkeydeMacBook-Air.local>
    Date:   Wed Dec 15 20:13:57 2021 +0800

        这是一个python小练习

    commit a5fe56a9d16cd785f0bf7b84b1f8571739e6a2b6
    Author: Monkey <monkey@MonkeydeMacBook-Air.local>
    Date:   Wed Dec 15 20:10:02 2021 +0800

        这是一个python小练习

    commit 7c6ac193462ed5e1ec5c9b9dc8350bc2c78e094b
    Author: Monkey <monkey@MonkeydeMacBook-Air.local>
    Date:   Wed Dec 15 20:03:18 2021 +0800

        这是一个python练习

git log --pretty=oneline
输出--
	1bb922cd906d0003eddf6731853df4bd35f68adc (HEAD -> master) 这是一个python小练习
	a5fe56a9d16cd785f0bf7b84b1f8571739e6a2b6 这是一个python小练习
	7c6ac193462ed5e1ec5c9b9dc8350bc2c78e094b 这是一个python练习

----------回溯到上一个版本
git reset --hard HEAD^
输出--
	HEAD is now at a5fe56a 这是一个python小练习

--------再次执行
git log
输出--
	commit a5fe56a9d16cd785f0bf7b84b1f8571739e6a2b6 (HEAD -> master)
	Author: Monkey <monkey@MonkeydeMacBook-Air.local>
	Date:   Wed Dec 15 20:10:02 2021 +0800

    这是一个python小练习

	commit 7c6ac193462ed5e1ec5c9b9dc8350bc2c78e094b
	Author: Monkey <monkey@MonkeydeMacBook-Air.local>
	Date:   Wed Dec 15 20:03:18 2021 +0800

    这是一个python练习
=======追溯到了上一个版本

----------还可以回到更改前到版本
【要找到版本号，可以不用写全，写前4，5个就行】
git reset --hard1bb922cd906d0003eddf6731853df4bd35f68adc

----------记录每一次的命令【可以找到你的版本号】
git reflog


----------恢复最新版本
git restore <file>

----------删除版本库
git rm <文件>
git commit -m '描述文字'
```



2. ### GitHub(远程仓库)设置与使用--先有本地库

```markdown
----------设置公钥和私钥
ssh-keygen -t rsa -C "邮箱"

然后把.pub文件复制到GitHub上

----------创建远程仓库和推送本地库
git remote add origin git@github.com:Steven-monkey/learngit.git
git branch -M main
git push -u origin main    ——>把本地库内容推送到远程

只要本地执行-->
			1.git add [文件名]
			2.git commit -m '描述信息'
			3.git push  origin master

----------查看远程库信息
git remote -v  ——>查看远程库信息
输出--
	origin	git@github.com:Steven-monkey/learngit.git (fetch)
	origin	git@github.com:Steven-monkey/learngit.git (push)


----------删除远程库
输入 git remote 会提示很多信息
输出--
		usage: git remote [-v | --verbose]
   	or: git remote add [-t <branch>] [-m <master>] [-f] [--tags | 		--no-tags] [--mirror=<fetch|push>] <name> <url>
   	or: git remote rename <old> <new>
  	 or: git remote remove <name>
  	 or: git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
  	 or: git remote [-v | --verbose] show [-n] <name>
  	 or: git remote prune [-n | --dry-run] <name>
  	 or: git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)...]
  	 or: git remote set-branches [--add] <name> <branch>...
  	 or: git remote get-url [--push] [--all] <name>
  	 or: git remote set-url [--push] <name> <newurl> [<oldurl>]
  	 or: git remote set-url --add <name> <newurl>
   	or: git remote set-url --delete <name> <url>

   	 -v, --verbose         be verbose; must be placed before a subcommand



git remote remove <name>  ——>删除远程仓库，本质就是断开远程和本地的连接
```

3. ### GitHub(远程仓库)设置与使用--先有远程库

```markdown
----------先创建远程库

----------克隆远程库到本地库
git clone --git@github.com:Steven-monkey/Study_Note.git
```

4. ### GitHub创建分支

```markdown
----------创建分支并切换到该分支
git checkout -b dev  ——>git checkout 命令加-b表示创建并切换

----------查看当前分支
git branch
当前分支前会带有*

----------切换分支
git checkout <分支>

---------合并分支（合并前要切换到主分支，然后再执行合并）
git merge <分支>

----------最新创建和切换分支
git switch -c <分支> ——>创建和切换到分支
git switch <分支>	——>切换分支
```

5. ### 解决冲突

```markdown
人生不如意之事十之八九。
----------
在分支上提交
git add 文件名
git commit -m '提示信息'

切换到主支上
git switch main
输出--
	


git log --graph --pretty=oneline --abbrev-commit
```

