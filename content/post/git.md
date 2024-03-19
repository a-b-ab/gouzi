+++
title = 'git'
date = 2024-03-19T13:35:01+08:00
draft = false
+++
# git

**啊能镇楼**

![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403181915672.jpeg)

## git配置

        $ git config --global user.name "runoob"
         $ git config --global user.email test@runoob.com

## 查看配置信息

        $ git config --list

## git工作流程

* 克隆git资源作为工作目录
* 在克隆的资源上添加或修改文件
* 如果其他人修改，你可以更新资源
* 在提交前查看修改
* 提交修改
* 在修改完成后，如果发现有错误，可以撤回提交并再次修改并提交

## 基本概念
* **工作区**：就是你在电脑里能看到的目录
* **暂存区**：英文叫stage或index，一般存放在 *.git* 目录下的index文件，所以我们把暂存区有时也叫作索引（index）
* **版本库**：工作区有一个隐藏目录 *.git*，这个不算工作区，而是Git的版本库

![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403181722043.png)

* 图中左侧为工作区，右侧为版本库。在版本库中标记为“index”的区域是暂存区（stage/index）,标记为“master”的是master分支所代表的目录树
* 图中我们可以看出此时“HEAD”实际是指向master分支的一个“游标”。所以图示的命令中出现HEAD的地方是可以用master来替换的
* 图中的object标识的区域为git的对象库，实际位于“.git/objects”目录下，里面包含了创建的各种对象及内容
* 当对工作区修改（或新增）的文件执行git add命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中
* 当执行提交（git commit）时，暂存区的目录树写到版本库（对象库）中，master分支会相应的更新。即master指向的目录树就是提交时暂存区的目录树
* 当执行 *git reset HEAD* 操作时，暂存区的目录树会被重写，被master分支指向的目录树所替换，但是工作区不受影响
* 当执行 *git rm --cached<file>* 命令时，会直接从暂存区删除文件，工作区则不做出改变。
* 当执行 *git checkout .* 或者 *git checkout -- <file>* 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。
* 当执行 *git checkout HEAD .* 或者 *git checkout HEAD <file>* 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动

## git 创建仓库
*git init初始化一个仓库*
Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。
在执行完成 git init 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。

*git init newrepo*使用我们指定目录作为Git仓库

初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交

```
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'

```
以上命令将目录下以 .c 结尾及 README 文件提交到仓库中。

**注： 在 Linux 系统中，commit 信息使用单引号 '，Windows 系统，commit 信息使用双引号 "。所以在 git bash 中 git commit -m '提交说明' 这样是可以的，在 Windows 命令行中就要使用双引号 git commit -m "提交说明"**

### git clone
我们使用 git clone 从现有 Git 仓库中拷贝项目
```
git clone <repo>
```

如果我们需要克隆到指定的目录，可以使用以下命令格式

```
git clone <repo> <directory>
```

参数说明
* repo：git仓库
* directory：本地目录

比如，要克隆 Ruby 语言的 Git 代码仓库 Grit，可以用下面的命令：
```
$ git clone git://github.com/schacon/grit.git
```

执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。

如果要自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：
```
$ git clone git://github.com/schacon/grit.git mygrit
```

![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403181910344.png)

* git init 初始化仓库
* git add . 添加文件到暂存区
* git commit 将暂存区内容添加到仓库中

### 创建仓库命令
* git 初始化仓库
* git clone 拷贝一份远程仓库，也就是下载一个项目
  

### 提交与修改
* git add 添加文件到暂存区
* git status 查看仓库当前的状态，显示有变更的文件
* git diff 比较文件的不同，即暂存区和工作区的差异
* git commit 提交暂存区到本地仓库
* git reset 回退版本
* git rm 将文件从暂存区和工作区删除
* git mv 移动或重命名工作区文件
* git checkout 分支切换
* git switch 更清晰地切换分支（2.3版本引入）
* git restore 恢复或撤销文件的更改


### 提交日志
* git log 查看历史提交记录
* git blame <file> 以列表形式查看指定文件的历史修改记录

### 远程操作
* git remote 远程仓库操作
* git fetch 从远程获取代码库
* git pull 下载远程代码并合并
* git push 上传远程代码并合并

## git分支管理
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403181930456.png)

创建分支命令：
git branch (branchname)

切换分支命令
git checkout (branchname)

当你切换分支的时候，git会用该分支的最后提交的快照替换你的工作目录的内容，以多个分支不需要多个目录。

合并分支命令
git merge

你可以多次合并到统一分支， 也可以选择在合并之后直接删除被并入的分支。


## git 分支管理
### 列出分支
git branch
没有参数时，git branch 会列出你在本地的分支

        $ git branch
        * master

