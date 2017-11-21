### 常用MySQL语法

1、 启动MySQL服务器：

    net start mysql;

2、 关闭MySQL服务器

    net stop mysql;

3、 进入

    mysql -h 主机地址 -u 用户名 －p 用户密码;

4、 退出

    exit;

5、显示数据库

    show databases;

6、 判断是否存在数据库dbname存在，存在就删除

    drop database if exists db_name;

7、 创建数据库db_name

    create database db_name;

8、 删除数据库db_name

    drop database db_name;

9、 使用数据库db_name

    use db_name;

10、 显示数据库中的表

    show tables;


11、 创建新表tb_name

```sql
create table tb_name(
    id TINYINT UNSIGNED NOT NULL AUTO_INCREMENT,　　　// id值。无符号、非空、递增——唯一性，可做主键

    name VARCHAR(60) NOT NULL COMMENT '用户姓名',     // COMMENT 添加注释

    score TINYINT UNSIGNED NOT NULL DEFAULT 0,　　　　// 设置默认列值
    
    created_at timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,  // CURRENT_TIMESTAMP 当前时间戳

    PRIMARY KEY(id)      // 主键

    )ENGINE=InnoDB　　　　// 设置表的存储引擎，一般常用InnoDB和MyISAM；InnoDB可靠，支持事务；MyISAM高效不支持全文检索

    DEFAULT charset=utf8　　// 设置默认的编码，防止数据库中文乱码

    COMMENT='xxx表';  // 表注释

```


12、 复制表

    CREATE TABLE tb_name2 SELECT * FROM tb_name;
    CREATE TABLE tb_name2 SELECT id,name FROM tb_name; // 复制表部分内容（id,name）

13、 创建临时表

    CREATE TEMPORARY TABLE tb_name


14、 查看表的信息

    DESCRIBE tb_name;
    SHOW COLUMNS in/from tb_name;

15、 删除表

    DROP [ TEMPORARY ] TABLE [ IF EXISTS ] tb_name[ ,tb_name2.......];

16、 重命名表

    RENAME TABLE old_name TO new_name;
    ALTER TABLE old_name RENAME new_name;

17、 增加一个列

    Alter table tabname add column col type
    注：列增加后将不能删除。DB2中列加上后数据类型也不能改变，唯一能改变的是增加varchar类型的长度。




#### 常用语句
1、创建数据库
CREATE DATABASE database-name

2、删除数据库
drop database dbname

3、备份sql server
--- 创建 备份数据的 device
USE master
EXEC sp_addumpdevice 'disk', 'testBack', 'c:\mssql7backup\MyNwind_1.dat'
--- 开始 备份
BACKUP DATABASE pubs TO testBack

4、创建新表
create table tabname(col1 type1 [not null] [primary key],col2 type2 [not null],..)

根据已有的表创建新表：
A：create table tab_new like tab_old (使用旧表创建新表)
B：create table tab_new as select col1,col2… from tab_old definition only

5、删除新表
drop table tabname

6、增加一个列
Alter table tabname add column col type
注：列增加后将不能删除。DB2中列加上后数据类型也不能改变，唯一能改变的是增加varchar类型的长度。

7、添加主键： Alter table tabname add primary key(col)
删除主键： Alter table tabname drop primary key(col)

8、创建索引：create [unique] index idxname on tabname(col….)
删除索引：drop index idxname
注：索引是不可更改的，想更改必须删除重新建。

9、创建视图：create view viewname as select statement
删除视图：drop view viewname

10、几个简单的基本的sql语句
选择：select * from table1 where 范围
插入：insert into table1(field1,field2) values(value1,value2)
删除：delete from table1 where 范围
更新：update table1 set field1=value1 where 范围
查找：select * from table1 where field1 like ’%value1%’ ---like的语法很精妙，查资料!
排序：select * from table1 order by field1,field2 [desc]
总数：select count as totalcount from table1
求和：select sum(field1) as sumvalue from table1
平均：select avg(field1) as avgvalue from table1
最大：select max(field1) as maxvalue from table1
最小：select min(field1) as minvalue from table1











