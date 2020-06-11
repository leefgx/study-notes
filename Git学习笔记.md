# Git学习笔记

###### 笔记声明：仅为个人学习笔记，摘录自[菜鸟教程](https://www.runoob.com/),仅用作个人学习，侵删。

#### git配置

Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。

这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：

- `/etc/gitconfig` 文件：系统中对所有用户都普遍适用的配置。若使用 `git config` 时用 `--system` 选项，读写的就是这个文件。
- `~/.gitconfig` 文件：用户目录下的配置文件只适用于该用户。若使用 `git config` 时用 `--global` 选项，读写的就是这个文件。
- 当前项目的 Git 目录中的配置文件（也就是工作目录中的 `.git/config` 文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以 `.git/config` 里的配置会覆盖 `/etc/gitconfig` 中的同名变量。

在 Windows 系统上，Git 会找寻用户主目录下的 .gitconfig 文件。主目录即 $HOME 变量指定的目录，一般都是 C:\Documents and Settings\$USER。

此外，Git 还会尝试找寻 /etc/gitconfig 文件，只不过看当初 Git 装在什么目录，就以此作为根目录来定位。

配置用户信息：

```
git config --global user.name "your name"
git config --global user.email "your_email@youremail.com"
```

配置密钥

```
ssh-keygen -t rsa -C "your_email@youremail.com"
```

验证密钥查看配置信息

```
ssh -T git@github.com
```

查看配置信息

```
git config --list
```

查看某个环境变量的设定

```
git config user.name
```

配置文本编辑器

```
git config --global core.editor emacs
```

配置差异分析工具

```
git config --global merge.tool vimdiff
```

#### git工作流程

一般工作流程如下：

- 克隆 Git 资源作为工作目录。
- 在克隆的资源上添加或修改文件。
- 如果其他人修改了，你可以更新资源。
- 在提交前查看修改。
- 提交修改。
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

#### Git 工作区、暂存区和版本库

Git 工作区、暂存区和版本库概念：

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库：**工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

工作区、版本库中的暂存区和版本库之间的关系：![img](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)



图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage, index），标记为 "master" 的是 master 分支所代表的目录树。

图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。

图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。

当对工作区修改（或新增）的文件执行 "git add" 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。

当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。

当执行 "git reset HEAD" 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。

当执行 "git rm --cached <file>" 命令时，会直接从暂存区删除文件，工作区则不做出改变。

当执行 "git checkout ." 或者 "git checkout -- <file>" 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。

当执行 "git checkout HEAD ." 或者 "git checkout HEAD <file>" 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

#### git创建仓库

初始化当前目录（本地仓库）

```
git init
```

初始化指定目录（本地仓库）

```
git init newrepo
```

克隆仓库

```
git clone <repo>
```

```
git clone <url>
```

###### 注：默认情况下，Git会按照你提供的URL所指示的项目的名称创建你的本地项目目录。通常就是该URL最后一个/之后的项目名称。如果你想要一个不一样的名字，你可以在该命令后加上你想要的名称。

克隆仓库到指定目录

```
git clone <repo> <directory>
```

几种效果等价的git clone写法：

```
git clone http://github.com/CosmosHua/locate new
git clone http://github.com/CosmosHua/locate.git new
git clone git://github.com/CosmosHua/locate new
git clone git://github.com/CosmosHua/locate.git new
```

git clone 时，可以所用不同的协议，包括 ssh, git, https 等，其中最常用的是 ssh，因为速度较快，还可以配置公钥免输入密码。各种写法如下：

```
git clone git@github.com:fsliurujie/test.git         --SSH协议
git clone git://github.com/fsliurujie/test.git          --GIT协议
git clone https://github.com/fsliurujie/test.git      --HTTPS协议
```

#### git基本操作

跟踪文件

```
git add <filename>
```

提交文件

```
git commit -[a]m '初始化项目版本'
```

