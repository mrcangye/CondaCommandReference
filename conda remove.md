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

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

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

## 网络选项

- -C, --use-index-cache

  使用源索引文件的缓存，即使它已过期。

- -k, --insecure

  允许 conda 执行不安全的 SSL 连接和传输。 相当于将`ssl_verify`设置为`false`。

- --offline

  离线模式，不连接网络。

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