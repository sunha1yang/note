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
    DROP TABLE IF EXISTS tb_name;

16、 重命名表

    RENAME TABLE old_name TO new_name;
    ALTER TABLE old_name RENAME new_name;

17、 











