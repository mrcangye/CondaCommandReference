# `conda remove`



从指定的 `conda`环境中删除包列表。

选项：

```
usage: conda remove [-h] [-n ENVIRONMENT | -p PATH] [-c CHANNEL] [--use-local]
                    [--override-channels] [--repodata-fn REPODATA_FNS] [--all]
                    [--features] [--force-remove] [--no-pin] [-C] [-k]
                    [--offline] [-d] [--json] [-q] [-v] [-y] [--dev]
                    [package_name [package_name ...]]
```

## 位置参数

- package_name

  要删除的包名

## 命名参数

- --dev

  在包装脚本中使用 `sys.executable -m conda` 而不是 `CONDA_EXE`。仅供测试。

## Target Environment Specification

- -n, --name

  环境名

- -p, --prefix

  环境全路径

## Channel Customization

- -c, --channel

  Additional channel to search for packages. These are URLs searched in the orderthey are given (including local directories using the '[file://](file:///)' syntax or simply a path like '/home/conda/mychan' or '../mychan'). Then, the defaults or channels from .condarc are searched (unless --override-channels is given). You can use 'defaults' to get the default packages for conda. You can also use any name and the .condarc channel_alias value will be prepended. The default channel_alias is http://conda.anaconda.org/.

- --use-local

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

## Solver Mode Modifiers

- --all

  删除所有包，即整个环境。

- --features

  Remove features (instead of packages).

- --force-remove, --force

  强制删除包而不删除依赖于它的包。 使用此选项通常会使环境处于损坏和不一致状态。

- --no-pin

  Ignore pinned file.

## 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

## Output, Prompt, and Flow Control Options

- -d, --dry-run

  只显示本应该做的事情。

- --json

  将所有输出报告为 json。 适合使用 conda 编程。

- -q, --quiet

  不显示进度条

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次。

- -y, --yes

  不要求确认