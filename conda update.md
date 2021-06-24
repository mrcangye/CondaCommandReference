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

  使用本地构建的包。与`-c local`同样的作用

- --override-channels

  不搜索默认或 `.condarc` 源。要求 `--channel`

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

- --download-only

  Solve an environment and ensure package caches are populated, but exit prior to unlinking and linking packages into the prefix.

- --show-channel-urls

  显示源网址。 覆盖`conda config --show show_channel_urls`给出的值。