此例的意思就是，我们有一个叫做 master 的分支，并且该分支是当前分支。

当你执行 git init 的时候，默认情况下 Git 就会为你创建 master 分支。

如果我们要手动创建一个分支。执行 git branch (branchname) 即可

        $ git branch testing
        $ git branch
        * master
        testing

现在我们可以看到，有了一个新分支 testing。

当你以此方式在上次提交更新之后创建了新分支，如果后来又有更新提交， 然后又切换到了 testing 分支，Git 将还原你的工作目录到你创建分支时候的样子。

接下来我们将演示如何切换分支，我们用 git checkout (branch) 切换到我们要修改的分支

        $ ls
        README
        $ echo 'runoob.com' > test.txt
        $ git add .
        $ git commit -m 'add test.txt'
        [master 3e92c19] add test.txt
        1 file changed, 1 insertion(+)
        create mode 100644 test.txt
        $ ls
        README        test.txt
        $ git checkout testing
        Switched to branch 'testing'
        $ ls
        README

当我们切换到 testing 分支的时候，我们添加的新文件 test.txt 被移除了。切换回 master 分支的时候，它们又重新出现了。

        $ git checkout master
        Switched to branch 'master'
        $ ls
        README        test.txt

我们也可以使用 git checkout -b (branchname) 命令来创建新分支并立即切换到该分支下，从而在该分支中操作。

        $ git checkout -b newtest
        Switched to a new branch 'newtest'
        $ git rm test.txt 
        rm 'test.txt'
        $ ls
        README
        $ touch runoob.php
        $ git add .
        $ git commit -am 'removed test.txt、add runoob.php'
        [newtest c1501a2] removed test.txt、add runoob.php
        2 files changed, 1 deletion(-)
        create mode 100644 runoob.php
        delete mode 100644 test.txt
        $ ls
        README        runoob.php
        $ git checkout master
        Switched to branch 'master'
        $ ls
        README        test.txt

如你所见，我们创建了一个分支，在该分支上移除了一些文件 test.txt，并添加了 runoob.php 文件，然后切换回我们的主分支，删除的 test.txt 文件又回来了，且新增加的 runoob.php 不存在主分支中。

使用分支将工作切分开来，从而让我们能够在不同开发环境中做事，并来回切换

### 删除分支
git branch -d (branchname)

例如我们要删除 testing 分支：
        $ git branch
        * master
        testing
        $ git branch -d testing
        Deleted branch testing (was 85fc7e7).
        $ git branch
        * master

### 分支合并
一旦某分支有了独立内容，你终究会希望将它合并回到你的主分支。 你可以使用以下命令将任何分支合并到当前分支中去

git merge

        $ git branch
        * master
        newtest
        $ ls
        README        test.txt
        $ git merge newtest
        Updating 3e92c19..c1501a2
        Fast-forward
        runoob.php | 0
        test.txt   | 1 -
        2 files changed, 1 deletion(-)
        create mode 100644 runoob.php
        delete mode 100644 test.txt
        $ ls
        README        runoob.php

以上实例中我们将 newtest 分支合并到主分支去，test.txt 文件被删除。

合并完后就可以删除分支

        $ git branch -d newtest
        Deleted branch newtest (was c1501a2).

删除后， 就只剩下 master 分支了：

        $ git branch
        * master

### 合并冲突

合并并不仅仅是简单的文件添加、移除的操作，Git 也会合并修改

        $ git branch
        * master
        $ cat runoob.php


首先，我们创建一个叫做 change_site 的分支，切换过去，我们将 runoob.php 内容改为

        <?php
        echo 'runoob';
        ?>

创建 change_site 分支：

        $ git checkout -b change_site
        Switched to a new branch 'change_site'
        $ vim runoob.php
        $ head -3 runoob.php
        <?php
        echo 'runoob';
        ?>
        $ git commit -am 'changed the runoob.php'
        [change_site 7774248] changed the runoob.php
        1 file changed, 3 insertions(+)
        
将修改的内容提交到 change_site 分支中。 现在，假如切换回 master 分支我们可以看内容恢复到我们修改前的(空文件，没有代码)，我们再次修改 runoob.php 文件。

        $ git checkout master
        Switched to branch 'master'
        $ cat runoob.php
        $ vim runoob.php    # 修改内容如下
        $ cat runoob.php
        <?php
        echo 1;
        ?>
        $ git diff
        diff --git a/runoob.php b/runoob.php
        index e69de29..ac60739 100644
        --- a/runoob.php
        +++ b/runoob.php
        @@ -0,0 +1,3 @@
        +<?php
        +echo 1;
        +?>
        $ git commit -am '修改代码'
        [master c68142b] 修改代码
        1 file changed, 3 insertions(+)

