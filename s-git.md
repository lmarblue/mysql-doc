# git源码管理
- git简介
- git的安装
- 使用git配置vim
- git基本命令
- GitHub的基本使用
- MarkDown
## 主要内容
### git简介
  1. 关于git  
  
      GIT 是一个分布式版本控制软件，最初由林纳斯·托瓦兹（Linus Torvalds）创作，于2005年以GPL发布。最初目的是为更好地管理Linux内核开发而设计。是目前世界上最先进的分布式版本控制系统.
  1. git诞生   
      很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。   
      Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？  
      事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！  
      你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符  。不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。  
      安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。  
      Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：   
      Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。  
      Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。  
      历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。  
### git安装
  sudo apt-get install git
### 使用git配置vim
#### 步骤
   1. git clone http://github.com/wangleihd/software.git  将software克隆过来
   1. cd sofetware/  切到software目录下
   1. cat software.sh  查看software.sh
   1. sudo ./install.sh  执行install.sh
   1. ./software.sh 执行software.sh
#### 安装中文输入法
   1. 完成上面的配置
   
   1. 点击设置中的language并打开 
   
   1. 点击install/remove language 选择Chinese并进行安装
   
   1. 安装好后text entry 添加english(US)以及chinese(pinyin)
   
   1. 重启虚拟机 sudo reboot
### git基本命令

  git help <command> # 显示command的help

  git show # 显示某次提交的内容 git show $id

  git add . # 将所有修改过的工作文件提交暂存区

  git rm <file> # 从版本库中删除文件

  git rm <file> --cached # 从版本库中删除文件，但不删除文件

  git reset <file> # 从暂存区恢复到工作文件

  git reset -- . # 从暂存区恢复到工作文件

  git reset --hard # 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改

  git revert <$id> # 恢复某次提交的状态，恢复动作本身也创建次提交对象

  git revert HEAD # 恢复最后一次提交的状态

  - 查看文件diff

  git diff <file> # 比较当前文件和暂存区文件差异 git diff

  git diff <id1><id1><id2> # 比较两次提交之间的差异

  git diff <branch1>..<branch2> # 在两个分支之间比较

  git diff --staged # 比较暂存区和版本库差异
  
  git diff --cached # 比较暂存区和版本库差异

  git diff --stat # 仅仅比较统计信息
 
  - 查看提交记录

  git log git log <file> # 查看该文件每次提交记录

  git log -p <file> # 查看每次详细修改内容的diff

  git log -p -2 # 查看最近两次详细修改内容的diff

  git log --stat #查看提交统计信息  tigMac上可以使用tig代替diff和log，brew install tig

  - Git 本地分支管理

  查看、切换、创建和删除分支

  git br -r # 查看远程分支

  git br <new_branch> # 创建新的分支

  git br -v # 查看各个分支最后提交信息
  
  git co <branch> # 切换到某个分支

  git co -b <new_branch> # 创建新的分支，并且切换过去

  git co -b <new_branch> <branch> # 基于branch创建新的new_branch

  git co $id # 把某次历史提交记录checkout出来，但无分支信息，切换到其他分支会自动删除

  git co $id -b <new_branch> # 把某次历史提交记录checkout出来，创建成一个分支

  git br -d <branch> # 删除某个分支

  git br -D <branch> # 强制删除某个分支 (未被合并的分支被删除的时候需要强制)

   分支合并和rebase

  git merge <branch> # 将branch分支合并到当前分支

  git merge origin/master --no-ff # 不要Fast-Foward合并，这样可以生成merge提交

  git rebase master <branch> # 将master rebase到branch，相当于： git co <branch> && git rebase master && git co master && git merge <branch>

  - Git补丁管理(方便在多台机器上开发同步时用)

  git diff > ../sync.patch # 生成补丁

  git apply ../sync.patch # 打补丁

  git apply --check ../sync.patch #测试补丁能否成功
 
  - Git暂存管理

  git stash # 暂存

  git stash list # 列所有stash

  git stash apply # 恢复暂存的内容

  git stash drop # 删除暂存区

  - Git远程分支管理

  git pull # 抓取远程仓库所有分支更新并合并到本地

  git pull --no-ff # 抓取远程仓库所有分支更新并合并到本地，不要快进合并

  git fetch origin # 抓取远程仓库更新

  git push # push所有分支

  git push origin master # 将本地主分支推到远程主分支

  git push -u origin master # 将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)

  git push origin <local_branch> # 创建远程分支， origin是远程仓库名

  git push origin <local_branch>:<remote_branch> # 创建远程分支

  git push origin :<remote_branch> #先删除本地分支(git br -d <branch>)，然后再push删除远程分支
 
  - Git远程仓库管理

    GitHub

  git remote -v # 查看远程服务器地址和仓库名称

  git remote show origin # 查看远程服务器仓库状态

  git remote add origin git@ github:robbin/robbin_site.git # 添加远程仓库地址

  - 创建远程仓库

  git clone --bare robbin_site robbin_site.git # 用带版本的项目创建纯版本仓库

  git remote add origin git@ github.com:robbin/robbin_site.git # 设置远程仓库地址

  git push -u origin master # 客户端首次提交

  git push -u origin develop # 首次将本地develop分支提交到远程develop分支，并且track

  git remote set-head origin master # 设置远程仓库的HEAD指向master分支

  也可以命令设置跟踪远程库和本地库

  git branch --set-upstream master origin/master

  git branch --set-upstream develop origin/develop 
