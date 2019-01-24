# 2.2 基本配置

## 调试、定位问题的配置
### 守护进程
**语法**: daemon on | off;
**默认**: daemon on;

### master/worker工作方式
**语法**: master_process on | off;
**默认**: master_process on;

### error日志的设置
**语法**: error_log /path/file level;
**默认**: error_log logs/error.log error;

### 处理几个特殊的调试点
**语法**: debug_points [stop | abort]

### 仅对指定的客户端输出debug级别的日志
**语法**: debug_connection [IP|CIDR]
events {
    debug_connection 10.224.66.14;
    debug_connection 10.224.57.0/24;
}

### 限制coredump核心转储文件的大小
**语法**: worker_rlimit_core size;

### 指定coredump文件生成的目录
**语法**: working_directory path;

## 正常运行的必备配置项
### 定义环境变量
**语法**: env VAR|VAR=VALUE;

### 嵌入其他配置文件
**语法**: include /path/file;

### pid文件的路径
**语法**: pid path/file;
**默认**: pid logs/nginx.pid;

### nginx进程运行的用户及用户组
**语法**: user username [groupname];
**默认**: user nobody nobody;

### nginx worker进程可以打开的最大句柄数
**语法**: worker_rlimit_nofile limit;

### 限制信号队列
**语法**: worker_rlimit_sigpending limit;

## 优化性能的配置项
### worker进程数
**语法**: worker_processes number;
**默认**: worker_processes 1;

### worker进程绑定CPU内核
**语法**: worker_cpu_affinity cpumask;

### SSL硬件加速
**语法**: ssl_engine device;

### 系统调用gettimeofday的执行频率
**语法**: timer_resolution t;

### worker进程优先级设置
**语法**: worker_priority nice;
**默认**: worker_priority 0;

## 事件配置项
### 是否打开accept锁
**语法**: accept_mutex [on|off];
**默认**: accept_mutex on;

### lock文件的路径
**语法**: lock_file path/file;
**默认**: lock_file logs/nginx.lock;

### 使用accept锁后到真正建立连接之间的延迟时间
**语法**: accept_mutex_delay Nms;
**默认**: accept_mutex_delay 500ms;

### 批量建立新连接
**语法**: multi_accept [on|off];
**默认**: multi_accept off;

### 选择事件模型
**语法**: use [kqueue|rtsig|epoll|/dev/poll/|select|poll|eventport];

### worker最大连接数
**语法**: worker_connections numbers;