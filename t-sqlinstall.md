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

  - sudo apt-get update
  - sudo apt-get install libmysqlclient-dev

## MYSQL接口介绍
  手册：mysql Documentation
  编写：#include <mysql/mysql.h>
  编译：gcc  test.c  -o test  -lmysqlclient

  MYSQL *mysql_init(MYSQL *mysql)
  功能：初始化函数，参数为NULL即可，接收返回值。
     失败，NULL

  MYSQL *mysql_real_connect(MYSQL *mysql, const char *host, const char *user, const char *passwd, const char *db, unsigned int            port, const char *unix_socket, unsigned long client_flag)
  功能：连接mysql服务器
      失败，NULL

  void mysql_close(MYSQL *mysql)
  功能：关闭服务器连接

  int mysql_real_query(MYSQL *mysql, const char *stmt_str, unsigned long length)
  功能：执行sql语句，sql语句不能以“；”结尾
      成功，0
      失败， 非0

  int mysql_query(MYSQL *mysql, const char *stmt_str)
  功能：执行sql语句，sql语句不能以“；”结尾

  MYSQL_RES *mysql_store_result(MYSQL *mysql)
   功能：存储 mysql_query()  或者  mysql_read_query() 的数据
     失败， NULL

  MYSQL_RES *mysql_use_result(MYSQL *mysql)
  功能：接收结果，速度要比mysql_use_result()快。

    void mysql_free_result(MYSQL_RES *result)
  功能：释放空间

  my_ulonglong mysql_num_rows(MYSQL_RES *result)
  功能：返回 mysql_store_result 的记录个数

  my_ulonglong mysql_affected_rows(MYSQL *mysql)
  功能：得到执行sql语句之后改变的记录数

  const char *mysql_error(MYSQL *mysql)
  功能：返回出错提示

  MYSQL_FIELD *mysql_fetch_field(MYSQL_RES *result)
  功能：返回集合中列的定义   
  MYSQL_FIELD *field;

  while((field = mysql_fetch_field(result)))
  {
     printf("field name %s\n", field->name);
  }

  MYSQL_FIELD *mysql_fetch_fields(MYSQL_RES *result)
  功能：返回集合中列的数组
  unsigned int num_fields;
  unsigned int i;
  MYSQL_FIELD *fields;

  num_fields = mysql_num_fields(result);
  fields = mysql_fetch_fields(result);
  for(i = 0; i < num_fields; i++)
  {
    printf("Field %u is %s\n", i, fields[i].name);
  }

  unsigned int mysql_num_fields(MYSQL_RES *result)
  功能：返回集合中列的个数

  my_ulonglong mysql_num_rows(MYSQL_RES *result）
  功能：返回集合中行的个数
  MYSQL_ROW mysql_fetch_row(MYSQL_RES *result)
  功能：返回集合中的一行， 结束或者错误返回NULL

  unsigned long *mysql_fetch_lengths(MYSQL_RES *result)
  功能：返回当前行中每一个字段值的长度 数组。
## CCGI 基本使用
  - [CGIC官网链接](https://boutell.com/cgic/)
## atom的安装以及使用
## Atom editor 开环境使用的插件

   - activate-power-mode：动感插件 atl + ctrl + o :打开插件
   - vim-mode：vim模式
   - ex-mode：实现:w功能
   - monokai：高亮显示
   - atom-ternjs：JavaScript 自动补全
   - autoprefixer：给 CSS 添加适当的前缀
   - color-picker：选颜色
   - emmet：写 HTML 的神器
   - atom-beautify：美化代码，空格啊什么什么的
   - autoclose-html：HTML自动补全闭标签
   - file-icons: 增加许多图标,在侧边蓝文件名前面的icon,,很赞
   - autocomplete-modules: 自动补全插件, 有HTML, CSS, python 等
   - highlight-selected: 高亮当前所选的文字, 双击后全文这个词或变量都会变高亮.
   - Open In Browser: 右键打开浏览器.
   - atom-clock: 在bar显示 时间
   - autocomplete-js-import: 模块导入智能提示
   - autocomplete-modules: 模块智能提示【node_modules】

## atom中c的编译