### GitHub的基本使用
#### 创建一个 github仓库
  ![github仓库](https://nts.newbieol.com/static/k6/02.git-github-markdown/github/images/github-2.png)   
#### GitHub仓库的使用
  1. 当本地没有git仓库时
    echo "# abc" >> README.md   
    
    git init  
    
    git add README.md  
    
    git commit -m "first commit"  
    
    git remote add origin https://github.com/wangleihd/freeBook-H5.git  
    
    git push -u origin master  
    
  1. 当已经有仓库时
  
    git remote add origin https://github.com/wangleihd/freeBook-H5.git
    
    git push -u origin master
    
  1. 也可直接下载这个项目
  
    git clone https://github.com/wangleihd/freeBook-H5.git
    
 ![创建好了的](https://nts.newbieol.com/static/k6/02.git-github-markdown/github/images/github-3.png)

### MarkDown
#### makdown介绍
  在刚才的导语里提到，Markdown 是一种用来写作的轻量级「标记语言」，它用简洁的语法代替排版，而不像一般我们用的字处理软件 Word 或 Pages 有大量的排版、字体设置。它使我们专心于码字，用「标记」语法，来代替常见的排版格式。例如此文从内容到格式，甚至插图，键盘就可以通通搞定了。目前来看，支持 Markdown 语法的编辑器有很多，包括很多网站（例如简书）也支持了 Markdown 的文字录入。Markdown 从写作到完成，导出格式随心所欲，你可以导出 HTML 格式的文件用来网站发布，也可以十分方便的导出 PDF 格式，这种格式写出的简历更能得到 HR 的好感。甚至可以利用 CloudApp 这种云服务工具直接上传至网页用来分享你的文章，全球最大的轻博客平台 Tumblr，也支持 Mou 这类 Markdown 工具的直接上传。
### 官方文档
  [创始人 John Gruber 的 Markdown 语法说明](http://daringfireball.net/projects/markdown/syntax)
  [Markdown 中文版语法说明](http://wowubuntu.com/markdown/#list)
### 基本语法
#### 标题
  ![标题](http://ww1.sinaimg.cn/large/6aee7dbbgw1effeaclhiyj20eh09cwez.jpg)  
  
  标题是每篇文章都需要也是最常用的格式，在 Markdown 中，如果一段文字被定义为标题，只要在这段文字前加 # 号即可。
#### 列表
  ![](http://ww4.sinaimg.cn/large/6aee7dbbgw1effew5aftij20d80bz3yw.jpg)
#### 引用
  只需要在文本前加入 > 这种尖括号（大于号）即可
  ![](http://ww3.sinaimg.cn/large/6aee7dbbgw1effezhonxlj20e009c3yu.jpg)
#### 图表与链接
  图片为：`![](){ImgCap}{/ImgCap}`

  链接为：`[]()`
  
  ![](http://ww2.sinaimg.cn/large/6aee7dbbgw1efffa67voyj20ix0ctq3n.jpg)
#### 粗体与斜体

  Markdown 的粗体和斜体也非常简单，用两个 * 包含一段文本就是粗体的语法，用一个 * 包含一段文本就是斜体的语法。
#### 表格 
  `|------|-----|------|(一般为属性列，这里有三列)
   |------|-----|------|（这个是固定的，三列就是这样的||里面不写东西）
   |------|------|------|（这里是第一行）`
   
   例如：
   | Tables        | Are           | Cool  |
   | ------------- |:-------------:| -----:|
   | col 3 is      | right-aligned | $1600 |
   | col 2 is      | centered      |   $12 |
   | zebra stripes | are neat      |    $1 |
#### 代码框
  如果你是个程序猿，需要在文章里优雅的引用代码框，在 Markdown下实现也非常简单，只需要用两个esc下面的有～符号的这个键（不是～符号）把中间的代码包裹起来
 ![](http://ww3.sinaimg.cn/large/6aee7dbbgw1effg1lsa97j20lt0a8dgs.jpg)、
#### 分割线
  分割线的语法只需要三个 `* `号
  ![](http://ww3.sinaimg.cn/large/6aee7dbbgw1effgmnpgqlj210j0us44j.jpg)
   
   
  

  
  

  
  
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
