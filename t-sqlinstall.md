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
## MYSQL命令行操作
### 连接MSQL格式
### 退出命令
### 修改密码
### 支持中文
### 特殊的SELECT命令
## Apache安装
## Apache开启CGI
## 安装mysql的C语言库
## MYSQL接口介绍
## CCGI 基本使用
## atom的安装以及使用
## Atom editor 开环境使用的插件
## atom中c的编译