现在这些改变已经记录到我的 "master" 分支了。接下来我们将 "change_site" 分支合并过来

        $ git merge change_site
        Auto-merging runoob.php
        CONFLICT (content): Merge conflict in runoob.php
        Automatic merge failed; fix conflicts and then commit the result.

        $ cat runoob.php     # 打开文件，看到冲突内容
        <?php
        <<<<<<< HEAD
        echo 1;
        =======
        echo 'runoob';
        >>>>>>> change_site
        ?>

我们将前一个分支合并到 master 分支，一个合并冲突就出现了，接下来我们需要手动去修改它

        $ vim runoob.php 
        $ cat runoob.php
        <?php
        echo 1;
        echo 'runoob';
        ?>
        $ git diff
        diff --cc runoob.php
        index ac60739,b63d7d7..0000000
        --- a/runoob.php
        +++ b/runoob.php
        @@@ -1,3 -1,3 +1,4 @@@
        <?php
        +echo 1;
        + echo 'runoob';
        ?>

在 Git 中，我们可以用 git add 要告诉 Git 文件冲突已经解决
        $ git status -s
        UU runoob.php
        $ git add runoob.php
        $ git status -s
        M  runoob.php
        $ git commit
        [master 88afe0e] Merge branch 'change_site'

### git查看提交历史
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182000182.png)

我们还可以用 --graph 选项，查看历史中什么时候出现了分支、合并。以下为相同的命令，开启了拓扑图选项

  *   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
  |\  
  | * 7774248 (change_site) changed the runoob.php
  * | c68142b 修改代码
  |/  
  * c1501a2 removed test.txt、add runoob.php
  * 3e92c19 add test.txt
  * 3b58100 第一次版本提交

现在我们可以更清楚明了地看到何时工作分叉、又何时归并。

你也可以用 --reverse 参数来逆向显示所有日志。

        $ git log --reverse --oneline
        3b58100 第一次版本提交
        3e92c19 add test.txt
        c1501a2 removed test.txt、add runoob.php
        7774248 (change_site) changed the runoob.php
        c68142b 修改代码
        d5e9fc2 (HEAD -> master) Merge branch 'change_site'


如果只想查找指定用户的提交日志可以使用命令：git log --author , 例如，比方说我们要找 Git 源码中 Linus 提交的部分

        $ git log --author=Linus --oneline -5
        81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
        3bb7256 make "index-pack" a built-in
        377d027 make "git pack-redundant" a built-in
        b532581 make "git unpack-file" a built-in
        112dd51 make "mktag" a built-in


如果你要指定日期，可以执行几个选项：--since 和 --before，但是你也可以用 --until 和 --after。

例如，如果我要看 Git 项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）

        $ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
        5469e2d Git 1.7.1-rc2
        d43427d Documentation/remote-helpers: Fix typos and improve language
        272a36b Fixup: Second argument may be any arbitrary string
        b6c8d2d Documentation/remote-helpers: Add invocation section
        5ce4f4e Documentation/urls: Rewrite to accomodate transport::address
        00b84e9 Documentation/remote-helpers: Rewrite description
        03aa87e Documentation: Describe other situations where -z affects git diff
        77bc694 rebase-interactive: silence warning when no commits rewritten
        636db2c t3301: add tests to use --format="%N"

更多 git log 命令可查看 http://git-scm.com/docs/git-log 或使用 git log --help 命令查看帮助信息。

git blame
git blame 命令用于逐行显示指定文件的每一行代码是由谁在什么时候引入或修改的。

strong>git blame 可以追踪文件中每一行的变更历史，包括作者、提交哈希、提交日期和提交消息等信息。

如果要查看指定文件的修改记录可以使用 git blame 命令，格式如下

git blame [选项] <文件路径>

![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182013279.png)

## git标签

如果你达到一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 git tag 给它打上标签。

比如说，我们想为我们的 runoob 项目发布一个"1.0"版本。 我们可以用 git tag -a v1.0 命令给最新一次提交打上（HEAD）"v1.0"的标签。

-a 选项意为"创建一个带注解的标签"。 不用 -a 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解。 我推荐一直创建带注解的标签。

$ git tag -a v1.0 


当你执行 git tag -a 命令时，Git 会打开你的编辑器，让你写一句标签注解，就像你给提交写注解一样。

现在，注意当我们执行 git log --decorate 时，我们可以看到我们的标签了

  *   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
  |\  
  | * 7774248 (change_site) changed the runoob.php
  * | c68142b 修改代码
  |/  
  * c1501a2 removed test.txt、add runoob.php
  * 3e92c19 add test.txt
  * 3b58100 第一次版本提交
  
