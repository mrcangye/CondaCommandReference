# `conda info`

显示有关conda 安装的信息。

选项有：

```
usage: conda info [-h] [--json] [-v] [-q] [-a] [--base] [-e] [-s]
                  [--unsafe-channels]
```

## 命名参数

- -a, --all

  显示所有的信息

- --base

  显示基本环境路径。

- -e, --envs

  列出所有已知的conda 环境

- -s, --system

  列出环境变量

- --unsafe-channels

  现示不安全的源列表。
## 输出、提示和控制流选项

- --json

  输出为 json格式，方便conda调用

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次

- -q, --quiet

  不显示进度条