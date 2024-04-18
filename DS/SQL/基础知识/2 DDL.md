DDL（Data Definition Language），数据定义语言，用于定义数据库对象，如数据库，表，字段
# 2.1 数据库的操作
## 查询
```SQL
SHOW DATABASES;
#查询所有数据库；注意分号

SELECT DATABASE();
#查询当前数据库
```
## 创建
```SQL
CREATE DATABASE[IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];
#框框[]内的参数皆为可选参数，实际输入指令是不带[]的，这里只是为了标注
#若名字不存在则创建数据库；字符集如utf8支持最多三字节字符，utf8mb4支持四字节字符

CREATE DATABASE 数据库名;
#这样就是最简单的创建方法
```
## 删除
```SQL
DROP DATABASE IF EXIST 数据库名;
#若数据库名存在，进行删除
```
## 使用
```SQL
USE 数据库名;
#即切换到这个数据库，以便对此数据库进行操作，和conda activate env_name的作用类似

SELECT DATABASE();
#查询当前数据库的名字
```
# 2.2 表的操作
## 粗浅的查询
```SQL
SHOW TABLES;
#查看当前数据库所有的表

DESC 表的名字;
#查询表的结构

SHOW CREATE TABLE 表的名字; 
#查询指定表的建表语句
```
## 创建
```SQL
CREATE TABLE 表的名字
(
	表列字段1 数据类型1 长度 是否可为空 约束规则, #注意逗号
	表列字段2 数据类型2 长度 是否可为空 约束规则,
	表列字段3 数据类型3 长度 是否可为空 约束规则,
	表列字段4 数据类型4 长度 是否可为空 约束规则  #注意没有逗号
)COMMENT '表的注释';

#示例，创建班级花名册表
CREATE TABLE class_info
(
	num INT NOT NULL PRIMARY KEY,
	#还可以在这里后方加上comment'注释内容'
	st_num VARCHAR(64) NOT NULL,
	#VARCHAR是字符串的意思
	name VARCHAR(64) NOT NULL,
	class VARCHAR(64) NOT NULL
)character set utf8 collate utf8_general_ci;

#查询表的结构
DESC 表的名字;

#查询指定表的建表语句，即展示包括上述建表语句的详细信息
SHOW CREATE TABLE 表的名字; 
```
## 插入数据
```SQL
#插入数据命令为
INSERT INTO table_name ( field1, field2,...fieldN ) VALUES ( value1, value2,...valueN );

#代码示例
INSERT INTO class_info ( num, st_num,name, class) VALUES ( 1, '123456','张三','4班' );
```
## 更详细的查询
```SQL
#查询表数据结构
SELECT column_name,column_name FROM table_name [WHERE Clause] [LIMIT N][ OFFSET M]

#示例代码
select * from class_info;
```
## 删除
```SQL
#删除数据
DELETE FROM table_name WHERE condition;

#示例代码
DELETE FROM class_info WHERE num = 1;
```