---
layout: post
title: Load data into mysql using csv file (mysqlimport)
---

if you have csv file containing data match with particular mysql table then you can load these data into mysql table using following comand

 mysqlimport --local  --fields-terminated-by=, -u root  -p DatabaseName  /path/and/table_name.csv

example : mysqlimport --local  --fields-terminated-by=, -u root  -p PRBT  /home/sisila/rbt/scheduled_contents.csv 



Please refer following refrence for more information [Mysql refrence](http://dev.mysql.com/doc/refman/5.7/en/mysqlimport.html).
