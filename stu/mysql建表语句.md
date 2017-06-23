# 建表语句
## 学校表
   create table School(scm varchar(32)  primary key,scname varchar(32) not null,location varchar(32),president varchar(32),fl varchar(8)) character set = utf8;
## 学院表
   create table academy(acno varchar(32)  primary key,acname varchar(32) nou null,sdept varchar(32),fl varchar(8))character set = utf8;
## 学生表   
   create table student(sno varchar(32)  primary key,sname varchar(32) not null,sage varchar(32) check(sage between 1 and 120),ssex varchar(32) check(ssex in ('男' ,'女')),location varchar(32),tel varchar(32),acno varchar(32),scm varchar(32),fl varchar(8),foreign key (acno) references academy(acno),foreign key (scm) references School(scm))character set = utf8;
## 课程表
   create table course(cno varchar(32)  primary key,cname varchar(32) not null,credit varchar(32) check(credit between 1 and 5),acno varchar(32),fl varchar(8),foreign key (acno) references academy(acno))character set = utf8;
## 成绩表
   create table score(cno varchar(32) ,sno varchar(32),score varchar(16) check(score between 0 and 100),fl varchar(8),primary key(cno,sno), foreign key (cno) references course(cno),foreign key (sno) references student(sno))character set = utf8;
## 教师表
   create table teacher(tno varchar(32)  primary key,tname varchar(32) not null,tage varchar(32) check(tage between 1 and 120),tsex varchar(32) check(tsex in ('男' ,'女')),location varchar(32),tel varchar(32),acno varchar(32),scm varchar(32),fl varchar(8),foreign key (acno) references academy(acno),foreign key (scm) references School(scm))character set = utf8;
## 教师与课程连接表
   create table tc(cno varchar(32) ,tno varchar(32),fl varchar(8),primary key(cno,tno), foreign key (cno) references course(cno),foreign key (tno) references teacher(tno))character set = utf8;
## 用户表
### 学生用户
   create table suser(sno varchar(32) primary key, password varchar(32) not null ,fl varchar(8),foreign key (sno) references student(sno))character set = utf8;
### 教师用户
   create table tuser(tno varchar(32) primary key, password varchar(32) not null ,fl varchar(8),foreign key (tno) references teacher(tno))character set = utf8;
## 视图
   - 只能在数据库内建，不能在c中建
   - use  st;  create view viewts  asselect score.sno,sname,acno,score,cno  from  score,student  where student.sno=score.sno ;
