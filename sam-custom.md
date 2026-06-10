

### 0610|build

```bash
# 8:41|err1-dseek
  debian9 microsandbox 构建报错 rust-lld: error: undefined symbol: copy_file_range
  # 根本原因：Debian 9的glibc版本过低
    问题根源：copy_file_range 这个符号（函数）是在 glibc 2.27 版本才被正式加入到C标准库中的。它为用户空间提供了一个统一的调用接口，如果底层内核不支持，glibc会提供一个用户空间的模拟实现来保证兼容性。
    系统现状：Debian 9 (Stretch) 于2017年发布，其默认的 glibc 版本是 2.24。



```

