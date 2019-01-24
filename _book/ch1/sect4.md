# 1.4 编译

## 编译和安装命令

```shell
$./configure
$make
$make install
```

## configure流程

```shell
hgh@hgh-Macmini:~/project/nginx-stable-1.14$ ./auto/configure --help

  --help                             print this message

  --prefix=PATH                      set installation prefix
  --sbin-path=PATH                   set nginx binary pathname
  --modules-path=PATH                set modules path
  --conf-path=PATH                   set nginx.conf pathname
  --error-log-path=PATH              set error log pathname
  --pid-path=PATH                    set nginx.pid pathname
  --lock-path=PATH                   set nginx.lock pathname

  --user=USER                        set non-privileged user for
                                     worker processes
  --group=GROUP                      set non-privileged group for
                                     worker processes

  --build=NAME                       set build name
  --builddir=DIR                     set build directory

  --with-select_module               enable select module
  --without-select_module            disable select module
  --with-poll_module                 enable poll module
  --without-poll_module              disable poll module

  --with-threads                     enable thread pool support

  --with-file-aio                    enable file AIO support

  --with-http_ssl_module             enable ngx_http_ssl_module
  --with-http_v2_module              enable ngx_http_v2_module
  --with-http_realip_module          enable ngx_http_realip_module
  --with-http_addition_module        enable ngx_http_addition_module
  --with-http_xslt_module            enable ngx_http_xslt_module
  --with-http_xslt_module=dynamic    enable dynamic ngx_http_xslt_module
  --with-http_image_filter_module    enable ngx_http_image_filter_module
  --with-http_image_filter_module=dynamic
                                     enable dynamic ngx_http_image_filter_module
  --with-http_geoip_module           enable ngx_http_geoip_module
  --with-http_geoip_module=dynamic   enable dynamic ngx_http_geoip_module
  --with-http_sub_module             enable ngx_http_sub_module
  --with-http_dav_module             enable ngx_http_dav_module
  --with-http_flv_module             enable ngx_http_flv_module
  --with-http_mp4_module             enable ngx_http_mp4_module
  --with-http_gunzip_module          enable ngx_http_gunzip_module
  --with-http_gzip_static_module     enable ngx_http_gzip_static_module
  --with-http_auth_request_module    enable ngx_http_auth_request_module
  --with-http_random_index_module    enable ngx_http_random_index_module
  --with-http_secure_link_module     enable ngx_http_secure_link_module
  --with-http_degradation_module     enable ngx_http_degradation_module
  --with-http_slice_module           enable ngx_http_slice_module
  --with-http_stub_status_module     enable ngx_http_stub_status_module

  --without-http_charset_module      disable ngx_http_charset_module
  --without-http_gzip_module         disable ngx_http_gzip_module
  --without-http_ssi_module          disable ngx_http_ssi_module
  --without-http_userid_module       disable ngx_http_userid_module
  --without-http_access_module       disable ngx_http_access_module
  --without-http_auth_basic_module   disable ngx_http_auth_basic_module
  --without-http_mirror_module       disable ngx_http_mirror_module
  --without-http_autoindex_module    disable ngx_http_autoindex_module
  --without-http_geo_module          disable ngx_http_geo_module
  --without-http_map_module          disable ngx_http_map_module
  --without-http_split_clients_module disable ngx_http_split_clients_module
  --without-http_referer_module      disable ngx_http_referer_module
  --without-http_rewrite_module      disable ngx_http_rewrite_module
  --without-http_proxy_module        disable ngx_http_proxy_module
  --without-http_fastcgi_module      disable ngx_http_fastcgi_module
  --without-http_uwsgi_module        disable ngx_http_uwsgi_module
  --without-http_scgi_module         disable ngx_http_scgi_module
  --without-http_grpc_module         disable ngx_http_grpc_module
  --without-http_memcached_module    disable ngx_http_memcached_module
  --without-http_limit_conn_module   disable ngx_http_limit_conn_module
  --without-http_limit_req_module    disable ngx_http_limit_req_module
  --without-http_empty_gif_module    disable ngx_http_empty_gif_module
  --without-http_browser_module      disable ngx_http_browser_module
  --without-http_upstream_hash_module
                                     disable ngx_http_upstream_hash_module
  --without-http_upstream_ip_hash_module
                                     disable ngx_http_upstream_ip_hash_module
  --without-http_upstream_least_conn_module
                                     disable ngx_http_upstream_least_conn_module
  --without-http_upstream_keepalive_module
                                     disable ngx_http_upstream_keepalive_module
  --without-http_upstream_zone_module
                                     disable ngx_http_upstream_zone_module

  --with-http_perl_module            enable ngx_http_perl_module
  --with-http_perl_module=dynamic    enable dynamic ngx_http_perl_module
  --with-perl_modules_path=PATH      set Perl modules path
  --with-perl=PATH                   set perl binary pathname

  --http-log-path=PATH               set http access log pathname
  --http-client-body-temp-path=PATH  set path to store
                                     http client request body temporary files
  --http-proxy-temp-path=PATH        set path to store
                                     http proxy temporary files
  --http-fastcgi-temp-path=PATH      set path to store
                                     http fastcgi temporary files
  --http-uwsgi-temp-path=PATH        set path to store
                                     http uwsgi temporary files
  --http-scgi-temp-path=PATH         set path to store
                                     http scgi temporary files

  --without-http                     disable HTTP server
  --without-http-cache               disable HTTP cache

  --with-mail                        enable POP3/IMAP4/SMTP proxy module
  --with-mail=dynamic                enable dynamic POP3/IMAP4/SMTP proxy module
  --with-mail_ssl_module             enable ngx_mail_ssl_module
  --without-mail_pop3_module         disable ngx_mail_pop3_module
  --without-mail_imap_module         disable ngx_mail_imap_module
  --without-mail_smtp_module         disable ngx_mail_smtp_module

  --with-stream                      enable TCP/UDP proxy module
  --with-stream=dynamic              enable dynamic TCP/UDP proxy module
  --with-stream_ssl_module           enable ngx_stream_ssl_module
  --with-stream_realip_module        enable ngx_stream_realip_module
  --with-stream_geoip_module         enable ngx_stream_geoip_module
  --with-stream_geoip_module=dynamic enable dynamic ngx_stream_geoip_module
  --with-stream_ssl_preread_module   enable ngx_stream_ssl_preread_module
  --without-stream_limit_conn_module disable ngx_stream_limit_conn_module
  --without-stream_access_module     disable ngx_stream_access_module
  --without-stream_geo_module        disable ngx_stream_geo_module
  --without-stream_map_module        disable ngx_stream_map_module
  --without-stream_split_clients_module
                                     disable ngx_stream_split_clients_module
  --without-stream_return_module     disable ngx_stream_return_module
  --without-stream_upstream_hash_module
                                     disable ngx_stream_upstream_hash_module
  --without-stream_upstream_least_conn_module
                                     disable ngx_stream_upstream_least_conn_module
  --without-stream_upstream_zone_module
                                     disable ngx_stream_upstream_zone_module

  --with-google_perftools_module     enable ngx_google_perftools_module
  --with-cpp_test_module             enable ngx_cpp_test_module

  --add-module=PATH                  enable external module
  --add-dynamic-module=PATH          enable dynamic external module

  --with-compat                      dynamic modules compatibility

  --with-cc=PATH                     set C compiler pathname
  --with-cpp=PATH                    set C preprocessor pathname
  --with-cc-opt=OPTIONS              set additional C compiler options
  --with-ld-opt=OPTIONS              set additional linker options
  --with-cpu-opt=CPU                 build for the specified CPU, valid values:
                                     pentium, pentiumpro, pentium3, pentium4,
                                     athlon, opteron, sparc32, sparc64, ppc64

  --without-pcre                     disable PCRE library usage
  --with-pcre                        force PCRE library usage
  --with-pcre=DIR                    set path to PCRE library sources
  --with-pcre-opt=OPTIONS            set additional build options for PCRE
  --with-pcre-jit                    build PCRE with JIT compilation support

  --with-zlib=DIR                    set path to zlib library sources
  --with-zlib-opt=OPTIONS            set additional build options for zlib
  --with-zlib-asm=CPU                use zlib assembler sources optimized
                                     for the specified CPU, valid values:
                                     pentium, pentiumpro

  --with-libatomic                   force libatomic_ops library usage
  --with-libatomic=DIR               set path to libatomic_ops library sources

  --with-openssl=DIR                 set path to OpenSSL library sources
  --with-openssl-opt=OPTIONS         set additional build options for OpenSSL

  --with-debug                       enable debug logging
```

