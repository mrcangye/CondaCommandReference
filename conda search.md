# `conda search`

搜索包并显示相关信息。

选项：

```
usage: conda search [-h] [--envs] [-i] [--subdir SUBDIR] [-c CHANNEL]
                    [--use-local] [--override-channels]
                    [--repodata-fn REPODATA_FNS] [-C] [-k] [--offline]
                    [--json] [-v] [-q]
```

## 命名参数

- --envs

  搜索当前用户的所有环境。 如果以管理员身份运行（在 Windows 上）或 UID 0（在 unix 上），那么会搜索系统上的所有已知环境。

- -i, --info

  提供每个包的详细信息。

- --subdir, --platform

  搜索给定的子目录。 格式应为“osx-64”、“linux-32”、“win-64”等。 默认是搜索当前平台。

## 自定义源

- -c, --channel

  用于搜索包的附加源。按照给定顺序搜索源（包括使用 '[file://](file:///)' 语法的本地目录或简单的路径，如 '/home/conda/mychan' 或 '../mychan '）。 然后，搜索 .condarc 中的默认源（除非给出了 --override-channels）。 您可以使用 `defaults` 来获取 conda 的默认包。 您还可以使用任何名称，并且 `.condar`   的  `channel_alias` 值将被添加。 默认的 `channel_alias` 是 http://conda.anaconda.org/。

- --use-local

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

- --repodata-fn

  指定远程服务器上的 repodata 名称。 Conda 将尝试您指定的内容，出现错误则最终将退回到 repodata.json。  首先尝试最左边的条目，并自动为您添加 repodata.json 。

## 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

## 输出、提示和控制流选项

- --json

  输出为json格式，方便后续编程使用

- -v, --verbose

  一次用于INFO，两次用于Debug，三次用于TRACE。

- -q, --quiet

  不显示进度条。

