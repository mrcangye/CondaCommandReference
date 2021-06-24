# `conda config`

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

## 输出、提示和控制流选项

- --json

  输出为 json格式，方便conda调用

- -v, --verbose

  可以多次使用。 INFO 一次，DEBUG 两次，TRACE 三次

- -q, --quiet

  不显示进度条

## 配置文件位置设定

如果没有这些标志中的任意一个，那么`conda`将会使用位于`C:\Users\你的用户名`的用户配置文件。linux请在`/home/docs/.condarc`查找

- --system

  将系统全局配置文件写到`/home/docs/checkouts/readthedocs.org/user_builds/continuumio-conda/conda/latest/.condarc`目录下。windows目录不详

- --env

  将配置文件写到虚拟环境中，如果环境未激活就写到用户配置文件目录下`C:\Users\你的用户名`，linux请在`/home/docs/.condarc`查找

- --file

  写到给定的文件中

## 配置子命令

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

## 配置修饰符

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