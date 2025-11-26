Windows10最恶心的地方就是频繁的进行系统自动更新，关又关不掉。选择拒绝更新吧，系统一直不停的提示系统更新啊更新啊的。选择更新吧，又可能会导致系统性能下降。甚至一些软件或网络打印机等相关设备又无法使用，然后就只能卸载更新。

所以，最好的做法就是彻底的禁止系统更新功能。

|**Note**|
|:----|
|下面内容是汇总网上各种教程得到，关闭Windows10系统更新有多种方式。非常建议将下面的步骤依次执行一次。|

# 关闭系统更新设置

按 “Windows + I” 键，打开 Windows 设置，单击“更新和安全”进入“Windows 更新”设置。继续点击“高级选项”：

![Settings_WindowsUpdateAdviceSetting.png](https://media.ituknown.org/windows-media/disable_windows_update/DisableSystemUpdateSetting/Settings_WindowsUpdateAdviceSetting.png)

在高级选项中将“更新选项”全部关闭：

![Settings_DisableUpdateOptions.png](https://media.ituknown.org/windows-media/disable_windows_update/DisableSystemUpdateSetting/Settings_DisableUpdateOptions.png)

**特别说明：** 暂停更新日期这里最好选择到最大。

# 关闭Windows Update服务

按“Windows + R”键，打开运行对话框，输入“services.msc”，回车确认进入系统服务窗口。在弹出的服务窗口中，找到“Windows Update”选项并双击打开：

![services_WindowsUpdateService.png](https://media.ituknown.org/windows-media/disable_windows_update/DisableWindowsUpdateService/services_WindowsUpdateService.png)

在“常规”项中，将“启动类型”设置为“禁用”（不要忘记点击“应用”）：

![services_WindowsUpdateService_StartType_Disable.png](https://media.ituknown.org/windows-media/disable_windows_update/DisableWindowsUpdateService/services_WindowsUpdateService_StartType_Disable.png)

在“恢复”项中，将图中框选的部分都设置为“无操作”，应用并确认。

![services_WindowsUpdateService_RecoverOperator.png](https://media.ituknown.org/windows-media/disable_windows_update/DisableWindowsUpdateService/services_WindowsUpdateService_RecoverOperator.png)

# 本地组策略编辑器

按“Windows + R”键，打开运行对话框，输入“gpedit.msc”，回车确认进入本地组策略编辑器。依次单击：

“计算机配置” > “管理模板” > “Windows组件” > “Windows更新”，分别找到“配置自动更新”和“删除使用所有 Windows 更新功能的访问权限”：

![gpedit_windows_update.png](https://media.ituknown.org/windows-media/disable_windows_update/gpedit/gpedit_windows_update.png)

在“配置自动更新”中，选择“已禁用”，应用并确认。

![gpedit_windows_update_disable_auto_update.png](https://media.ituknown.org/windows-media/disable_windows_update/gpedit/gpedit_windows_update_disable_auto_update.png)

在“删除使用所有 Windows 更新功能的访问权限”中，选择“已启用”，应用并确认。

![gpedit_windows_update_enable_delete.png](https://media.ituknown.org/windows-media/disable_windows_update/gpedit/gpedit_windows_update_enable_delete.png)

# 任务计划程序

按“Windows + R”键，打开运行对话框，输入“taskschd.msc”，回车确认进入任务计划程序窗口。依次单击：

“任务计划程序库” > “Microsoft” > “Windows” > “WindowsUpdate”。

选中“Schedule Start”，并在“所选项”中单击“禁用”：

![schedule_task.png](https://media.ituknown.org/windows-media/disable_windows_update/taskschd/schedule_task.png)

# 注册表编辑器

按“Windows + R”键，打开运行对话框，输入“regedit.exe”，回车确认进入注册表编辑器。

在首部地址栏输入： `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\UsoSvc` （或依次点击）进入到 UsoSvc。

分别找到 “Start” 和 “FailureActions”：

![regedit_UsoSvc.png](https://media.ituknown.org/windows-media/disable_windows_update/regedit/regedit_UsoSvc.png)

双击“Start”，在弹出的窗口中将“数值数据”改为“4”，并单击“确定”：

![regedit_UsoSvc_Start4.png](https://media.ituknown.org/windows-media/disable_windows_update/regedit/regedit_UsoSvc_Start4.png)

双击“FailureActions”，在弹出的窗口中将“00000010”和“00000018”行中的第五个数值（框选的的部分），由原来的“01”改为“00”，再单击“确定”。

![regedit_UsoSvc_FailureActions00.png](https://media.ituknown.org/windows-media/disable_windows_update/regedit/regedit_UsoSvc_FailureActions00.png)

# 效果

最后来看下效果：

![result.png](https://media.ituknown.org/windows-media/disable_windows_update/result.png)

还想给我偷偷更新？死心吧你！
