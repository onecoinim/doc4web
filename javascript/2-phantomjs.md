Phantomjs 的安装与使用
--------------------------------------------

官方网站：[http://phantomjs.org](http://phantomjs.org)

## 2. 抓取网页

* 抓取

http://javascript.ruanyifeng.com/tool/phantomjs.html#toc15

http://blog.csdn.net/starean/article/details/9467697

* 吐槽

http://segmentfault.com/q/1010000000149454

http://blog.cooer.net/2014/%E8%AE%A9%E4%BA%BA%E6%AC%A2%E5%96%9C%E8%AE%A9%E6%88%91%E5%BF%A7%E7%9A%84phantomjs/

## 1. ubuntu 12.04 - 64bit 上的编译安装

* 安装依赖包

```
sudo apt-get install build-essential g++ flex bison gperf ruby perl \
libsqlite3-dev libfontconfig1-dev libicu-dev libfreetype6 libssl-dev \
libpng-dev libjpeg-dev
```

* 下载新版源代码：
    
```
https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.0.0-source.zip
```

解压后，进入文件夹执行：   
  
```
$ ./build.sh
```            
  
会很慢,大概30min左右后，会在文件夹下产生一个bin文件夹，里面有个phantomjs可执行文件；

* 下载二进制包【推荐】

```
https://phantomjs.googlecode.com/files/phantomjs-1.9.2-linux-x86_64.tar.bz2  
```

如果上面的被墙，就在下面的地址，选择合适的

```
https://bitbucket.org/ariya/phantomjs/downloads 
```

然后，解压，同样执行下一步。

* 把phantomjs可执行文件放到系统路径下

```
sudo mv bin/phantomjs /usr/local/bin/
```