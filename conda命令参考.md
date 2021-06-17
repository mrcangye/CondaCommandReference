# conda命令参考

## 前言

`conda`命令参考，来源于英文官方文档[Command reference](https://docs.conda.io/projects/conda/en/latest/commands.html#)

值得一提的是，`conda`提供了命令行帮助模式，当为某个命令犹豫不决的时候，不妨试试在这个命令的后面加上`--help`标签

举个栗子

`conda install --help`

在终端输入会显示该命令的格式和注解，当然，**是英文的**

## conda 主要命令

### conda clean

`conda clean`命令的主要功能是删除未使用的包或者缓存

它的选项标签有：

```bash
usage: conda clean [-h] [-a] [-i] [-p] [-t] [-f]
                   [-c TEMPFILES [TEMPFILES ...]] [-d] [--json] [-q] [-v] [-y]
```

#### 删除选项

- -a, --all

  删除索引缓存、锁定的文件、未使用的缓存包和压缩包

- -i, --index-cache

  删除索引缓存

- -p, --packages

  从可写的包缓存中删除未使用的包。

  警告：通过符号链接方式安装的包是不会被检查的

- -t, --tarballs

  删除缓存压缩包

- -f, --force-pkgs-dirs

  删除所有可写的包缓存。 此选项不包含在 --all 标志中。

  警告：这将破坏使用符号链接安装的包回到包缓存的环境。

- -c, --tempfiles

  删除由于正在使用而无法提前删除的临时文件。 参数是应该找到删除文件的路径。

#### 输出、提示和控制流选项

- -d, --dry-run

  只显示应该完成的事情

- --json

  输出为 json格式，方便conda调用

- -q, --quiet

  不显示进度条

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次

- -y, --yes

  不要求安装确认

### `conda config`

这个命令实际上用于用户配置文件`conda`的配置的，当然也可以直接在用户配置文件`.condarc`上修改，如果是windows，用户配置文件应该在`C:\Users\你的用户名`目录下。linux请在`/home/docs/.condarc`查找

可选命令如下

```bash
usage: conda config [-h] [--json] [-v] [-q] [--system | --env | --file FILE]
                    [--show [SHOW [SHOW ...]] | --show-sources | --validate |
                    --describe [DESCRIBE [DESCRIBE ...]] | --write-default]
                    [--get [KEY [KEY ...]] | --append KEY VALUE | --prepend
                    KEY VALUE | --set KEY VALUE | --remove KEY VALUE |
                    --remove-key KEY | --stdin]
```

#### 输出、提示和控制流选项

- --json

  输出为 json格式，方便conda调用

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次

- -q, --quiet

  不显示进度条

#### 配置文件位置设定

如果没有这些标志中的任意一个，那么`conda`将会使用位于`C:\Users\你的用户名`的用户配置文件。linux请在`/home/docs/.condarc`查找

- --system

  将系统全局配置文件写到`/home/docs/checkouts/readthedocs.org/user_builds/continuumio-conda/conda/latest/.condarc`目录下。windows目录不详

- --env

  将配置文件写到虚拟环境中，如果环境未激活就写到用户配置文件目录下`C:\Users\你的用户名`，linux请在`/home/docs/.condarc`查找

- --file

  写到给定的文件中

#### 配置子命令

- --show

  显示计算和编译的配置值。 如果没有给出参数，则显示所有配置值的信息。

- --show-sources

  显示所有已识别的配置源。

- --validate

  验证所有配置源。

- --describe

  显示给定的配置参数。 如果没有给出参数，则显示所有配置参数的信息。

- --write-default

  将默认配置写入文件。相当于`conda config --describe > ~/.condarc`

#### 配置修饰符

- --get

  获取配置值。

- --append

  在列表键末尾添加一个配置值。

- --prepend, --add

  在列表键开头添加一个配置值。

- --set

  设置布尔值或字符串键

- --remove

  从列表键中删除配置值。 这将删除该值的所有实例。

- --remove-key

  删除配置键（及其所有值）。

- --stdin

  应用通过输入流提供的yaml配置信息。

### `conda create`

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

#### 位置参数

- package_spec

  要在 conda 环境中安装或更新的软件包的名字

#### 命名参数

- --clone

  现有本地环境的路径或名字

- --file

  从给定文件中读取包版本，可以通过重复使用。举个栗子`--file=file1 --file=file2`

- --dev

  在脚本中使用`sys.executable -m conda` 而不是 conda程序。 主要用于针对旧 Python 版本测试新 conda 源的开发测试期间使用。

#### 目标环境的选项

- -n, --name

  环境名字

- -p, --prefix

  环境的全路径

#### 自定义源

- -c, --channel

  用于搜索包的源。 按照给定顺序搜索URL。包括使用`file`语法或简单路径的本地目录，然后搜索 `.condarc`文件中的默认值或源（除非给出了 --override-channels）。既可以使用`defaults`来获取`conda`的默认包。 也可以使用任何名字，并且`.condarc`文件中的` channel_alias `值将被添加。默认的`channel_alias`值请参阅 http://conda.anaconda.org/

- --use-local

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.
  
  指定远程服务器上的 repodata 名称。 Conda 将尝试你指定的任何内容，但如果你的规范与你在此处指定的内容不符，将退回到 repodata.json。 这用于使用时间范围减少的 repodata。 你可以多次通过此标志。 首先尝试最左边的条目，并自动为你添加 repodata.json 的后备。

#### Solver Mode Modifiers

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

#### 包链接和安装时的选项

- --copy

  使用副本而不是硬链接或软链接安装所有软件包。

#### 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

#### 输出、提示和控制流选项

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



### `conda info`

显示有关conda 安装的信息。

选项有：

```
usage: conda info [-h] [--json] [-v] [-q] [-a] [--base] [-e] [-s]
                  [--unsafe-channels]
```

#### 命名参数

- -a, --all

  显示所有的信息

- --base

  显示基本环境路径。

- -e, --envs

  List all known conda environments.

  列出所有已知的conda 环境

- -s, --system

  列出环境变量

- --unsafe-channels

  现示不安全的源列表。

#### 输出、提示和控制流选项

- --json

  输出为 json格式，方便conda调用

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次

- -q, --quiet

  不显示进度条

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

#### Target Environment Specification

- -n, --name

  Name of environment.

- -p, --prefix

  Full path to environment location (i.e. prefix).

#### Channel Customization

- -c, --channel

  Additional channel to search for packages. These are URLs searched in the orderthey are given (including local directories using the '[file://](file:///)' syntax or simply a path like '/home/conda/mychan' or '../mychan'). Then, the defaults or channels from .condarc are searched (unless --override-channels is given). You can use 'defaults' to get the default packages for conda. You can also use any name and the .condarc channel_alias value will be prepended. The default channel_alias is http://conda.anaconda.org/.

- --use-local

  Use locally built packages. Identical to '-c local'.

- --override-channels

  Do not search default or .condarc channels. Requires --channel.

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

#### Solver Mode Modifiers

- --strict-channel-priority

  Packages in lower priority channels are not considered if a package with the same name appears in a higher priority channel.

- --no-channel-priority

  Package version takes precedence over channel priority. Overrides the value given by conda config --show channel_priority.

- --no-deps

  Do not install, update, remove, or change dependencies. This WILL lead to broken environments and inconsistent behavior. Use at your own risk.

- --only-deps

  Only install dependencies.

- --no-pin

  Ignore pinned file.

- --force-reinstall

  Ensure that any user-requested package for the current operation is uninstalled and reinstalled, even if that package already exists in the environment.

- --freeze-installed, --no-update-deps

  Do not update or change already-installed dependencies.

- --update-deps

  Update dependencies.

- -S, --satisfied-skip-solve

  Exit early and do not run the solver if the requested specs are satisfied. Also skips aggressive updates as configured by 'aggressive_update_packages'. Similar to the default behavior of 'pip install'.

- --update-all, --all

  Update all installed packages in the environment.

- --update-specs

  Update based on provided specifications.

#### Package Linking and Install-time Options

- --copy

  Install all packages using copies instead of hard- or soft-linking.

- -m, --mkdir

  Create the environment directory if necessary.

- --clobber

  Allow clobbering of overlapping file paths within packages, and suppress related warnings.

#### Networking Options

- -C, --use-index-cache

  Use cache of channel index files, even if it has expired.

- -k, --insecure

  Allow conda to perform "insecure" SSL connections and transfers. Equivalent to setting 'ssl_verify' to 'false'.

- --offline

  Offline mode. Don't connect to the Internet.

#### 输出、提示和控制流选项

- -d, --dry-run

  Only display what would have been done.

- --json

  输出为 json格式，方便conda调用

- -q, --quiet

  不显示进度条

- -v, --verbose

  Can be used multiple times. Once for INFO, twice for DEBUG, three times for TRACE.

- -y, --yes

  不要求安装确认

- --download-only

  Solve an environment and ensure package caches are populated, but exit prior to unlinking and linking packages into the prefix.

- --show-channel-urls

  Show channel urls. Overrides the value given by conda config --show show_channel_urls.



Examples:

> conda install -n myenv scipy



# `conda list`



List linked packages in a conda environment.

Options:



```
usage: conda list [-h] [-n ENVIRONMENT | -p PATH] [--json] [-v] [-q]
                  [--show-channel-urls] [-c] [-f] [--explicit] [--md5] [-e]
                  [-r] [--no-pip]
                  [regex]
```

## Positional Arguments

- regex

  List only packages matching this regular expression.

## Named Arguments

- --show-channel-urls

  Show channel urls. Overrides the value given by conda config --show show_channel_urls.

- -c, --canonical

  Output canonical names of packages only. Implies --no-pip.

- -f, --full-name

  Only search for full names, i.e., ^<regex>$.

- --explicit

  List explicitly all installed conda packaged with URL (output may be used by conda create --file).

- --md5

  Add MD5 hashsum when using --explicit

- -e, --export

  Output requirement string only (output may be used by conda create --file).

- -r, --revisions

  List the revision history and exit.

- --no-pip

  Do not include pip-only installed packages.

## Target Environment Specification

- -n, --name

  Name of environment.

- -p, --prefix

  Full path to environment location (i.e. prefix).

## Output, Prompt, and Flow Control Options

- --json

  Report all output as json. Suitable for using conda programmatically.

- -v, --verbose

  Use once for info, twice for debug, three times for trace.

- -q, --quiet

  Do not display progress bar.



Examples:

List all packages in the current environment:

> conda list

List all packages installed into the environment 'myenv':

> conda list -n myenv

Save packages for future use:

> conda list --export > package-list.txt

Reinstall packages from an export file:

> conda create -n myenv --file package-list.txt



[Next ](https://docs.conda.io/projects/conda/en/latest/commands/package.html)[ Previous](https://docs.conda.io/projects/conda/en/latest/commands/install.html)

# `conda package`



Low-level conda package utility. (EXPERIMENTAL)

Options:



```
usage: conda package [-h] [-n ENVIRONMENT | -p PATH] [-w PATH [PATH ...]] [-r]
                     [-u] [--pkg-name PKG_NAME] [--pkg-version PKG_VERSION]
                     [--pkg-build PKG_BUILD]
```

## Named Arguments

- -w, --which

  Given some PATH print which conda package the file came from.

- -r, --reset

  Remove all untracked files and exit.

- -u, --untracked

  Display all untracked files and exit.

- --pkg-name

  Package name of the created package.

- --pkg-version

  Package version of the created package.

- --pkg-build

  Package build number of the created package.

## Target Environment Specification

- -n, --name

  Name of environment.

- -p, --prefix

  Full path to environment location (i.e. prefix).

[Next ](https://docs.conda.io/projects/conda/en/latest/commands/remove.html)[ Previous](https://docs.conda.io/projects/conda/en/latest/commands/list.html)

# `conda remove`



Remove a list of packages from a specified conda environment.

> This command will also remove any package that depends on any of the specified packages as well---unless a replacement can be found without that dependency. If you wish to skip this dependency checking and remove just the requested packages, add the '--force' option. Note however that this may result in a broken environment, so use this with caution.

Options:



```
usage: conda remove [-h] [-n ENVIRONMENT | -p PATH] [-c CHANNEL] [--use-local]
                    [--override-channels] [--repodata-fn REPODATA_FNS] [--all]
                    [--features] [--force-remove] [--no-pin] [-C] [-k]
                    [--offline] [-d] [--json] [-q] [-v] [-y] [--dev]
                    [package_name [package_name ...]]
```

## Positional Arguments

- package_name

  Package names to remove from the environment.

## Named Arguments

- --dev

  Use sys.executable -m conda in wrapper scripts instead of CONDA_EXE. This is mainly for use during tests where we test new conda source against old Python versions.

## Target Environment Specification

- -n, --name

  Name of environment.

- -p, --prefix

  Full path to environment location (i.e. prefix).

## Channel Customization

- -c, --channel

  Additional channel to search for packages. These are URLs searched in the orderthey are given (including local directories using the '[file://](file:///)' syntax or simply a path like '/home/conda/mychan' or '../mychan'). Then, the defaults or channels from .condarc are searched (unless --override-channels is given). You can use 'defaults' to get the default packages for conda. You can also use any name and the .condarc channel_alias value will be prepended. The default channel_alias is http://conda.anaconda.org/.

- --use-local

  Use locally built packages. Identical to '-c local'.

- --override-channels

  Do not search default or .condarc channels. Requires --channel.

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

## Solver Mode Modifiers

- --all

  Remove all packages, i.e., the entire environment.

- --features

  Remove features (instead of packages).

- --force-remove, --force

  Forces removal of a package without removing packages that depend on it. Using this option will usually leave your environment in a broken and inconsistent state.

- --no-pin

  Ignore pinned file.

## Networking Options

- -C, --use-index-cache

  Use cache of channel index files, even if it has expired.

- -k, --insecure

  Allow conda to perform "insecure" SSL connections and transfers. Equivalent to setting 'ssl_verify' to 'false'.

- --offline

  Offline mode. Don't connect to the Internet.

## Output, Prompt, and Flow Control Options

- -d, --dry-run

  Only display what would have been done.

- --json

  Report all output as json. Suitable for using conda programmatically.

- -q, --quiet

  Do not display progress bar.

- -v, --verbose

  Can be used multiple times. Once for INFO, twice for DEBUG, three times for TRACE.

- -y, --yes

  Do not ask for confirmation.



Examples:

> conda remove -n myenv scipy

# `conda search`



- Search for packages and display associated information.

  The input is a MatchSpec, a query language for conda packages. See examples below.

Options:



```
usage: conda search [-h] [--envs] [-i] [--subdir SUBDIR] [-c CHANNEL]
                    [--use-local] [--override-channels]
                    [--repodata-fn REPODATA_FNS] [-C] [-k] [--offline]
                    [--json] [-v] [-q]
```

## Named Arguments

- --envs

  Search all of the current user's environments. If run as Administrator (on Windows) or UID 0 (on unix), search all known environments on the system.

- -i, --info

  Provide detailed information about each package.

- --subdir, --platform

  Search the given subdir. Should be formatted like 'osx-64', 'linux-32', 'win-64', and so on. The default is to search the current platform.

## Channel Customization

- -c, --channel

  Additional channel to search for packages. These are URLs searched in the orderthey are given (including local directories using the '[file://](file:///)' syntax or simply a path like '/home/conda/mychan' or '../mychan'). Then, the defaults or channels from .condarc are searched (unless --override-channels is given). You can use 'defaults' to get the default packages for conda. You can also use any name and the .condarc channel_alias value will be prepended. The default channel_alias is http://conda.anaconda.org/.

- --use-local

  Use locally built packages. Identical to '-c local'.

- --override-channels

  Do not search default or .condarc channels. Requires --channel.

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

## Networking Options

- -C, --use-index-cache

  Use cache of channel index files, even if it has expired.

- -k, --insecure

  Allow conda to perform "insecure" SSL connections and transfers. Equivalent to setting 'ssl_verify' to 'false'.

- --offline

  Offline mode. Don't connect to the Internet.

## Output, Prompt, and Flow Control Options

- --json

  Report all output as json. Suitable for using conda programmatically.

- -v, --verbose

  Use once for info, twice for debug, three times for trace.

- -q, --quiet

  Do not display progress bar.



Examples:

Search for a specific package named 'scikit-learn':

> conda search scikit-learn

Search for packages containing 'scikit' in the package name:

> conda search *scikit*

Note that your shell may expand '*' before handing the command over to conda. Therefore it is sometimes necessary to use single or double quotes around the query.

> conda search '*scikit' conda search "\*scikit*"

Search for packages for 64-bit Linux (by default, packages for your current platform are shown):

> conda search numpy[subdir=linux-64]

Search for a specific version of a package:

> conda search 'numpy>=1.12'

Search for a package on a specific channel

> conda search conda-forge::numpy conda search 'numpy[channel=conda-forge, subdir=osx-64]'



[Next ](https://docs.conda.io/projects/conda/en/latest/commands/update.html)[ Previous](https://docs.conda.io/projects/conda/en/latest/commands/remove.html)



# `conda update`



Updates conda packages to the latest compatible version.

> This command accepts a list of package names and updates them to the latest versions that are compatible with all other packages in the environment.
>
> Conda attempts to install the newest versions of the requested packages. To accomplish this, it may update some packages that are already installed, or install additional packages. To prevent existing packages from updating, use the --no-update-deps option. This may force conda to install older versions of the requested packages, and it does not prevent additional dependency packages from being installed.

Options:



```
usage: conda update [-h] [-n ENVIRONMENT | -p PATH] [-c CHANNEL] [--use-local]
                    [--override-channels] [--repodata-fn REPODATA_FNS]
                    [--strict-channel-priority] [--no-channel-priority]
                    [--no-deps | --only-deps] [--no-pin] [--copy] [-C] [-k]
                    [--offline] [-d] [--json] [-q] [-v] [-y] [--download-only]
                    [--show-channel-urls] [--file FILE] [--force-reinstall]
                    [--freeze-installed | --update-deps | -S | --update-all | --update-specs]
                    [--clobber]
                    [package_spec [package_spec ...]]
```

## Positional Arguments

- package_spec

  Packages to install or update in the conda environment.

## Named Arguments

- --file

  Read package versions from the given file. Repeated file specifications can be passed (e.g. --file=file1 --file=file2).

## Target Environment Specification

- -n, --name

  Name of environment.

- -p, --prefix

  Full path to environment location (i.e. prefix).

## Channel Customization

- -c, --channel

  Additional channel to search for packages. These are URLs searched in the orderthey are given (including local directories using the '[file://](file:///)' syntax or simply a path like '/home/conda/mychan' or '../mychan'). Then, the defaults or channels from .condarc are searched (unless --override-channels is given). You can use 'defaults' to get the default packages for conda. You can also use any name and the .condarc channel_alias value will be prepended. The default channel_alias is http://conda.anaconda.org/.

- --use-local

  Use locally built packages. Identical to '-c local'.

- --override-channels

  Do not search default or .condarc channels. Requires --channel.

- --repodata-fn

  Specify name of repodata on remote server. Conda will try whatever you specify, but will ultimately fall back to repodata.json if your specs are not satisfiable with what you specify here. This is used to employ repodata that is reduced in time scope. You may pass this flag more than once. Leftmost entries are tried first, and the fallback to repodata.json is added for you automatically.

## Solver Mode Modifiers

- --strict-channel-priority

  Packages in lower priority channels are not considered if a package with the same name appears in a higher priority channel.

- --no-channel-priority

  Package version takes precedence over channel priority. Overrides the value given by conda config --show channel_priority.

- --no-deps

  Do not install, update, remove, or change dependencies. This WILL lead to broken environments and inconsistent behavior. Use at your own risk.

- --only-deps

  Only install dependencies.

- --no-pin

  Ignore pinned file.

- --force-reinstall

  Ensure that any user-requested package for the current operation is uninstalled and reinstalled, even if that package already exists in the environment.

- --freeze-installed, --no-update-deps

  Do not update or change already-installed dependencies.

- --update-deps

  Update dependencies.

- -S, --satisfied-skip-solve

  Exit early and do not run the solver if the requested specs are satisfied. Also skips aggressive updates as configured by 'aggressive_update_packages'. Similar to the default behavior of 'pip install'.

- --update-all, --all

  Update all installed packages in the environment.

- --update-specs

  Update based on provided specifications.

## Package Linking and Install-time Options

- --copy

  Install all packages using copies instead of hard- or soft-linking.

- --clobber

  Allow clobbering of overlapping file paths within packages, and suppress related warnings.

## Networking Options

- -C, --use-index-cache

  Use cache of channel index files, even if it has expired.

- -k, --insecure

  Allow conda to perform "insecure" SSL connections and transfers. Equivalent to setting 'ssl_verify' to 'false'.

- --offline

  Offline mode. Don't connect to the Internet.

## Output, Prompt, and Flow Control Options

- -d, --dry-run

  Only display what would have been done.

- --json

  Report all output as json. Suitable for using conda programmatically.

- -q, --quiet

  Do not display progress bar.

- -v, --verbose

  Can be used multiple times. Once for INFO, twice for DEBUG, three times for TRACE.

- -y, --yes

  Do not ask for confirmation.

- --download-only

  Solve an environment and ensure package caches are populated, but exit prior to unlinking and linking packages into the prefix.

- --show-channel-urls

  Show channel urls. Overrides the value given by conda config --show show_channel_urls.



Examples:

> conda update -n myenv scipy



[Next ](https://docs.conda.io/projects/conda/en/latest/glossary.html)[ Previous](https://docs.conda.io/projects/conda/en/latest/commands/search.html)



## [Conda vs. pip vs. virtualenv commands](https://docs.conda.io/projects/conda/en/latest/commands.html#id2)

If you have used pip and virtualenv in the past, you can use conda to perform all of the same operations. Pip is a package manager and virtualenv is an environment manager. Conda is both.

Scroll to the right to see the entire table.

| Task                                 | Conda package and environment manager command         | Pip package manager command                                  | Virtualenv environment manager command                |
| ------------------------------------ | ----------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------- |
| Install a package                    | `conda install $PACKAGE_NAME`                         | `pip install $PACKAGE_NAME`                                  | X                                                     |
| Update a package                     | `conda update --name $ENVIRONMENT_NAME $PACKAGE_NAME` | `pip install --upgrade $PACKAGE_NAME`                        | X                                                     |
| Update package manager               | `conda update conda`                                  | Linux/macOS: `pip install -U pip` Win: `python -m pip install -U pip` | X                                                     |
| Uninstall a package                  | `conda remove --name $ENVIRONMENT_NAME $PACKAGE_NAME` | `pip uninstall $PACKAGE_NAME`                                | X                                                     |
| Create an environment                | `conda create --name $ENVIRONMENT_NAME python`        | X                                                            | `cd $ENV_BASE_DIR; virtualenv $ENVIRONMENT_NAME`      |
| Activate an environment              | `conda activate $ENVIRONMENT_NAME`*                   | X                                                            | `source $ENV_BASE_DIR/$ENVIRONMENT_NAME/bin/activate` |
| Deactivate an environment            | `conda deactivate`                                    | X                                                            | `deactivate`                                          |
| Search available packages            | `conda search $SEARCH_TERM`                           | `pip search $SEARCH_TERM`                                    | X                                                     |
| Install package from specific source | `conda install --channel $URL $PACKAGE_NAME`          | `pip install --index-url $URL $PACKAGE_NAME`                 | X                                                     |
| List installed packages              | `conda list --name $ENVIRONMENT_NAME`                 | `pip list`                                                   | X                                                     |
| Create requirements file             | `conda list --export`                                 | `pip freeze`                                                 | X                                                     |
| List all environments                | `conda info --envs`                                   | X                                                            | Install virtualenv wrapper, then `lsvirtualenv`       |
| Install other package manager        | `conda install pip`                                   | `pip install conda`                                          | X                                                     |
| Install Python                       | `conda install python=x.x`                            | X                                                            | X                                                     |
| Update Python                        | `conda update python`*                                | X                                                            | X                                                     |

\* `conda activate` only works on conda 4.6 and later versions. For conda versions prior to 4.6, type:

> - Windows: `activate`
> - Linux and macOS: `source activate`

\* `conda update python` updates to the most recent in the series, so any Python 2.x would update to the latest 2.x and any Python 3.x to the latest 3.x.

