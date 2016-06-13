title: "Nginx+lua环境搭建"
date: 2015-05-11 14:09:53
tags: Nginx lua
---
使用[OpenResty](http://openresty.org/)安装.

我理解为类似WampServer一站式安装包(不对请指正)

```
$ wget http://openresty.org/download/ngx_openresty-1.7.10.1.tar.gz
$ tar -zxvf ngx_openresty-1.7.10.1.tar.gz
$ cd ngx_openresty-1.7.10.1
$ ./configure
$ make && make install
```
configure之前需要安装的相关组件

```
$ yum -y install gcc zlib zlib-devel openssl openssl-devel
```
安装目录默认会在

```
$ cd /usr/local/openresty/
```
测试lua环境是否正常

```
$ lua
print("hello")
```
测试nginx+lua

```
cd /usr/local/openresty/nginx/conf
```
在nginx.conf里添加测试内容

```
 location /hello {
        default_type 'text/plain';
        content_by_lua 'ngx.say("ok")';
        }
```
启动nginx

```
$ sbin/nginx
```
浏览器访问页面显示ok,完毕!
