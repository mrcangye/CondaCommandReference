# `conda package`

主要用于`conda`各种包的包管理

选项：

```
usage: conda package [-h] [-n ENVIRONMENT | -p PATH] [-w PATH [PATH ...]] [-r]
                     [-u] [--pkg-name PKG_NAME] [--pkg-version PKG_VERSION]
                     [--pkg-build PKG_BUILD]
```

## 命名参数

- -w, --which

  列出包所在路径

- -r, --reset

  删除所有未跟踪的文件并退出。

- -u, --untracked

  列出所有未跟踪的文件并退出。

- --pkg-name

  创建的包的包名。

- --pkg-version

  创建的包的包版本

- --pkg-build

  创建的包的构建号。

## 目标环境参数

- -n, --name

  环境名

- -p, --prefix

  环境所在全路径