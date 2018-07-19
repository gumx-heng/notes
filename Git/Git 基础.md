# Git 基础


Git 基础，即学会一个基本的Git使用流程和一些基本概念。主流程包括获取仓库、提交修改、推送修改、撤销修改。以及辅助的打标签，修改远程仓库地址功能。


## 2.1 获取 Git 仓库

有两种获取Git仓库的方式：


* 在现有项目或者目录下导入所有文件到Git中；
* 从一个服务器克隆一个现有的Git仓库

### 从现有目录中初始化仓库

在项目目录下打开git命令行工具，执行init操作

	$ git init

该命令将会创建一个名为 .git 的目录，这个目录包就是Git仓库的主文件夹。存放着文件跟踪的所有信息。

### 克隆仓库

如果你获得一份已经存在的Git仓库的拷贝，可以使用 git clone 命令，来拉取 Git 仓库的几乎所有文件，包括每一个文件的每一个版本。这也正是Git的一大特性，通过克隆，你可以得到一个和远程仓库一样的本地仓库，就像复制粘贴一样。此时，这个仓库就是你自己的花园，你可以随意修剪。

	$ git clone https://github.com/libgit2/libgit2
	

Git 支持多种数据传输协议。 上面的例子使用的是 https:// 协议，不过你也可以使用 git:// 协议或者使用 SSH 传输协议，比如 user@server:path/to/repo.git



## 2.2 记录每次更新到仓库

每一个文件都不外乎这两种状态：**已跟踪或未跟踪**。**已跟踪的文件**是指那些被纳入了版本控制的文件，在上一次快照中有它们的记录，在工作一段时间后，它们的状态可能处于未修改，已修改或已放入暂存区。 工作目录中除已跟踪文件以外的所有其它文件都属于**未跟踪文件**，它们既不存在于上次快照的记录中，也没有放入暂存区。所谓的更新就是文件的状态更新。

一个文件的总是从未跟踪到已跟踪，从已修改到已暂存到已提交，然后再从已提交到已暂存再到已提交，如次循环。或者删除文件，退出跟踪。生命周期图如下




![Git 文件生命周期](./images/Git文件生命周期.png)


###通过 git status 命令，我们可以查看仓库中文件的状态。

	$ git status
	On branch master // 当前所在分支
	Your branch is up to date with 'origin/master'. //当前分支的状态

	Changes to be committed://待提交的修改（已暂存）
  	(use "git reset HEAD <file>..." to unstage)

	modified:   Git/Git 基础.md

	Changes not staged for commit:待暂存的修改（已修改）
  	(use "git add/rm <file>..." to update what will be committed)
  	(use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    Git/b.png

	Untracked files: 待追踪的文件
  	(use "git add <file>..." to include in what will be committed)

	Git/images/


###使用命令 git add 开始跟踪一个文件/暂存一个文件。

	$ git add README
	
这是个多功能命令：可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态等，git add 命令使用文件或目录的路径作为参数；如果参数是目录的路径，该命令将递归地跟踪该目录下的所有文件。

###状态简览

使用 git status -s 或者 git status --short 查看更为简洁的状态报告。

	$ git status -s
	MM "Git/Git 基础.md"
	 D Git/b.png
	?? Git/images/

?? 标记未追踪的文件，A 表示新添加追踪的文件，D 表示删除的文件，M 分为左右两种，左边的M表示修改已暂存的文件，右边的表示修改未暂存。


### 忽略文件

使用 .gitignore 配置不需要Git管理的文件。比如日志文件等临时文件。

文件 .gitignore 的格式规范如下：

* 所有空行或者以 ＃ 开头的行都会被 Git 忽略。

* 可以使用标准的 glob 模式匹配。

* 匹配模式可以以（/）开头防止递归。

* 匹配模式可以以（/）结尾指定目录。

* 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。

例子

	# no .a files
	*.a
	
	# but do track lib.a, even though you're ignoring .a files above
	!lib.a
	
	# only ignore the TODO file in the current directory, not subdir/TODO
	/TODO
	
	# ignore all files in the build/ directory
	build/
	
	# ignore doc/notes.txt, but not doc/server/arch.txt
	doc/*.txt
	
	# ignore all .pdf files in the doc/ directory
	doc/**/*.pdf


### 查看已暂存和未暂存的修改

使用 git diff 查看未暂存的文件的修改内容。
使用 git diff --cached 查看已暂存的文件的修改内容

### 提交已暂存的修改

使用 git commit 提交已暂存的修改

	$ git commit

然后填写提交信息。 也可以使用git commit -m “msg” 在一行命令里完成提交和信息的填写。


### 跳过使用暂存区域

有时候，提交就是要提交所有的改动， 此时要先执行 git add . 将所有文件暂存，然后在执行 git commit -m ‘msg’。这样会显得麻烦， 此时可以使用 git commit -a -m ‘msg’ 实现一行命令实现提交修改的功能。


### 移除文件
要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），然后提交。 可以用 git rm 命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清单中了。


另外一种情况是，我们想把文件从 Git 仓库中删除（亦即从暂存区域移除），但仍然希望保留在当前工作目录中。 换句话说，你想让文件保留在磁盘，但是并不想让 Git 继续跟踪。 当你忘记添加 .gitignore 文件，不小心把一个很大的日志文件或一堆 .a 这样的编译生成文件添加到暂存区时，这一做法尤其有用。 为达到这一目的，使用 --cached 选项：

	$ git rm --cached README


### 移动文件

Git 并不显式跟踪文件移动操作。 如果在 Git 中重命名了某个文件，仓库中存储的元数据并不会体现出这是一次改名操作。

要在 Git 中对文件改名，可以这么做：

	$ git mv file_from file_to

运行 git mv 就相当于运行了下面三条命令：

	$ mv README.md README
	$ git rm README.md
	$ git add README

如此分开操作，Git 也会意识到这是一次改名，所以不管何种方式结果都一样。 两者唯一的区别是，mv 是一条命令而另一种方式需要三条命令，直接用 git mv 轻便得多。 不过有时候用其他工具批处理改名的话，要记得在提交前删除老的文件名，再添加新的文件名。



## 2.3 查看提交历史

## 2.4 撤销操作

## 2.5 远程仓库的使用

## 2.6 打标签

## 2.7 Git 别名

## 2.8 总结

