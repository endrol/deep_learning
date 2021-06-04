# Git and Github
[Basic Github Usage](#Basic-Github-Usage)

[Something about Git](#Something-about-Git)

## Basic Github Usage
这里有一篇关于[github的讲解](https://backlog.com/git-tutorial/cn/intro/intro1_1.html)，图文并茂,虽然都是命令行，但是对应的操作基本在vscode能找到. 这里更加推荐这篇中文的[github docs](https://docs.github.com/cn/github/getting-started-with-github/getting-started-with-git/ignoring-files), 不仅是中文，而且也有从简单到深入git使用技巧。

[Basic Github Usage with VScode](#Basic-Github-Usage-with-VScode)  
[切换branch](#切换branch)
## Basic Github Usage with VScode

github可以让你管理项目,在引用别人的代码的时候也更加方便，同时如果你熟悉git，可以在**命令行**看到改动的地方，github repo页面也一直是能直观看到代码改动的地方。

### 一些术语
我们先提前规定一些说法，在之后的使用过程中主要用这些英文术语而不是其他的说法，能够更准确表达。
* repo - Repositories, 项目
* branch - branches, repo的不同分支，用于部署不同的功能和版本控制
* fork - 功能类似于branch，是你没有权限在其他人repo更改时的版本控制选择
* clone - 下载
* change, stash change, commit, push - 一系列操作，分别为修改，保存修改，准备上传修改（需要添加说明），上传
* pull - 同步此时github上的repo，**注意**：你需要清空change，否则会有冲突
* pull request - branches之间的合并，暂时用不到

### 利用VScode进行简单的项目管理
不管你是从头部署一个repo，还是加入已经有的代码，如果你要在你自己的github repos上见到，你都需要以下操作
1. create a repo. add a Readme and a gitignore file. 在VScode上的 **Source Control** 找到该repo，同步branch，同步键在commit 左边
2. git clone this repo in a folder A. 现在 *A* 是你的repo地址
    - 请记住这点，git会在你的本地repo中创建一个 **.git** 文件夹，该文件夹是平时隐藏的，这个文件夹是和远程仓库对应的， 一个 **.git** 对应一个repo。任何有关**git**的设置都可以认为在该文件夹下，作为用户来说，无需操心git有什么操作
3. 添加项目文件到 *A* 中
4. 上传到github
    - 选择changes文件， 选择一些值得上传的，模型等其他资源文件可以放在**google-drive**上，适当使用*git ignore* 来过滤一些你不想push的文件类型
    - stash changes and add commit information, 添加commit
    - push 到github

之后你就可以在github管理该项目了

### 切换branch  

branch可以作为github版本控制的利器，值得频繁使用。同样的[讲解](https://backlog.com/git-tutorial/cn/stepup/stepup1_1.html)可以让你更加理解branch
### 新增一个branch
你可以使用git 命令进行操作，在vscode里，在 **Source control**中选择当前branch name, 当鼠标在上面悬浮几秒，你应该可以看到 **checkout branch/ tag...**，click一下，选择branch,或者创建new branch

| |
|-|
<img src="./images/gitlogo.png" width=350>

## Something about Git
>Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

All tutorial and API detail can be found in [API](https://git-scm.com/docs) and [Github_Doc](https://docs.github.com/en/github/getting-started-with-github/quickstart). They have full and intutive insigt about **Git**.

[Before start](#Before-start)  
[Remote and local, Github and local Git](#Remote-and-local,-Github-and-local-Git)  
[Commits](#Commits)  
[Reset and Revert Git commit](#Reset-and-Revert-Git-commit)  
[Git Rebase](#Git-Rebase)  
[Errors and solutions](#Errors-and-solutions)

### Before start
* It is better to use `ssh` instead of `http` for cloning repo. Otherwise Git will always ask you about the id and password. See this [answer](https://docs.github.com/en/github/getting-started-with-github/getting-started-with-git/why-is-git-always-asking-for-my-password) for detail. 

* Generate ssh-key and store that key in github setting. This create a constant bond between your PC and github page. Please follow [this link](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to add ssh-key.

### Remote and local, Github and local Git
First let's clear some common sense. **Remote** means the github page that's on the cloud. In some tutorial you may see **upstream**, in this case, your local project repo is **downstream** and files flow from upsteam to downstream. *Make sense, right?*

In this [tutorial](https://docs.github.com/en/github/getting-started-with-github/getting-started-with-git/managing-remote-repositories) you shall learn how to add remote and managing them.

Here are some simple CLI for easy-using.
* `git remote add original [URL]`: link local repository to remote.
* `git remote -v`: check remote information
* Just keep in mind. `git clone`, `git fetch`, `git pull`, `git push` are CLI in remote usage.


### Commits
Probably is the most important conception in Git. Every item that Git/Github store is a commit information.

Detail information can be found in [Git_API_Commit](https://git-scm.com/docs/git-commit). Here are some simple usage that might be useful.
* `-a`: enable `git add` in `-a`, often used like this `-am`
* `-m`: message
* `--amend`: replace the last commit. Very useful

#### For commit log information
`git log [-p]` gives commit logs. `-p` shows diff information. Or you can use `git show COMMIT_ID` to see difference in a commit.

#### For current un-commit changes
`git status` gives a quick look at the work un-commited right now.

### Reset and Revert Git commit
There are times that you want go back to previous work. You can use `git reset` or `git revert` to do that. See [Git_Reset_API](https://git-scm.com/docs/git-reset) for detail.

Here is a [Git_Answer](https://blog.csdn.net/yxlshk/article/details/79944535) shows their difference and examples how an when we do this stuff.
* `git reset --hard COMMIT_ID`: lose modification since COMMIT_ID
* `git reset --soft HEAD~1`: uncommit last one but save what has been modified.
* `git revert -n COMMIT_ID`: re-do that COMMIT_ID but save the later commits since COMMIT_ID. (Can be conflicat)

### Git Rebase
Rebase is a high level operation. 
>The `git rebase` command allows you to easily change a series of commits, modifying the history of your repository. You can reorder, edit, or squash commits together.
Here is a [Rebase_tutorial](http://jartto.wang/2018/12/11/git-rebase/) explain what it is with examples. 

Basically `git rebase` has two scenrios.
* Merge multiple unnecessary commits.  
``git rebase -i HEAD~4`` merges 4 latest commits
* Merge branches.  
``git reabse BRANCH_NAME``

### Errors and solutions
* `Git Push Error: insufficient permission for adding an object to repository database`, see this [answer](https://stackoverflow.com/questions/6448242/git-push-error-insufficient-permission-for-adding-an-object-to-repository-datab)
