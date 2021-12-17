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
----------在分支上提交
git add 文件名
git commit -m '提示信息'

----------切换到主支上
git switch main
输出--
	Switched to branch 'main'
	Your branch is ahead of 'origin/main' by 1 commit.
  	(use "git push" to publish your local commits)


----------git log也可以看到分支的合并情况：
git log --graph --pretty=oneline --abbrev-commit
```

6. ### 分支管理

```markdown
主分支上创建分支，在分支上再创建分支。
git merge --no-ff -m "merge with no-ff" dev
```

7. ### BUG分支

```markdown
----------保存现有工作区，让你可以去做另外一件事
git stash

----------查看之前保存的工作区
git stash list
输出--
	stash@{0}: WIP on dev: f52c633 add merge
	
---------恢复之前的保存的工作区
git stash apply
	---恢复后，stash内容并不删除，你需要用git stash drop来删除
git stash pop
	---恢复的同时把stash内容也删了
	---再用git stash list查看时，就看不到任何内容了stash内容了
----------修复了主分支bug，分支上也有bug，也要先修复。
git cherry-pick 4c805e2

----------丢弃一个没有被合并过的分支  大写D
git branch -D <name>
```

8. ### 多人协作

```markdown
---------查看远程库信息
git remote
git remote -v
----------推送远程库
git push origin master
git push origin dev
		1.master分支上主分支，要时刻与远程同步
		2.dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步
		3.bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
		4.feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发

---------解决远程推送冲突问题
git pull ——>抓取提交信息，在本地合并，解决冲突，再推送

----------本地分支和远程分支要建立连接，然后再pull
git branch --set-upstream-to=origin/dev dev
```

- #### 多人协作整体流程

```markdown
1.首先，可以试图用git push origin <branch-name>推送自己的修改；

2.如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

3.如果合并有冲突，则解决冲突，并在本地提交；

4.没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

5.如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。
```

- #### 小结

```markdown
1.查看远程库信息，使用git remote -v；

2.本地新建的分支如果不推送到远程，对其他人就是不可见的；

3.从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

4.在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

5.建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

6.从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。
```

9. ### 创建标签

```markdown
----------创建标签
git tag v1.0
----------查看标签
git tag
---------补之前没有打的标签
git log --pretty=oneline --abbrev-commit   ——>找到历史提交（最重要的是那个号码）
--输出
	12a631b (HEAD -> master, tag: v1.0, origin/master) merged bug 	fix 101
	4c805e2 fix bug 101
	e1e9c68 merge with no-ff
	f52c633 add merge
	cf810e4 conflict fixed
	5dc6824 & simple
	14096d0 AND simple
	b17d20e branch test
	d46f35e remove test.txt
	b84166e add test.txt
	519219b git tracks changes
	e43a48b understand how stage works
	1094adb append GPL
	e475afc add distributed
	eaadf4e wrote a readme file	
----------补标签
git tag v0.9 f52c633

----------查看标签信息
git show <标签名字>
git show v1.0

----------创建带有说明的标签
git tag -a v0.1 -m "version 0.1 released" 1094adb
```

10. ### 操作标签

```markdown
---------删除标签
git tag -d v0.1
输出--
	Deleted tag 'v0.1' (was f15b0dd)
----------推送标签到远程
git push origin v1.0
---------推送全部标签到远程
git push origin --tags

如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：
git tag -d v0.9
git push origin :refs/tags/v0.9
```

11. ### Github使用

```markdown
----------克隆其他项目
点“Fork”就在自己的账号下克隆了一个仓库
然后再自己仓库下down下来
```

12. ### 自定义Git

```markdown
----------显示git的颜色
git config --global color.ui true
```

- #### 忽略特殊文件

```markdown
----------忽略文件组合
https://github.com/github/gitignore

----------强制添加忽略文件
git add -f App.class    ——>添加一个-f

----------检测.gitignore文件
git check-ignore -v <文件名>

----------编写.gitignore文件规则
.* ----->忽略以.开头的所有文件
*.class ---->排除所以.class文件
!.gitignore ---->不排除.gitignore文件
!app.class ---->不排除app.class文件
```

13. ### 配置别名

```markdown
----------更改git命令
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.br branch

----------查看和修改配置文件
cat .git/config 

当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中
# This is Git's per-user configuration file.
[user]
	name = Monkey
	email = 445928814@qq.com
# Please adapt and uncomment the following lines:
#	name = Monkey
#	email = monkey@MonkeydeMacBook-Air.local
[color]
	ui = true

```

