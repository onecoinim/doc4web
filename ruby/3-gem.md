Gem 的安装与使用
---------------

#### 1、gem install xxx 的时候遇到错误信息包含：“Error fetching data: Errno::ETIMEDOUT: Operation timed out - connect(2)”

解决：网络问题导致请求服务器连接被重置了。你可以尝试换一台机器或网络尝试安装，检测是否是服务器的问题。如果是，请更新源：

    $ gem sources --remove https://rubygems.org/
    $ gem sources -a https://ruby.taobao.org/
    $ gem sources -l
    *** CURRENT SOURCES ***
    
    https://ruby.taobao.org        