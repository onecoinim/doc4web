Padrino 开发框架使用


#### 1. rake ar:create失败，似乎没有任何作用？

问题：https://github.com/padrino/padrino-framework/issues/1856

解决：

* 上面的链接给了一种解决办法，就是注释掉attr_protected的使用；
    
* 为了省事，直接使用SQL语句： 
   
    Mysql创建数据库sql语句
    CREATE DATABASE IF NOT EXISTS onecoinim_db_product DEFAULT CHARSET utf8 COLLATE utf8_general_ci;