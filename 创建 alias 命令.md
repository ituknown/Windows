Windows 创建 alias 可以借助批处理脚本（bat）实现。只需要将目标命令写到 bat 文件中，并加入环境变量中即可（文件名就是对应的 alias 命令）。

以 wsl 启动 ubuntu 为例，批处理脚本如下：

```bat
@echo off
wsl.exe -d ubuntu %*
```

脚本文件名为 ubuntu.bat，加入环境变量之后，只需要在任意命令终端执行 `ubuntu.bat` 命令即可立刻打开 ubuntu，及其方便。

其中，`%*` 是一个特殊的变量，表示将所有参数传递给命令。例如，如果你有一个脚本（比如 myscript.bat），你可以这样调用它：

```bat
myscript.bat arg1 arg2 arg3
```