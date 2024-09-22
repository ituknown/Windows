# 前言

OneDrive 在某个版本升级之后意外发现侧边栏出现了两个 OneDrive 图标：

![OneDriveSidebarTray.png](http://windows-media.knowledge.ituknown.cn/onedrive/disable_sidebar_tray/OneDriveSidebarTray.png)

这两个图标分别是 OneDrive for Business 和 OneDrive For Personal。如果安装的是家庭版应该不会出现这个问题

老实说，删又删不掉，卸载又卸载不了，看着是真特码难受！不给有些博主找到了解决办法，这里完全是搬运，总结下来有两种解决方式，总有一款适合你！

# 方法一

Win + R 打开运行，输入 “regedit” 打开注册表。定位到：“计算机\HKEY_CLASSES_ROOT\CLSID”。按住 Ctrl + F 搜索 OneDrive：

![CLSID_search_OneDrive.png](http://windows-media.knowledge.ituknown.cn/onedrive/disable_sidebar_tray/method1/CLSID_search_OneDrive.png)

通常会定义为到内部有一个 System.IsPinnedToNameSpaceTree 属性的 {ID} 的条目，将改值修改为 0：

![Set_SystemIsPinnedToNameSpaceTree_0.png](http://windows-media.knowledge.ituknown.cn/onedrive/disable_sidebar_tray/method1/Set_SystemIsPinnedToNameSpaceTree_0.png)

关机重启之后就会看到只会有一个 OneDrive 了~

| **Note**                      |
| :---------------------------- |
| 如果你没定位到改条目，说明该方法不适合你，考虑使用方法二。 |
# 方法二

还是使用 Win + R 打开运行，输入 “regedit” 打开注册表。这次定位到：“计算机\HKEY_CURRENT_USER\SOFTWARE\Microsoft\OneDrive”。

找到 DisablePersonalSync 属性，将改值修改为“1”：

![Set_DisablePersonalSync_1.png](http://windows-media.knowledge.ituknown.cn/onedrive/disable_sidebar_tray/method2/Set_DisablePersonalSync_1.png)

如果你没找到改属性，就右键点击 OneDrive，选择新建 “DWORD（32位）值”：

![NewDWORD32.png](http://windows-media.knowledge.ituknown.cn/onedrive/disable_sidebar_tray/method2/NewDWORD32.png)

之后重命名为 DisablePersonalSync，再执行值即可！

关机重启之后就会看到右侧菜单栏中的 “OneDrive - Personal” 消失了~