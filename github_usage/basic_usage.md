

## [Basic Github Usage](#basic-github-usage) 
[Basic Github Usage with VScode](#-Basic-Github-Usage-with-VScode)
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
