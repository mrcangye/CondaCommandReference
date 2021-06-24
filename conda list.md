# `conda list`

列出 conda 环境中的包。

选项：

```
usage: conda list [-h] [-n ENVIRONMENT | -p PATH] [--json] [-v] [-q]
                  [--show-channel-urls] [-c] [-f] [--explicit] [--md5] [-e]
                  [-r] [--no-pip]
                  [regex]
```

## 位置参数

- regex

  仅列出与正则表达式匹配的包。

## 命名参数

- --show-channel-urls

  显示源网址。 覆盖`conda config --show show_channel_urls`给出的值。

- -c, --canonical

  仅输出包的规范名称。 意味着 --no-pip。

- -f, --full-name

  仅仅搜索全名。

- --explicit

  明确列出所有使用 URL 的已安装 conda（输出可由 conda create --file 使用）。

- --md5

  使用 --explicit 时添加 MD5 哈希和

- -e, --export

  Output requirement string only (output may be used by conda create --file).

  输出仅为字符串（输出使用 conda create --file ）。

- -r, --revisions

  列出修订历史后退出。

- --no-pip

  不包含仅使用 pip 安装的软件包。

## 目标环境参数

- -n, --name

  环境名

- -p, --prefix

  环境位置的全路径

## 输出、提示和控制流选项

- --json

  Report all output as json. Suitable for using conda programmatically.

- -v, --verbose

  Use once for info, twice for debug, three times for trace.

- -q, --quiet

  Do not display progress bar.

