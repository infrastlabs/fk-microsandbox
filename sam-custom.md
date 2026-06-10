

### 0610|build

- ref `drat//2026/26-0606-agent-manager-ui.md`
- deb9.224/ubt16.223; glib228@deb10`[231@ubt20; 231@deb11.same]`; 
  - ubt26-2.43|`ubt24-2.39|ubt22-2.35|ubt20-2.31`|ubt18-2.27|ubt16-2.23|ubt14-2.19
  - `deb13-2.41|deb12-2.36|deb11-2.31`|deb10-2.28|deb9-2.24|deb8-2.19@2015
  - cent7-2.17|cent8-2.28|cent9.steam-2.34

```bash
# 8:41|err1-dseek
  # debian9 microsandbox 构建报错 rust-lld: error: undefined symbol: copy_file_range ==> ubt18.glibc227
  根本原因：Debian 9的glibc版本过低
    问题根源：copy_file_range 这个符号（函数）是在 glibc 2.27 版本才被正式加入到C标准库中的。它为用户空间提供了一个统一的调用接口，如果底层内核不支持，glibc会提供一个用户空间的模拟实现来保证兼容性。
    系统现状：Debian 9 (Stretch) 于2017年发布，其默认的 glibc 版本是 2.24。

  # 换ubuntu18 报错 rust-lld: error: undefined symbol: statx ==> deb10.glibc228
  🎯 根本原因：statx 与 glibc 版本
    statx 的引入：statx 是一个较新的系统调用，它能提供比传统 stat 函数更丰富的文件信息。glibc 在 2.28 版本才正式封装了这个系统调用，并将其作为C标准库的一部分公开。
    你的环境：你使用的 Ubuntu 18.04，其默认的 glibc 版本是 2.27。它恰好缺少 statx 的封装

```

