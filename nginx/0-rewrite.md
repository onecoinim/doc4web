
### 官方文档

链接：http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_pass

### 重写配置

1. 重写服务器localhost:4200 -> localhost，需要proxy_redirect，但对于image,css,script等无效

链接：http://superuser.com/questions/690916/how-to-make-nginx-rewrite-uris-in-http-body-content

     https://gist.github.com/lukemelia/3714b351c7865d091160

     http://w.gdu.me/wiki/sysadmin/nginx_proxy_redirect.html 【中文】

     http://serverfault.com/questions/586586/nginx-redirect-via-proxy-rewrite-and-preserve-url 【无效果】

插件：https://github.com/yaoweibin/ngx_http_substitutions_filter_module

2. 重写地址需要rewrite，但对于host和请求参数无效

链接：http://blog.cafeneko.info/2010/10/nginx_rewrite_note/

