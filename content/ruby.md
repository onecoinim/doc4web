ruby 语言及其框架 目录
----------------

## 1. rails

## 2. padrino

### (2)详解Rack::Cookie

问题：

https://github.com/padrino/padrino-framework/issues/1801

参考：

http://cookiebody.github.io/2014/10/24/cookie-and-session-in-rack.html
http://cookiebody.github.io/2014/04/20/padrino-csrf-protection.html


### (1) rake ar:create失败，似乎没有任何作用？

问题：https://github.com/padrino/padrino-framework/issues/1856

解决：

* 上面的链接给了一种解决办法，就是注释掉attr_protected的使用；
    
* 为了省事，直接使用SQL语句： 
   
    Mysql创建数据库sql语句
    CREATE DATABASE IF NOT EXISTS onecoinim_db_product DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
    
## 3. gems

### (1) gem install xxx 的时候遇到错误信息包含：“Error fetching data: Errno::ETIMEDOUT: Operation timed out - connect(2)”

解决：网络问题导致请求服务器连接被重置了。你可以尝试换一台机器或网络尝试安装，检测是否是服务器的问题。如果是，请更新源：

    $ gem sources --remove https://rubygems.org/
    $ gem sources -a https://ruby.taobao.org/
    $ gem sources -l
    *** CURRENT SOURCES ***
    
    https://ruby.taobao.org        
    
## 4. ruby

### (5) 网站内容抓取

https://ruby-china.org/topics/21157

http://docs.seattlerb.org/mechanize/EXAMPLES_rdoc.html#label-Google

http://casperjs.org/

http://my.oschina.net/xsinger/blog/14206

### (4) ruby执行周期性任务

http://www.cnblogs.com/wangyuyu/p/3818826.html

### (3) ruby文件操作

* 比较好的中文文档

链接：http://www.bkjia.com/ruby/998607.html

链接：http://notreally.iteye.com/blog/155071

### (2) Json文件操作

* 文档

http://ruby-doc.org/stdlib-2.1.2/libdoc/json/rdoc/JSON.html

* sinatra读取json配置文件 

https://github.com/sinatra/sinatra-contrib/blob/master/lib/sinatra/config_file.rb

* 很好的问答

http://cache.baiducontent.com/c?m=9d78d513d98306ff13fa940f55578a3a0e54f12561c0d16568d3e75f92140112063cf7fc677c1f5e95833e7000dc5441abb665236e5e64e0db9cd61798ac925f7ed57829335bd100548844f38a5b2ec3279758e2ab04b3faad6d84aea48b9e090fdd53733cdde78b2c5303ca19b05361a8b1993e4f0c51e0f03b67f85e742e9d&p=9a63dc1197904ead19bd9b7b0f42&newp=c262c54ad3c107fc57eff8374a0a92695803ed6036d7d553&user=baidu&fm=sc&query=ruby+json+to%5Fhash&qid=b1eaf5040000688b&p1=9

You want JSON.parse or JSON.load:

    def load_user_lib( filename )
      JSON.parse( IO.read(filename) )
    end
    
The key here is to use IO.read as a simple way to load the JSON string from disk, so that it can be parsed.

I've linked to the JSON documentation above, so you should go read that for more details. But in summary:

    json = my_object.to_json — method on the specific object to create a JSON string.
    json = JSON.generate(my_object) —�0�2create JSON string from object.
    JSON.dump(my_object, someIO) — create a JSON string and write to a file.
    my_object = JSON.parse(json) — create a Ruby object from a JSON string.
    my_object = JSON.load(someIO) — create a Ruby object from a file.

Alternatively:

    def load_user_lib( filename )
      File.open( filename, "r" ) do |f|
        JSON.load( f )
      end
    end

Note: I have used a "snake_case" name for the method corresponding to your "camelCase" saveUserLib as this is the Ruby convention.

### (1) Erb文件操作

* 文档

http://ruby-doc.org/stdlib-2.2.2/libdoc/erb/rdoc/ERB.html