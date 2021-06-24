# `conda create`

从指定的包列表创建一个新的 conda 环境。 要使用创建的环境，在该环境的目录中使用`conda activate envname`。 `envname`用你的环境的名字替换一下。此命令需要` -n NAME `或` -p PREFIX `选项。

命令选项

```
usage: conda create [-h] [--clone ENV] [-n ENVIRONMENT | -p PATH] [-c CHANNEL]
                    [--use-local] [--override-channels]
                    [--repodata-fn REPODATA_FNS] [--strict-channel-priority]
                    [--no-channel-priority] [--no-deps | --only-deps]
                    [--no-pin] [--copy] [-C] [-k] [--offline] [-d] [--json]
                    [-q] [-v] [-y] [--download-only] [--show-channel-urls]
                    [--file FILE] [--no-default-packages] [--dev]
                    [package_spec [package_spec ...]]
```

## 位置参数

- package_spec

  要在 conda 环境中安装或更新的软件包的名字

## 命名参数

- --clone

  现有本地环境的路径或名字

- --file

  从给定文件中读取包版本，可以通过重复使用。举个栗子`--file=file1 --file=file2`

- --dev

  在脚本中使用`sys.executable -m conda` 而不是 conda程序。 主要用于针对旧 Python 版本测试新 conda 源的开发测试期间使用。

## 目标环境的选项

- -n, --name

  环境名字

- -p, --prefix

  环境的全路径

## 自定义源

- -c, --channel

  用于搜索包的源。 按照给定顺序搜索URL。包括使用`file`语法或简单路径的本地目录，然后搜索 `.condarc`文件中的默认值或源（除非给出了 --override-channels）。既可以使用`defaults`来获取`conda`的默认包。 也可以使用任何名字，并且`.condarc`文件中的` channel_alias `值将被添加。默认的`channel_alias`值请参阅 http://conda.anaconda.org/

- --use-local

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

  指定远程服务器上的 repodata 名称。 Conda 将尝试你指定的任何内容，但如果你的规范与你在此处指定的内容不符，将退回到 repodata.json。 这用于使用时间范围减少的 repodata。 你可以多次通过此标志。 首先尝试最左边的条目，并自动为你添加 repodata.json 的后备。

## Solver Mode Modifiers

- --strict-channel-priority

  如果具有相同名称的包出现在较高优先级源中，则不考虑较低优先级源中的包。

- --no-channel-priority

  包版本优先于源优先级。 覆盖 `conda config --show channel_priority `给出的值。

- --no-deps

  不安装、更新、删除或更改依赖项。 这将导致破坏环境和不一致的行为。 风险自负。

- --only-deps

  只安装依赖项。

- --no-pin

  忽略固定文件。

- --no-default-packages

  忽略 .condarc 文件中的`create_default_packages`。

## 包链接和安装时的选项

- --copy

  使用副本而不是硬链接或软链接安装所有软件包。

## 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

## 输出、提示和控制流选项

- -d, --dry-run

  只显示本应该做的事情。

- --json

  输出为 json格式，方便conda调用

- -q, --quiet

  不显示进度条

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次。

- -y, --yes

  不要求安装确认

- --download-only

  Solve an environment and ensure package caches are populated, but exit prior to unlinking and linking packages into the prefix.

- --show-channel-urls

  显示源地址。 覆盖`conda config --show show_channel_urls` 给出的值.