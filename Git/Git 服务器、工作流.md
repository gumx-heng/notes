# Git 服务器

## 4.1 协议

Git 主要使用四种协议来传输资料：

* 本地协议 （local）
	
	其中远程版本就是硬盘中的另一个目录。命令如下：
	
		$ git clone /opt/git/project.git
		$ git clone file:///opt/git/project.git

* HTTP 协议
	
	HTTP 协议分为两种：一种是 “智能” HTTP 协议，只运行在HTTP/S 端口上，并且可以使用各种 HTTP 验证机制，可读写，需要输入用户名和密码，必要时可以验证 SSL，Git 1.6.6之后引入的。另一种是 哑（Dumb） HTTP 协议，这是一种只读协议，Git 1.6.6之前的，并不常用。

		$ git clone https://example.com/gitproject.git
	
* SSH（Scure Shell）协议


	架设 Git 服务器时常用 SSH 协议作为传输协议，SSH 协议是一个验证授权的网络协议。用例如下：

		$ git clone ssh://user@server/project.git
	
	或者使用一个简短的 scp 式的写法：
	
		$ git clone user@server:project.git


* Git 协议

	
	接下来是 Git 协议。 这是包含在 Git 里的一个特殊的守护进程；它监听在一个特定的端口（9418），类似于 SSH 服务，但是访问无需任何授权。
	
	优点：目前，Git 协议是 Git 使用的网络传输协议里最快的。
	缺点：目前，Git 协议是 Git 使用的网络传输协议里最快的。


# Git 工作流


## 5.1 分布式工作流程

* 集中式工作流（不使用分支的情况下）
* 集成管理者工作流 （多仓库的管理）
* 司令官与副官工作流（多仓库管理的变种，增加一级）


## 5.2 提交准则

* 提交前删除空格。 使用 git diff --check 查找空格类的修改

		$ git diff --check

* 对于巨大的提交，提交前可以拆分各个问题，逐个提交。对于两个问题修改同一个问题的文件，可以使用 git add --patch 来部分暂存文件。
* 规范的提交信息

