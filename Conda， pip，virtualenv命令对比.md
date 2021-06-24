### Conda， pip，virtualenv命令对比 

如果你过去使用过 pip 和 virtualenv，则可以使用 conda 执行所有相同的操作。 Pip 是一个包管理器，virtualenv 是一个环境管理器。 conda两者的功能都有。

| 任务名                | Conda 包和环境管理器命令                              | Pip 包管理器命令                                             | Virtualenv 环境管理器命令                             |
| --------------------- | ----------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------- |
| 安装包                | `conda install $PACKAGE_NAME`                         | `pip install $PACKAGE_NAME`                                  | X                                                     |
| 更新包                | `conda update --name $ENVIRONMENT_NAME $PACKAGE_NAME` | `pip install --upgrade $PACKAGE_NAME`                        | X                                                     |
| 更新包管理器          | `conda update conda`                                  | Linux/macOS: `pip install -U pip` Win: `python -m pip install -U pip` | X                                                     |
| 卸载包                | `conda remove --name $ENVIRONMENT_NAME $PACKAGE_NAME` | `pip uninstall $PACKAGE_NAME`                                | X                                                     |
| 创建一个环境          | `conda create --name $ENVIRONMENT_NAME python`        | X                                                            | `cd $ENV_BASE_DIR; virtualenv $ENVIRONMENT_NAME`      |
| 激活环境              | `conda activate $ENVIRONMENT_NAME`*                   | X                                                            | `source $ENV_BASE_DIR/$ENVIRONMENT_NAME/bin/activate` |
| 退出环境              | `conda deactivate`                                    | X                                                            | `deactivate`                                          |
| 寻找可用包            | `conda search $SEARCH_TERM`                           | `pip search $SEARCH_TERM`                                    | X                                                     |
| 从指定源安装包        | `conda install --channel $URL $PACKAGE_NAME`          | `pip install --index-url $URL $PACKAGE_NAME`                 | X                                                     |
| 列出已安装包          | `conda list --name $ENVIRONMENT_NAME`                 | `pip list`                                                   | X                                                     |
| 创建requirements 文件 | `conda list --export`                                 | `pip freeze`                                                 | X                                                     |
| 列出所有的环境        | `conda info --envs`                                   | X                                                            | Install virtualenv wrapper, then `lsvirtualenv`       |
| 安装其他的包管理器    | `conda install pip`                                   | `pip install conda`                                          | X                                                     |
| 安装python            | `conda install python=x.x`                            | X                                                            | X                                                     |
| 更新python            | `conda update python`*                                | X                                                            | X                                                     |