## 相关开源软件

[zlib](https://zlib.net/)

[pcre](https://www.pcre.org/)

[openssl](https://www.openssl.org/source/)

## 本地链接编译

```shell
$./auto/configure --with-pcre=../pcre-8.42 --with-zlib=../zlib-1.2.11
```

## 启动方式

```shell
# 1.默认启动方式
$/usr/local/nginx/sbin/nginx
# 2.-c指定配置文件
$/usr/local/nginx/sbin/nginx -c nginx.conf
# 3.-p指定nginx的安装目录
$/usr/local/nginx/sbin/nginx -p /usr/local/nginx
# 4.指定全局配置项
$/usr/local/nginx/sbin/nginx -g "pid /var/nginx/test.pid"
```

## 检测配置文件是否错误

```shell
$/usr/local/nginx/sbin/nginx -p /usr/local/nginx -t
```

## nginx选项

| 选项 |       含义       |
| :--: | :--------------: |
|  -v  |     查看版本     |
|  -V  | 查看编译阶段参数 |

## configure的流程

```shell
## auto/configure

# 处理configure命令参数
. auto/options
# 检测echo的\c(不换行)和-n(长度限制)的能力,创建Makefile
. auto/init
# 分析Nginx的源码结构
. auto/sources
# 获取本地NGX_PLATFORM
...
# 检查GCC是否安装,检查GCC版本是否支持编译nginx
. auto/cc/conf
# 对于非windows操作系统定义一些必要的头文件
. auto/headers
# 检测当前系统相关方法的支持
. auto/os/conf
# 定义类unix操作系统中通用的头文件和系统调用等,并检查当前环境是否支持
. auto/unix
# 线程使用
. auto/threads
# nginx模块处理
. auto/modules
# 处理三方依赖库
. auto/lib/conf
# 本地文件和目录
...
# 创建objs/Makefile文件
. auto/make
# 为objs/Makefile加入需要链接的第三方静态库,动态库或目标文件
. auto/lib/make
# 为objs/Makefile中加入install功能
. auto/install
# 加入NGX_SUPPRESS_WARN宏,NGX_SMP宏
. auto/stubs
# 显示总览结果
. auto/summary
```

