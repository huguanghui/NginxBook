# 2.1 配置结构

## 通用语法
### 块配置项
```cpp
events {
...
}

http {
...
}

upstream backend {
    server 127.0.0.1:8080;
}

gzip on;
server {
    ...
    location /webstatic {
        gzip on;
    }
}
```

### 配置项的语法
```cpp
配置项名 配置项值1 配置项值2 ... ;
```

### 配置项注释
```cpp
#pid    logs/nginx.pid
```

### 配置项的单位
```cpp
空间大小
    K或k  千字节
    M或者m 兆字节
时间大小
    ms(毫秒)
    s(秒)
    m(分钟)
    h(小时)
    d(天)
    w(周)
    M(月)
    y(年)
```