查看git状态

```
git status [-s]
```

```
git diff
```

执行git diff来查看执行git status的结果的详细信息。

git diff命令显示已写入缓存与已修改但尚未写入缓存的写入的区别。git diff有两个主要的应用场景。

- 尚未缓存的调整：**git diff**
- 查看已缓存的缓存：**git diff --cached**
- 查看已缓存的与未缓存的所有替换：**git diff HEAD**
- 显示摘要而非整个diff： **git diff --stat**

git reset HEAD命令用于取消已缓存的内容

```
git reset HEAD
```

从Git中移除文件

```
git rm <filename>
```

如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项**-f**

```
git rm -f <文件>
```

如果把文件从暂存区域中移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用**--cached**选项即可

```
git rm --cached <file>
```

递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件：

```
git rm –r * 
```

git mv 命令用于移动或重命名一个文件、目录、软连接

```
git mv README  README.md
```

#### Git 分支管理

创建分支命令：

```
git branch (branchname)
```

切换分支命令:

```
git checkout (branchname)
```

合并分支命令:

```
git merge (branchname)
```

创建新分支并立即切换到该分支下：

```
git checkout -b newtest
```

删除分支命令：

```
git branch -d (branchname)
```

执行 `git branch -a` 可以查看所有的分支名

合并冲突

一个合并冲突就出现了，接下来我们需要手动去修改它。

修改完成后，在 Git 中，我们可以用 git add 要告诉 Git 文件冲突已经解决

#### git查看提交历史

```
git log [--oneline][--graph][reverse][--author][--since][--before][--until][--after][--no-merges]
```

#### git标签

```
git tag [-a] v1.0
```

```
git tag [-a] v0.9 85fc7e7
```

查看所有标签

```
git tag
```

指定标签信息命令

```
git tag -a <tagname> -m "runoob.com标签"
```

PGP签名标签命令：

```
git tag -s <tagname> -m "runoob.com标签"
```

删除标签

```
git tag -d v1.1
```

查看此版本所修改的内容

```
git show v1.0
```

#### git远程仓库

添加一个新的远程仓库

```
git remote add [shortname] [url]
```

查看当前配置有哪些远程仓库

```
git remote
```

提取远程仓库：

远程仓库下载新分支与数据：

```
git fetch origin master
```

该命令执行完后需要执行git merge 远程分支到你所在的分支。

从远端仓库提取数据并尝试合并到当前分支：

```
git merge origin/master
```

推送到远程仓库

推送新分支与数据到远端仓库命令

```
git push origin master
```

删除远程仓库

```
git remote rm origin
```

##### master、origin master 与 origin/master 有什么区别？

- **master** 这个很好理解，它代表本地的某个分支名。
- **origin master** 代表着两个概念，前面的 **origin** 代表远程名，后面的 **master** 代表远程分支名。
- **origin/master** 只代表一个概念，即远程分支名，是从远程拉取代码后在本地建立的一份拷贝（因此也有人把它叫作本地分支）。

- 执行 `git fetch origin master` 时，它的意思是从名为 **origin** 的远程上拉取名为 **master** 的分支到本地分支 **origin/master** 中。既然是拉取代码，当然需要同时指定远程名与分支名，所以分开写。
- 执行 `git merge origin/master` 时，它的意思是合并名为 **origin/master** 的分支到当前所在分支。既然是分支的合并，当然就与远程名没有直接的关系，所以没有出现远程名。需要指定的是被合并的分支。
- 执行 `git push origin master` 时，它的意思是推送本地的 **master** 分支到远程 **origin**，涉及到远程以及分支，当然也得分开写了。
- 还可以一次性拉取多个分支的代码：`git fetch origin master stable oldstable`；
- 也还可以一次性合并多个分支的代码：`git merge origin/master hotfix-2275 hotfix-2276 hotfix-2290`；

#### Git Gitee

#### Git 服务器搭建