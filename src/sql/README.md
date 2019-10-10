#  SQL语法
-------------------------------------------------------------------
##  基础部分
####  select
```
select col_name from table_name;
#仅返回同列中值不同的记录
select distinct col_name from table_name;
```

#### SQL order by keyword
```
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

####  insert
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

#or insert all values
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

####  NULL
```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

####   update
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

#### delete
```
DELETE FROM table_name
WHERE condition;
```

###  运算符小结

####  BETWEEN
```
SELECT
    col_name
FROM
    table_name
WHERE
    col_name BETWEEN 8000 AND 10000
ORDER BY col_name;
```

####  IN
```
SELECT
    col_name
FROM
    table_name
WHERE
    col_name IN (1 , 9)
ORDER BY col_name;
```

#### LIKE
```
SELECT
    col_name
FROM
    table_name
WHERE
    col_name LIKE 'Ma%'
ORDER BY col_name;
```

####  ALL
```
SELECT
    col_name
FROM
    table_name
WHERE
    col_name >= ALL (SELECT
            col_name
        FROM
            table_name
        WHERE
            another_col_name = 8)
```

####  ANY
```
SELECT
    col_name
FROM
    table_name
WHERE
    col_name > ANY(SELECT
            AVG(another_col_name)
        FROM
            table_name
        GROUP BY another_col_name_1)
```

#### EXISTS
```
SELECT
    col_name
FROM
    table_name e
WHERE
    EXISTS( SELECT
            another_col_name
        FROM
            another_table_name d
        WHERE
            d.another_col_name = e.col_name);
```


-------------------------------------------------------------------------------
##  进阶
####  top|limit|rownu
```
#mysql limit
SELECT col_name
FROM  table_name
LIMIT 5;
```

####  通配符
|通配符|意义|备注|
|-|-|-|
|%|一个或者多个字符| %asd% |
|_|匹配单个字符|
|-|范围匹配|a-z a到z的任一字符|
|[]|以括号中字符的任一个|[abs]
|[!]|非括号内任一字符|[!abs]

####  数据类型
 |数据类型|描述|备注|
 |-|-|-|
 |CHARACTER(n)|字符/字符串，固定长度n||
 |VARCHAR(n)|字符/字符串，可变长度、最大为n
 |BINARY(n)|二进制串，固定长度n
 |VARBINARY(n)|可变长度二进制串，最大为n
 |BOOLEAN|布尔类型|
 |INTEGER(p)|整数，精度p|
 |SMALLINT|整数，精度5|
 |INTEGER|整数，精度10|
 |BIGINT|整数，精度19|
 |DECIMAL(p,s)|精度p 小数点后s位|
 |NUMERIC(p,s)|精度p，小数点后s位
 |FLOAT(p)|尾数精度p
 |REAL|尾数精度7
 |FLOAT|尾数精度16
 |DOUBLE PRECISION|尾数精度16
 |DATE|年月日
 |TIME|时分秒
 |TIMESTAMP|年月日时分秒
 |INTERVAL|整数、代表一段时间，取决于区间类型
 |ARRAY|元素的固定长度的有序集合
 |MULTISET|元素的可变长度的无序集合
 |XML|XML数据



####  join
######  返回一个连接的表，表的字段有col1 、col2
```
SELECT table1.col1, table2.col2
FROM table1
INNER JOIN table2
ON table1.col_id=table2.col_id;
```

####  alter
######   向表中增加一列
```
ALTER TABLE table_name
ADD column_name datatype
```

######  删除表中的某一列
```
ALTER TABLE table_name
DROP COLUMN column_name
```

######  修改某一列的数据类型
```
#msyql/oracle
ALTER TABLE table_name
MODIFY COLUMN column_name datatype

#sql server/ms acess
ALTER TABLE table_name
ALTER COLUMN column_name datatype
```

####  auto increment
```
#mysql
id INT NOT NULL  AUTO_INCREMENT
#默认从1开始，如从100开始
ALTER TABLE table_name AUTO_INCREMENT=100

 #sql server  1开始步长也为1
 ID int IDENTITY(1,1) PRIMARY KEY

```


####  sql   DATE FUNCTION FOR mysql
|function|describe|bak|
|-|-|-|
|NOW()|返回当前的日期和时间
|CURDATE()|返回当前的日期
|CURTIME()|返回当前的时间
|DATE()|提取日期或日期/时间表达式的日期部分
|EXTRACT()|	返回日期/时间的单独部分
|DATE_ADD()|向日期添加指定的时间间隔
|DATE_SUB()|从日期减去指定的时间间隔
|DATEDIFF()|返回两个日期之间的天数
|DATE_FORMAT()|	用不同的格式显示日期/时间


#####   mysql date tyoe example
|datatype|value example|
|-|-|
|DATE|YYYY-MM-DD|
|DATETIME|YYYY-MM-DD HH:MM:SS|
|TIMESTAMP|YYYY-MM-DD HH:MM:SS|
|YEAR|YYYY 或YY|

####  alias
```
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;
```
