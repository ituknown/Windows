
![task_memory.png](http://windows-media.knowledge.ituknown.cn/memory_compress/task_memory.png)

# 查看内存压缩状态

```PowerShell
Get-MMAgent
```

示例：

```PowerShell
> Get-MMAgent

ApplicationLaunchPrefetching : True
ApplicationPreLaunch         : True
MaxOperationAPIFiles         : 256
MemoryCompression            : True  < 开启压缩
OperationAPI                 : True
PageCombining                : False
PSComputerName               :
```

# 禁用内存压缩

```PowerShell
Disable-MMAgent -mc
```

示例：

![disable_mmagent.png](http://windows-media.knowledge.ituknown.cn/memory_compress/disable_mmagent.png)
# 启用内存压缩

```
Enable-MMAgent -mc
```