### `conda install`

将软件包安装到指定的 conda 环境中。

选项：

```
usage: conda install [-h] [--revision REVISION] [-n ENVIRONMENT | -p PATH]
                     [-c CHANNEL] [--use-local] [--override-channels]
                     [--repodata-fn REPODATA_FNS] [--strict-channel-priority]
                     [--no-channel-priority] [--no-deps | --only-deps]
                     [--no-pin] [--copy] [-C] [-k] [--offline] [-d] [--json]
                     [-q] [-v] [-y] [--download-only] [--show-channel-urls]
                     [--file FILE] [--force-reinstall]
                     [--freeze-installed | --update-deps | -S | --update-all | --update-specs]
                     [-m] [--clobber] [--dev]
                     [package_spec [package_spec ...]]
```

#### 包参数

- package_spec

  要在 conda 环境中安装或更新的软件包的名字。

#### 命名参数

- --revision

  恢复到指定的 REVISION。

- --file

  从给定文件中读取包版本。 可以重复使用（例如 --file=file1 --file=file2）。

- --dev

  在包装脚本中使用 sys.executable -m conda 而不是 CONDA_EXE。 这主要用于在我们针对旧 Python 版本测试新 conda 源的测试期间使用。

#### 目标环境参数

- -n, --name

  环境名字

- -p, --prefix

  环境的路径

#### 自定义源

- -c, --channel

  用于搜索包的源。 按照给定顺序搜索URL。包括使用`file`语法或简单路径的本地目录，然后搜索 `.condarc`文件中的默认值或源（除非给出了 --override-channels）。既可以使用`defaults`来获取`conda`的默认包。 也可以使用任何名字，并且`.condarc`文件中的` channel_alias `值将被添加。默认的`channel_alias`值请参阅 http://conda.anaconda.org/

- --use-local

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

- --repodata-fn

  指定远程服务器上的 repodata 名称。 Conda 将尝试你指定的任何内容，但如果你的规范与你在此处指定的内容不符，将退回到 repodata.json。 这用于使用时间范围减少的 repodata。 你可以多次通过此标志。 首先尝试最左边的条目，并自动为你添加 repodata.json 的后备。

#### Solver Mode Modifiers

- --strict-channel-priority

  如果具有相同名称的包出现在较高优先级源中，则不考虑较低优先级源中的包。

- --no-channel-priority

  Package version takes precedence over channel priority. Overrides the value given by conda config --show channel_priority.

  包版本优先于源优先级。 覆盖 `conda config --show channel_priority` 给出的值。

- --no-deps

  Do not install, update, remove, or change dependencies. This WILL lead to broken environments and inconsistent behavior. Use at your own risk.

  不安装、更新、删除或更改依赖项。 这将导致破坏环境，引发不一致。 风险自负。

- --only-deps

  只安装依赖项。

- --no-pin

  Ignore pinned file.

- --force-reinstall

  卸载并重新安装包，即使该包已存在于环境中。

- --freeze-installed, --no-update-deps

  不更新或更改已安装的依赖项。

- --update-deps

  更新依赖项。

- -S, --satisfied-skip-solve

  如果满足要求，提前退出并且不运行解释器。 还跳过由`aggressive_update_packages`配置的主动更新。 类似于`pip install`的默认行为。

- --update-all, --all

  更新环境中所有已安装的软件包。

- --update-specs

  根据提供的要求进行更新。

#### 包链接和安装时的选项

- --copy

  使用副本而不是硬链接或软链接安装所有软件包。

- -m, --mkdir

  如有必要，创建环境目录。

- --clobber

  允许破坏包内重叠的文件路径，并关闭相关警告。

#### 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

#### 输出、提示和控制流选项

- -d, --dry-run

  只显示应该做的事情。

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

  显示源网址。 覆盖`conda config --show show_channel_urls`给出的值。

