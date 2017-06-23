# 知识点
## MYSQL背景介绍
  MySQL是一个关系型数据库管理系统，由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL是最好的 RDMS (Relational Database Management System，关系数据库管理系统) 应用软件。 MySQL是一种关系数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。 MySQL所使用的 SQL 语言是用于访问数据库的最常用标准化语言。MySQL 软件采用了双授权政策，分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，一般中小型网站的开发都选择 MySQL 作为网站数据库。
## 特点
  - MySQL是开源的，所以你不需要支付额外的费用。
  - MySQL支持大型的数据库。可以处理拥有上千万条记录的大型数据
  - MySQL使用标准的SQL数据语言形式。
  - MySQL可以允许于多个系统上，并且支持多种语言。这些编程语言包括C、C++、Python、Java、Perl、PHP、Eiffel、Ruby和Tcl等
  - MySQL支持大型数据库，支持5000万条记录的数据仓库，32位系统表文件最大可支持4GB，64位系统支持最大的表文件为8TB。
  - MySQL是可以定制的，采用了GPL协议，你可以修改源码来开发自己的MySQL系统。

## ubuntu安装MYSQL
  - sudo apt-get update 更新源 在更新源之前先要
    1. sudo vim /etc/apt/sources.list   用vim打开源列表文件建其内容删除
    1. 将下列的源粘贴到源列表里
    
        deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
        deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
        deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
        deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
      
        `##测试版源`
      
       deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
      
        `# 源码`
      
       deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
       deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
       deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
        deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
      
        `##测试版源`
      
        deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
      
       `# Canonical 合作伙伴和附加`
      
        deb http://archive.canonical.com/ubuntu/ xenial partner
        deb http://extras.ubuntu.com/ubuntu/ xenial main
  - sudo apt-get install mysql-client mysql-server 安装mysql服务器和客户端
  - sudo /etc/init.d/mysqld start 启动mysql服务

## workbench安装

  - sudo apt-get install mysql-workbench
## MYSQL命令行操作
### 连接MSQL格式
  - 连接到本机上的MYSQL
  
      `mysql -u root -p`
  - 连接到远程主机上的MYSQL
  
      `假设远程主机的IP为：110.110.110.110，用户名为root,密码为abcd123。则键入以下命令： mysql -h110.110.1`
### 退出命令
  exit(回车)  或者 quit(回车)
### 修改密码
  mysqladmin -u用户名 -p旧密码 password 新密码
### 支持中文
  - 在每次创建表的时候都在最后加上 character set = utf8 就可以很好的支持中文
  - alter table information convert to character set utf8;（以创建了一个不支持中文的table时）

### 特殊的SELECT命令
  - 显示MYSQL的版本   mysql> select version();
  - 显示当前时间      mysql> select now();
  - 显示年月日        SELECT DAYOFMONTH(CURRENT_DATE);
  - 显示字符串        mysql> SELECT "welecome to my blog!";
  - 当计算器用        mysql> select ((4 _4) / 10 ) + 25;
  - 串接字符串        mysql> select CONCAT(f_name, " ", l_name) AS Name from employee_data where title = 'Marketing Executive';
      
## Apache安装
  - sudo apt-get update
  - sudo apt-get install tasksel
  - sudo tasksel
## CGI
  CGI(Common Gateway Interface) 是WWW技术中最重要的技术之一，有着不可替代的重要地位。CGI是外部应用程序（CGI程序）与WEB服务器之间的接口标准，是在CGI程序和Web服务器之间传递信息的过程。CGI规范允许Web服务器执行外部程序，并将它们的输出发送给Web浏览器，CGI将Web的一组简单的静态超媒体文档变成一个完整的新的交互式媒体。
## Apache开启CGI
  - 需要在Apache中开启cgi支持
  
      sudo ln -s /etc/apache2/mods-available/cgi.load /etc/apache2/mods-enabled/cgi.load
  - 需要重启apache服务器
  
      service apache2 restart
  - 需要运行的cgi文件的存放路径为:
  
      /usr/lib/cgi-bin
  - 改完目录的权限, 方便对目录下的文件写.
  
      sudo mkdir /usr/lib/cgi-bin/sx
      
      sudo chmod 777 /usr/lib/cgi-bin/sx
## 安装mysql的C语言库

## MYSQL接口介绍
## CCGI 基本使用
## atom的安装以及使用
## Atom editor 开环境使用的插件
## atom中c的编译
