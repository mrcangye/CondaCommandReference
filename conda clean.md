# conda clean

`conda clean`命令的主要功能是删除未使用的包或者缓存

它的选项标签有：

```bash
usage: conda clean [-h] [-a] [-i] [-p] [-t] [-f]
                   [-c TEMPFILES [TEMPFILES ...]] [-d] [--json] [-q] [-v] [-y]
```

## 删除选项

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

## 输出、提示和控制流选项

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