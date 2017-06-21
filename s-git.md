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
   
   
   
   
   
   
