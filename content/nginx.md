
### 官方文档

链接：http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_pass

### 重写配置

3. squid3 代理服务器、缓存服务器、加速器

```
# Squid中文权威指南
http://home.arcor.de/pangj/squid/index.html

# 前端nginx负载均衡后端多个squid配置
http://www.eduyo.com/server/linux/829.html

# 在ec2上配置squid http代理服务器笔记
http://www.zuola.com/weblog/2012/12/1873.htm

# 双服务器，CentOS系统，使用Squid和Stunnel搭建翻墙代理服务
http://fuweiyi.com/others/2014/05/15/a-Centos-Squid-Stunnel-proxy.html

# Stunnel + Squid + pac文件快速简单自动过滤翻墙
https://www.fourfire.cc/544.html

# 用NGINX 代理翻墙
http://www.linuxbyte.org/yong-nginx-daili-fanqiang.html
```

2. 重写地址需要rewrite，但对于host和请求参数无效

链接：http://blog.cafeneko.info/2010/10/nginx_rewrite_note/

1. 重写服务器localhost:4200 -> localhost，需要proxy_redirect，但对于image,css,script等无效

链接：http://superuser.com/questions/690916/how-to-make-nginx-rewrite-uris-in-http-body-content

     https://gist.github.com/lukemelia/3714b351c7865d091160

     http://w.gdu.me/wiki/sysadmin/nginx_proxy_redirect.html 【中文】

     http://serverfault.com/questions/586586/nginx-redirect-via-proxy-rewrite-and-preserve-url 【无效果】

插件：https://github.com/yaoweibin/ngx_http_substitutions_filter_module

