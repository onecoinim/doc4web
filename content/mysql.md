Mysql 数据库
------------------

### 3. 生产环境下不建议使用socket

* MySQL error - socket '/tmp/myqsl.sock'

https://github.com/paulsutcliffe/dreamhostrails/issues/3

### 2、Mysql在ubuntu下的安装

    $ sudo apt-get install libmysqlclient-dev libmysql-ruby
    $ sudo apt-get install mysql-server

### 1、Mysql创建数据库sql语句

    CREATE DATABASE IF NOT EXISTS onecoinim_db_product DEFAULT CHARSET utf8 COLLATE utf8_general_ci;

