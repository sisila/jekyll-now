---
layout: post
title: MySQL Import CSV data
---

Following simple comand will populate mysql table with data whic are stored in a csv file.

{% highlight bash %} mysqlimport --local  --fields-terminated-by=, -u root  -p DatabaseName  /path/and/table_name.csv {% endhighlight %}

Important
------	

1. csv file name should equal to table name.
2. number of column in tablke should match with values count of a csv line.
3. this method is usefull to insert big amount of data in to a mysql table.

example :
------
test_table.csv
{% highlight css %}
$ cat /home/sisila/test_table.csv 
1,sisila
2,praveena
3,malika
$
 {% endhighlight %} 

create a database and import data
 {% highlight sql %}
mysql>  CREATE DATABASE test_database;
Query OK, 1 row affected (0.00 sec)
mysql>  use test_database;
Database changed
mysql> create table test_table(id int, name varchar(100));
Query OK, 0 rows affected (0.46 sec)

mysql> desc test_database;
ERROR 1146 (42S02): Table 'test_database.test_database' doesn't exist
mysql> desc test_table;
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| id    | int(11)      | YES  |     | NULL    |       |
| name  | varchar(100) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
2 rows in set (0.01 sec)

mysql> 

 {% endhighlight %}

 import data
{% highlight shell %}
$ mysqlimport --local  --fields-terminated-by=, -u root  -p test_database  /home/sisila/test_table.csv
{% endhighlight %} 

check the result
{% highlight sql %}
mysql> use test_database;
Database changed
mysql> select * from test_table;
+------+----------+
| id   | name     |
+------+----------+
|    1 | sisila   |
|    2 | praveena |
|    3 | malika   |
+------+----------+
3 rows in set (0.00 sec)

mysql> 

{% endhighlight %}


Please refer following refrence for more information [Mysql refrence](http://dev.mysql.com/doc/refman/5.7/en/mysqlimport.html).
