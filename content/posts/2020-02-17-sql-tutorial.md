---
title: "数据库漫游指南 - SQL"
date: 2020-02-17T22:28:47+08:00
categories: 编程之道
tags:
    - SQL
    - Database
type: "home"
toc: true
mathjax: false
codes: [sql]
comments: true
vertical: false
image: true
draft: false
---

SQL（Structured Query Language）是「结构化查询语言」，它是对关系型数据库的操作语言。它可以应用到所有关系型数据库中，例如：MySQL、Oracle、SQL Server等。它主要划分为以下几类：

- **DQL - Data Query Language**：数据查询语言，用来查询记录（数据）。<u>select</u>
- **DDL - Data Definition Language**：数据定义语言，用来定义数据库对象；<u>create/drop/alter</u>
- **DML - Data Manipulation Language**：数据操作语言，用来定义数据库记录；<u>Insert/delete/update</u>
- **DCL - Data Control Language**：数据控制语言，用来定义访问权限和安全级别；

<!--more-->

## DQL：数据查询语言

```sql
SELECT
	selection_list /*要查询的列名称*/
FROM
	table_list /*要查询的表名称*/
WHERE
	condition /*行条件*/
GROUP BY
	grouping_columns /*对结果分组*/
HAVING
	condition /*分组后的行条件*/
ORDER BY
	sorting_columns /*对结果排序*/
LIMIT
	offset_start, row_count /*结果限定*/

```

### SELECT - 选取



> **DISTINCT - 去重**
>
>



### WHERE - 筛选



> **AND & OR 运算符**
>
>



#### IN - 多值匹配

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2,...);
```

> **IN 与 = 的异同**
>
> -  相同点：均在WHERE中使用作为筛选条件之一、均是等于的含义
> -  不同点：IN可以规定多个值，等于规定一个值



#### LIKE - 字符匹配

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;
```

> 通配符：
>
> | 通配符                         | 描述                       |
> | :----------------------------- | :------------------------- |
> | %                              | 替代 0 个或多个字符        |
> | _                              | 替代一个字符               |
> | [*charlist*]                   | 字符列中的任何单一字符     |
> | [^*charlist*] 或 [!*charlist*] | 不在字符列中的任何单一字符 |



#### BETWEEN - 范围匹配

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

> **请注意，在不同的数据库中，BETWEEN 操作符会产生不同的结果！**
>
> - 在某些数据库中，BETWEEN 选取介于两个值之间但不包括两个测试值的字段。
> - 在某些数据库中，BETWEEN 选取介于两个值之间且包括两个测试值的字段。
> - 在某些数据库中，BETWEEN 选取介于两个值之间且包括第一个测试值但不包括最后一个测试值的字段。



### GROUP BY - 分组





### ORDER BY - 排序





### TOP / LIMIT / ROWNUM - 限制数目

- SQL Server / MS Access 语法

```sql
SELECT TOP number|percent column_name(s)
FROM table_name;
```

- Oracle 语法

```sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

- MySQL 语法

```sql
SELECT column_name(s)
FROM table_name
LIMIT number;
```

> 附注：**OFFSET**
>
> 为了与 PostgreSQL 兼容，MySQL 也支持句法： `LIMIT # OFFSET #`
>
> 1. selete * from testtable limit 2,1;
>
> 2. selete * from testtable limit 2 offset 1;
>
> 注意：
>
> - 数据库数据计算是从0开始的
> - offset X 是跳过 X 个数据，limit Y 是选取 Y 个数据
> - limit X, Y 中 X 表示跳过 X 个数据，读取 Y 个数据



### ---------------------------------------

### AS - 别名

- 列的 SQL 别名语法

```sql
SELECT column_name AS alias_name
FROM table_name;
```

- 表的 SQL 别名语法

```sql
SELECT column_name(s)
FROM table_name AS alias_name;
```

> **在下面的情况下，使用别名很有用：**
>
> - 在查询中涉及超过一个表
> - 在查询中使用了函数
> - 列名称很长或者可读性差
> - 需要把两个列或者多个列结合在一起



### JOIN - 多表连接

![sql-join.png](https://www.runoob.com/wp-content/uploads/2019/01/sql-join.png)

> **可以使用的不同的 SQL JOIN 类型：**
>
> - **INNER JOIN**：如果表中有至少一个匹配，则返回行
> - **LEFT JOIN**：即使右表中没有匹配，也从左表返回所有的行
> - **RIGHT JOIN**：即使左表中没有匹配，也从右表返回所有的行
> - **FULL JOIN**：只要其中一个表中存在匹配，则返回行



### AUTO INCREMENT - 自增序列





-----

## DML：数据操作语言

### INSERT INTO - 插入纪录





### UPDATE - 更新记录





### DELETE - 删除记录









-----

## DDL：数据定义语言

### CREATE DATABASE - 创建数据库





### CREATE TABLE - 创建数据表



> **约束：**
>
>



> **数据类型：**https://www.runoob.com/sql/sql-datatypes.html



### CREATE INDEX - 创建索引





### ALTER TABLE - 修改表





### DROP - 删除







-----

## SQL 常用函数
