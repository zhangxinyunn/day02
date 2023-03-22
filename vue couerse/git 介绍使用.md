### 下载安装git 官网git.www.com

终端测试是否安装成功 git -v 回车

（新建一个新的文件夹）使用git 需要

### 配置 name emall 

​    name 终端输入 git config --global user.name '这里面写自己的名字 或公司里面的英文名 （方便查找）'
​    emall    终端输入git config --global user.emall '邮件箱号'

### 使用git：

```
 git status
        -查看当前仓库状态
```

​    git init
​        -初始化仓库（显示开发者公司不用）

```
    git init
        -初始化仓库（显示开发者公司不用）
```

刚刚添加到项目中的文件处于未跟踪状态
    未跟踪 --》暂存 

```
 git add <需要暂存的文件名称>  将文件切换到暂存的状态
        git add * 将所有已修改（未跟踪）的文件暂存
```

###     暂存 --》未修改

​    

```
 git commit -m '提交的这个文件是干嘛的 跟上提交的文件名'将暂存的文件存储到仓库中
        git commit -a -m '提交的这个文件是干嘛的 跟上提交的文件名' 提交所有已修改的文件（未跟踪的文件不会提交）
```

###     未修改 --》修改

    总结 需要修改后都需要暂存 然后再是未修改 再到 修改

常用的命令 (filename：文件名)

### 1.重置文件 ：

```
	git restore <filename>  恢复文件

	git restore --staged <filename> 暂存状态取消
```

### 2.删除文件：

​	

```
git rm <filename> 删除文件

git rm<filename> -f  强制删除
```

### 3.移动文件：

```
	gie mv from to 移动文件  重命名操作
```

### 分支

git在存储文件时，每一次代码的提交都会创建一个与之对应的节点，git就是通过一个个的节点来记录代码的状态，节点会构成一个树状结构，树状结构就是意味这个树会分叉，默认情况下仓库只有一个分支，命名为master。在使用git时，可以创建多个分支与分支之间相互独立，在一个分支上修改代码不会影响其它的分支。

​	

```
git branch  查看分支
```

```
git branch  -c <branch name> 创建新的分支（branch name  表示要创建的分支名）

git branch -d <branch name>  删除分支

git switch <branch name>  切换分支

git switch -c <branch name>  创建并切换分支
git merge <branch name> 合并分支
```



在开发中，我们都是在自己的分支上编辑代码，代码编写完成后，再将自己的分支合并到主分支中。

### 变基（rebase）

在开发中除了通过merge来合并分支外，我们可以通过变基来完成分支合并。

我们通过merge合并分支时，在提交记录中会将所有的分支创建和分支合并的过程中全部显示出来，这样当项目比较复杂，开发过程比较波折时，我们必须要反复创建、合并、删除分支，这样一来将使得我们代码提交记录变得极为混乱。

原理（变基时发生了什么）

​	1.当我们发生变基时，git会首先找到两条分支最近的共同祖先

​	2.对比当前分支相对于祖先的历史提交，并且将他们提取出来存到一个临时文件中。

​	3.将当前部分的部分指向目标基地。

​	4.以当前基地开始，重新执行历史操作

变基和merge对于合并来说最终的结果是一样的，但是变基后会使得我们提交的代码记录更整洁更清晰，大部分情况下合并和变基是可以互换的，但是如果分支已提交给了远程仓库，那么这时尽量不要使用变基

### 远程仓库（rebase）

目前我对于git所以操作都是在本地进行的，在开发中显然不能这样的，这时我们就需要一个远程git仓库，远程仓库和本地仓库的本质没什么区别，不同点在于远程仓库可以被多人同时访问使用，方便我们协同开发。在实际开发中，git的服务器通常中公司内部搭建内部使用或者购买一些公共的私有git服务器，我们学习阶段，直接使用一些开放公共git仓库。目前我们常用的库有两个：GitHub和Gitee（码云）

https://github.com/（手机备忘录有操作步骤）

将本地库上传git：

下面这些代码在网站上生成复制来的

```bash
git remote add origin https://github.com/zhangxinyunn/git-demo.git
# git remote add <remote name> <url>  (remote name:仓库名称) （路径）

git branch -M main
# 修改分支名字为 main

git push -u origin main
#git push 将代码上传服务器上
```

将本地库上传gitee：

```bash
git remote add gitee https://gitee.com/urban-migrant-workers/git-demo.git
git push -u origin main
```

### 远程库的操作命令

```bash
git remote #列出当前的关联的远程库
git remote add <远程库名><url> #关联远程库
git remote remove <远程库名> #删除远程库
git push -u <远程库名><分支> #向远程库推送代码，并和当前分支关联
git clone <url> #从远程库下载代码

git push #如果本地的版本低于远程库，push默认是推不上去
git fatch #要想推送成功，必须先确保本地库和远程库的版本一致，fetch它会从远程仓库下载所有代码，但是它不会		  将代码和当前分支自动合并
		  #使用fetch拉去代码后，必须手动对代码进行合并
git pull #从服务器上拉取代码并自动合并
```

