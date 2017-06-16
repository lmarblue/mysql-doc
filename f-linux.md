# 知识点
  * Linux历史
  * 人物介绍  
  * Linux安装
  * Linux命令
  * Vmware tools安装
  * Linux下vim安装
  * vim的配置
## 主要的内容
### Linux历史
  ![Image of Yaktocat]( https://nts.newbieol.com/static/k6/mySQL/class-001/img/Unix_timeline.png)
#### Linux
&ensp;&ensp;在1991年，林纳斯·托瓦兹开始在MINIX上开发Linux内核，为MINIX写的软件也可以在Linux内核上使用。后来使用GNU软件代替MINIX的软件，因为使用从GNU系统来的源代码可以自由使用，这对Linux的发展是有益。使用GNU GPL协议的源代码可以被其他项目所使用，只要这些项目使用同样的协议发布。为了让Linux可以在商业上使用，林纳斯·托瓦兹决定更改他原来的协议（这个协议会限制商业使用），以GNU GPL协议来代替。之后许多开发者致力融合GNU元素到Linux中，做出一个有完整功能的、自由的操作系统。

&ensp;&ensp;Linux的第一个版本在1991年9月被大学FTP server管理员Ari Lemmke发布在Internet上，最初Torvalds称这个内核的名称为“Freax”，意思是自由（“free”）和奇异（“freak”）的结合字，并且附上“X”这个常用的字母，以配合所谓的类Unix的系统。但是FTP服务器管理员嫌原来的命名“Freax”的名称不好听，把内核的称呼改成“Linux”，当时仅有10000行程序码，仍必须运行于Minix操作系统之上，并且必须使用硬盘开机；随后在10月份第二个版本（0.02版）发布，同时这位芬兰赫尔辛基的大学生在comp.os.minix上发布一则消息

&ensp;&ensp;Hello everybody out there using minix- I’m doing a (free) operation system (just a hobby, won’t be big and professional like gnu) for 386(486) AT clones.

&ensp;&ensp;1994年3月，Linux1.0版正式发布，Marc Ewing成立Red Hat软件公司，成为最著名的Linux经销商之一。

&ensp;&ensp;Unix & Linux历史源流

&ensp;&ensp;早期Linux的开机管理程序（boot loader）使用LILO（Linux Loader），早期的LILO存在着一些难以容忍的缺陷，例如无法识别1024柱面以后的硬盘空间，后来的GRUB（GRand Unified Bootloader）克服这些缺点，具有‘动态搜索内核文件’的功能，可以让用户在开机的时候，自行编辑开机设置系统文件，通过ext2或ext3文件系统中加载Linux Kernel（GRUB通过不同的文件系统驱动可以识别几乎所有Linux支持的文件系统，因此可以使用很多文件系统来格式化内核文件所在的扇区，并不局限于ext文件系统）。

&ensp;&ensp;Linux的标志和吉祥物是一只名字叫做Tux的企鹅，标志的由来是因为Linus在澳洲时曾被一只动物园里的企鹅咬了一口，便选择企鹅作为Linux的标志。更容易被接受的说法是：企鹅代表南极，而南极又是全世界所共有的一块陆地。这也就代表Linux是所有人的Linux。    
#### ubuntu Linux
Ubuntu(自非洲南部祖鲁语或科萨语的“ubuntu”一词,译为乌班图. 意思是“施人人道”、“乐于分享”)由马克·舍特尔沃斯创立，其首个版本—4.10发布于2004年10月20日，它以Debian为开发蓝本。与Debian稳健的升级策略不同，Ubuntu每六个月便会发布一个新版，以便人们即时地获取和使用新软件。Ubuntu的开发目的是为了使个人电脑变得简单易用，同时也提供针对企业应用的服务器版本。Ubuntu的每个新版本均会包含当时最新的GNOME桌面环境，通常在GNOME发布新版本后一个月内发行。

  ![Image of Yaktocat](https://nts.newbieol.com/static/k6/mySQL/class-001/img/Ubuntu_17.04_English.png)
### 人物介绍
  ![Image of Yaktocat](https://nts.newbieol.com/static/k6/mySQL/class-001/img/linus.png)   
  
  Linus Torvalds：Linux之父，芬兰赫尔辛基大学
### Linux安装
#### 步骤
  1. 打开VMware Workstation（一个安装虚拟机的软件）
  1. 点击Fil下的new Virtual Machine Wizard
  1. 点击下一步之后把你Linux的镜像文件导入
  1. 之后点击下一步并设置虚拟机的空间
  1. 设置你的Linux的用户名以及密码
  1. 安装完成
### Linux命令
#### 常用命令
  1. ls     显示文件或目录
     - `-l`  列出文件详细信息l(list)
     - `-a`  列出当前目录下所有文件及目录，包括隐藏的a(all)
  1. mkdir  创建目录
      - `-p`  创建目录，若无父目录，则创建p(parent)     
  1. cd     切换目录   
  1. touch  创建空文件  
  1. echo   创建带有内容的文件。
  1. cat    查看文件内容
  1. cp     拷贝  
  1. mv     移动或重命名  
  1. rm     删除文件
      - `-r`  递归删除，可删除子目录及文件
       - `-f`  强制删除
  1. find   在文件系统中搜索某文件
  1. wc     统计文本中行数、字数、字符数  
  1. grep   在文本文件中查找某个字符串
  1. rmdir  删除空目录
  1. tree   树形结构显示目录，需要安装tree包
  1. pwd    显示当前目录  
  1. ln     创建链接文件   
  1. more、less   分页显示文本文件内容
  1. head、tail   显示文件头、尾内容  
  1. ctrl+alt+F1  命令行全屏模式
#### 打包压缩相关命令
  1. gzip：
  1. bzip2：
  1. tar:     打包压缩
      - `-c`  归档文件  tar  -cvf
       - `-x` 压缩文件
       - `-z` gzip压缩文件  tar  -zcvf
       - `-j` bzip2压缩文件 tar  -jcvf
       - `-v` 显示压缩或解压缩过程 v(view)
       - `-f` 使用档名
#### 关机/重启机器
  1. shutdown
      - `-r`  关机重启
      - `-h`  关机不重启
      - now     立刻关机
  1. halt        关机  
  1. reboot      重启
### Vmware tools安装
  1. 在虚拟机右下角点击CD/DVD2,再点击setting将linux.iso导入进来
  1. 将VMwareTools-9.2.0-799703.tar.gz复制到根目录下,如下操作可实现此操作
     - cd /media/
     - cd linux/
     - cd VMware\ Tools
     - ls
     - cp VMwareTools-9.2.0-799703.tar.gz ~l
     - cd
     - ls
  1. tar xvf VMwareTools-9.2.0-799703.tar.gz 将VMwareTools-9.2.0-799703.tar.gz解压缩 
  1. cd Vmware-tools-distrib/
  1. sudo ./....  执行.....文件集安装完成。



   







  
  
  
