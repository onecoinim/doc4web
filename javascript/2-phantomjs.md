Phantomjs 的安装与使用
--------------------------------------------

官方网站：http://phantomjs.org

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

* 把phantomjs可执行文件放到系统路径下

```
sudo mv bin/phantomjs /usr/local/bin/
```