如果我们忘了给某个提交打标签，又将它发布了，我们可以给它追加标签。

例如，假设我们发布了提交 85fc7e7(上面实例最后一行)，但是那时候忘了给它打标签。 我们现在也可以

        $ git tag -a v0.9 85fc7e7
        $ git log --oneline --decorate --graph
        *   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
        |\  
        | * 7774248 (change_site) changed the runoob.php
        * | c68142b 修改代码
        |/  
        * c1501a2 removed test.txt、add runoob.php
        * 3e92c19 add test.txt
        * 3b58100 (tag: v0.9) 第一次版本提交


如果我们要查看所有标签可以使用以下命令

        $ git tag
        v0.9
        v1.0

指定标签信息命令：
git tag -a <tagname> -m "runoob.com标签"

PGP签名标签命令
git tag -s <tagname> -m "runoob.com标签"


## git远程仓库（github）
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182017215.png)

### 添加远程库
要添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用,命令格式如下

git remote add [shortname] [url]

本例以 Github 为例作为远程仓库，如果你没有 Github 可以在官网 https://github.com/注册。

由于你的本地 Git 仓库和 GitHub 仓库之间的传输是通过SSH加密的，所以我们需要配置验证信息：

使用以下命令生成 SSH Key：

后面的 your_email@youremail.com 改为你在 Github 上注册的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。

成功的话会在 ~/ 下生成 .ssh 文件夹，进去，打开 id_rsa.pub，复制里面的 key。

        $ ssh-keygen -t rsa -C "429240967@qq.com"
        Generating public/private rsa key pair.
        Enter file in which to save the key (/Users/tianqixin/.ssh/id_rsa): 
        Enter passphrase (empty for no passphrase):    # 直接回车
        Enter same passphrase again:                   # 直接回车
        Your identification has been saved in /Users/tianqixin/.ssh/id_rsa.
        Your public key has been saved in /Users/tianqixin/.ssh/id_rsa.pub.
        The key fingerprint is:
        SHA256:MDKVidPTDXIQoJwoqUmI4LBAsg5XByBlrOEzkxrwARI 429240967@qq.com
        The key's randomart image is:
        +---[RSA 3072]----+
        |E*+.+=**oo       |
        |%Oo+oo=o. .      |
        |%**.o.o.         |
        |OO.  o o         |
        |+o+     S        |
        |.                |
        |                 |
        |                 |
        |                 |
        +----[SHA256]-----+

回到 github 上，进入 Account => Settings（账户配置）

左边选择 SSH and GPG keys，然后点击 New SSH key 按钮,title 设置标题，可以随便填，粘贴在你电脑上生成的 key。

为了验证是否成功，输入以下命令：

        $ ssh -T git@github.com
        The authenticity of host 'github.com (52.74.223.119)' can't be established.
        RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
        Are you sure you want to continue connecting (yes/no/[fingerprint])? yes                   # 输入 yes
        Warning: Permanently added 'github.com,52.74.223.119' (RSA) to the list of known hosts.
        Hi tianqixin! You've successfully authenticated, but GitHub does not provide shell access. # 成功信息

以下命令说明我们已成功连上 Github。

之后登录后点击" New repository " 

之后在在Repository name 填入 runoob-git-test(远程仓库名) ，其他保持默认设置，点击"Create repository"按钮，就成功地创建了一个新的Git仓库

#### 查看当前的远程库
git remote

        $ git remote
        origin
        $ git remote -v
        origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
        origin    git@github.com:tianqixin/runoob-git-test.git (push)

#### 提取远程仓库

Git 有两个命令用来提取远程仓库的更新。

1、从远程仓库下载新分支与数据

git fetch

该命令执行完后需要执行 git merge 远程分支到你所在的分支。

2、从远端仓库提取数据并尝试合并到当前分支：

git merge

该命令就是在执行 git fetch 之后紧接着执行 git merge 远程分支到你所在的任意分支

![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182024856.png)

#### 推送到远程仓库

推送你的新分支与数据到某个远端仓库命令:

git push [alias] [branch]

以上命令将你的 [branch] 分支推送成为 [alias] 远程仓库上的 [branch] 分支，实例如下。

$ touch runoob-test.txt      # 添加文件
$ git add runoob-test.txt 
$ git commit -m "添加到远程"
master 69e702d] 添加到远程
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 runoob-test.txt

$ git push origin master    # 推送到 Github

#### 删除远程仓库

git remote rm [别名]

## git服务其搭建（暂时不搞）

*以上文档资料来自菜鸟教程，本人只是学习并总结借鉴*

*最后,德狗镇楼*
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182029744.jpg)