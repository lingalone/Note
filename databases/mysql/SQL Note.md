#SQL Note

##select distinct语句与distinct关键字
> 作用：关键字用于返回唯一不同的值。
* 结构：
```mysql
select distinct column_name1, column_name2,... from table_name;
```
* 例子

```mysql
 mysql> select *from websites;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
|  1 | Google       | https://www.google.cm/    |     1 | USA     |
|  2 | 淘宝         | https://www.taobao.com/   |    13 | CN      |
|  3 | 菜鸟教程     | http://www.runoob.com/    |  4689 | CN      |
|  4 | 微博         | http://weibo.com/         |    20 | CN      |
|  5 | Facebook     | https://www.facebook.com/ |     3 | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.00 sec)
```
* 处理结果：
```mysql
mysql> select distinct country from websites;
+---------+
| country |
+---------+
| USA     |
| CN      |
+---------+
2 rows in set (0.00 sec)
```
* **思考：如何计算重复项的数目??**

```mysql
mysql> select count(country) as countrynum,country from websites group by country;
+------------+---------+
| countrynum | country |
+------------+---------+
|          3 | CN      |
|          2 | USA     |
+------------+---------+
2 rows in set (0.00 sec)
```



-----
## where子句

>作用：用于过滤记录，提取满足标准的记录
* 结构：
```mysql
select column_name1, column_name2,...
from table_name
where column_name operator value;
```
* 例子：

```mysql
mysql> select *from websites where country='CN';
+----+--------------+-------------------------+-------+---------+
| id | name         | url                     | alexa | country |
+----+--------------+-------------------------+-------+---------+
|  2 | 淘宝         | https://www.taobao.com/ |    13 | CN      |
|  3 | 菜鸟教程     | http://www.runoob.com/  |  4689 | CN      |
|  4 | 微博         | http://weibo.com/       |    20 | CN      |
+----+--------------+-------------------------+-------+---------+
3 rows in set (0.00 sec)
```

* **where中operator（操作符，运算符）有哪些?**
--------

|     运算符     |                    描述                    |
| :---------: | :--------------------------------------: |
|   between   | 在某范围内where col_name between val1 and val2 |
|    like     |         搜索列中的指定模式(模式识别如'char%')          |
|     in      | 在指定项内，例：where city in('beijing','shanghai') |
| not,and,or  | 逻辑运算符，分别表示否、并且、或，用于多个逻辑连接。优先级：not > and > or |
|      =      |                    等于                    |
|     !=      |            不等于，某些数据库系统也写作 <>             |
|  >,<,>=,<=  |             大于，小于，大于等于，小于等于              |
| not between |                 不在某个范围之内                 |
|  not like   |                 LIKE的反义                  |
|   not in    |                  不在指定项内                  |
|   is null   |                  空值判断符                   |
| is not null |                  非空判断符                   |
|      %      |         模式匹配符，表示任意字串,一般和like一起使用         |

-------
## order by 关键字
>作用：用于对结果集按照一列或者多列进行排序，默认为升序排序。
* 结构：
```mysql
select column_name1, column_name2... 
from table_name 
order by column_name1, column_name2,.... asc|desc;
```
> **注意：指定对某列进行升降排序时，在列名后直接加asc|desc。**

* 例子：
```mysql
mysql> select * from websites;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
|  1 | Google       | https://www.google.cm/    |     1 | USA     |
|  2 | 淘宝         | https://www.taobao.com/   |    13 | CN      |
|  3 | 菜鸟教程     | http://www.runoob.com/    |  4689 | CN      |
|  4 | 微博         | http://weibo.com/         |    20 | CN      |
|  5 | Facebook     | https://www.facebook.com/ |     3 | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.00 sec)
```
* 结果：	
```mysql
mysql> select * from websites order by country desc,alexa asc;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
|  1 | Google       | https://www.google.cm/    |     1 | USA     |
|  5 | Facebook     | https://www.facebook.com/ |     3 | USA     |
|  2 | 淘宝         | https://www.taobao.com/   |    13 | CN      |
|  4 | 微博         | http://weibo.com/         |    20 | CN      |
|  3 | 菜鸟教程     | http://www.runoob.com/    |  4689 | CN      |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.00 sec)
```
> 理解：对country列先按降序排，排完后对alexa列进行升序排。