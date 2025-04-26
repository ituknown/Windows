# 前言

Win10系统中自带 Windows Defender 杀毒软件，很多人都特别的排斥。其一是扫描的频率太高，占用大量CPU。其二是有些文件不经过任何提示就直接删除（比如 Windows 激活工具 KMS🌚🌚🌚）。

想要彻底的关闭 Windows Defender 主要有两种办法，其一是通过修改本地用户组策略来实现，其二就是修改注册表。

| **NOTE**                                                                                 |
|:-----------------------------------------------------------------------------------------|
| 网上有很多关闭 Windows Defender 的软件，其原理也是通过修改本地用户组策略或注册表来实现的。 |

# 通过修改本地用户组策略实现关闭defender安全中心

首先要找到本地用户组策略，可以使用下面两种方式打开：

使用快捷键 win+R，输入 `gpedit.msc` 点击确认打开本地用户组策略：

![gpedit-1673326054fE7qlUcy.png](https://ituknown.cn/windows-media/disable_windows_defender/gpedit-1673326054fE7qlUcy.png)

或直接在Windows搜索中搜索“本地组策略”：

![search-groupedit-1673326077cO3AKdh5.png](https://ituknown.cn/windows-media/disable_windows_defender/search-groupedit-1673326077cO3AKdh5.png)

打开本地组策略之后依次选择 计算机配置 » 管理模板 » Windows组件 » Microsoft Defender防病毒 » 实时保护。

然后选择右边栏设置中的 “关闭实时保护”，右键编辑，之后选择 “已启用”（默认为未配置）并依次点击 应用 » 确认：

![close-realtimedefender-1673326100eA5tU7ub.png](https://ituknown.cn/windows-media/disable_windows_defender/close-realtimedefender-1673326100eA5tU7ub.png)

现在再到安全设置中看下实时保护，此时就会看到已被关闭且无法手动打开（如果你看不到该效果尝试关机重启）：

![close-realtime-defender-done-16733382649bh4KZg.png](https://ituknown.cn/windows-media/disable_windows_defender/close-realtime-defender-done-16733382649bh4KZg.png)

# 使用Defender Control工具关闭安全中心

Defender Control 是Github开源的一款小巧精悍的一键开启/关闭Windows Defender工具，目前仅支持Win10和早期的Win11。

仓库地址是：https://github.com/qtkite/defender-control

使用起来特别简单，直接在 [release](https://github.com/qtkite/defender-control/releases) 页面下载 exe 程序即可：

![defender-control-release.png](https://ituknown.cn/windows-media/disable_windows_defender/defender-control-release.png)

- disable-defender.exe 用于禁用 Windows Defender
- enable-defender.exe  用于开启 Windows Defender

下载后右键使用超级管理员运行即可！

|**注意**|
|:-------|
|系统默认会将该工具识别为病毒软件，在下载前记得先在设置面板中将“病毒和威胁防护»实时保护”关闭掉！|
