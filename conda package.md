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