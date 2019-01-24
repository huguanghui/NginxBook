# 3.2 模块API

## 3.2.1 内存池

### API描述
```cpp
#define NGX_DEFAULT_POOL_SIZE    (16 * 1024)
// 创建内存池(size通常设为NGX_DEAULT_POOL_SIZE)
ngx_pool_t *ngx_create_pool(size_t size, ngx_log_t *log);
// 销毁内存池
void ngx_destroy_pool(ngx_pool_t *pool);
// 重置内存池(把大块内存释放给操作系统,小块内存在不释放的情况下复用)
void ngx_reset_pool(ngx_pool_t *pool);

//  分配地址对齐的内存.按总线长度(sizeof(unsigned long))地址对齐后,可以减少CPU读取内存的次数.
void *ngx_palloc(ngx_pool_t *pool, size_t size);
// 分配内存时不进行地址对齐
void *ngx_pnalloc(ngx_pool_t *pool, size_t size);
// 分配出地址对齐的内存后,再调用memset将这些内存全部清0
void *ngx_pcalloc(ngx_pool_t *pool, size_t size);
// 按alignment进行地址对齐来分配内存.无论size有多小,采用大地址方式.
void *ngx_pmemalign(ngx_pool_t *pool, size_t size, size_t alignment);
// 提前释放大块内存
ngx_int_t ngx_pfree(ngx_pool_t *pool, void *p);

// 添加一个需要在内存池释放时同时释放的资源.
ngx_pool_cleanup_t *ngx_pool_cleanup_add(ngx_pool_t *p, size_t size);
// 在内存池释放前，关闭需要关闭文件
void ngx_pool_run_cleanup_file(ngx_pool_t *p, ngx_fd_t fd);
// 关闭文件来释放资源的方法
void ngx_pool_cleanup_file(void *data);
// 删除文件来释放资源的方法
void ngx_pool_delete_file(void *data);
```

## 3.2.2 error日志
```cpp
#define NGX_HAVE_VARIADIC_MACROS  1

#define ngx_log_error(level, log, args...)                                    \
    if ((log)->log_level >= level) ngx_log_error_core(level, log, args)

void ngx_log_error_core(ngx_uint_t level, ngx_log_t *log, ngx_err_t err,
    const char *fmt, ...);

#define ngx_log_debug(level, log, args...)                                    \
    if ((log)->log_level & level)                                             \
        ngx_log_error_core(NGX_LOG_DEBUG, log, args)

#define ngx_log_debug0(level, log, err, fmt)                                  \
        ngx_log_debug(level, log, err, fmt)

#define ngx_log_debug1(level, log, err, fmt, arg1)                            \
        ngx_log_debug(level, log, err, fmt, arg1)

#define ngx_log_debug2(level, log, err, fmt, arg1, arg2)                      \
        ngx_log_debug(level, log, err, fmt, arg1, arg2)

#define ngx_log_debug3(level, log, err, fmt, arg1, arg2, arg3)                \
        ngx_log_debug(level, log, err, fmt, arg1, arg2, arg3)

#define ngx_log_debug4(level, log, err, fmt, arg1, arg2, arg3, arg4)          \
        ngx_log_debug(level, log, err, fmt, arg1, arg2, arg3, arg4)

#define ngx_log_debug5(level, log, err, fmt, arg1, arg2, arg3, arg4, arg5)    \
        ngx_log_debug(level, log, err, fmt, arg1, arg2, arg3, arg4, arg5)

#define ngx_log_debug6(level, log, err, fmt,                                  \
                       arg1, arg2, arg3, arg4, arg5, arg6)                    \
        ngx_log_debug(level, log, err, fmt,                                   \
                       arg1, arg2, arg3, arg4, arg5, arg6)

#define ngx_log_debug7(level, log, err, fmt,                                  \
                       arg1, arg2, arg3, arg4, arg5, arg6, arg7)              \
        ngx_log_debug(level, log, err, fmt,                                   \
                       arg1, arg2, arg3, arg4, arg5, arg6, arg7)

#define ngx_log_debug8(level, log, err, fmt,                                  \
                       arg1, arg2, arg3, arg4, arg5, arg6, arg7, arg8)        \
        ngx_log_debug(level, log, err, fmt,                                   \
                       arg1, arg2, arg3, arg4, arg5, arg6, arg7, arg8)

ngx_log_t *ngx_log_init(u_char *prefix);
void ngx_cdecl ngx_log_abort(ngx_err_t err, const char *fmt, ...);
void ngx_cdecl ngx_log_stderr(ngx_err_t err, const char *fmt, ...);
u_char *ngx_log_errno(u_char *buf, u_char *last, ngx_err_t err);
ngx_int_t ngx_log_open_default(ngx_cycle_t *cycle);
ngx_int_t ngx_log_redirect_stderr(ngx_cycle_t *cycle);
ngx_log_t *ngx_log_get_file_log(ngx_log_t *head);
char *ngx_log_set_log(ngx_conf_t *cf, ngx_log_t **head);

static ngx_inline void
ngx_write_stderr(char *text)
{
    (void) ngx_write_fd(ngx_stderr, text, ngx_strlen(text));
}

static ngx_inline void
ngx_write_stdout(char *text)
{
    (void) ngx_write_fd(ngx_stdout, text, ngx_strlen(text));
}
```
