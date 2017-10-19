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

    drop database if exists dbname;

7、 创建数据库dbname

    create database dbname;

8、 删除数据库dbname

    drop database dbname;

9、 使用数据库dbname

    use dbname;

10、 显示数据库中的表

    show tables;


11、 创建新表tabname

```sql
create table tab_name(
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

13、 











