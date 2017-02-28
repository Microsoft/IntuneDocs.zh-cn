---
title: "适用于 Windows 10 的 Intune 设备限制设置 |Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可用来控制 Windows 10 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 208312eea9df0b6330e6eac9334bd63bb13624c5
ms.lasthandoff: 02/16/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 10 及更高版本设备限制设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>常规
-     **屏幕捕获** - 让用户以图像形式捕获设备屏幕。 （仅限 Windows 10 移动版）
-     **复制和粘贴（仅限移动设备）** - 允许设备上应用间的复制和粘贴操作。
-     **手动注销** - 允许用户手动从设备中删除工作区帐户。
-     **手动安装根证书** -     
-     **诊断数据提交** - 可能的值有：
    -         **无** - 不将数据发送给 Microsoft
    -         **基本** - 将有限的信息发送给 Microsoft
    -         **增强** - 将增强的诊断数据发送给 Microsoft
    -         **完全** - 发送与“增强”相同的数据，外加有关设备状态的其他数据
-     **相机** - 允许或阻止使用设备上的相机。
-     **可移动存储** - 指定外部存储设备（如 SD 卡）是否可以与该设备结合使用。
-     **地理位置** - 指定设备是否可以使用位置服务信息。
-     **Internet 共享** - 允许在设备上使用 Internet 连接共享。
-     **手机重置** - 控制用户是否可以在设备上恢复出厂设置。
-     **USB 连接** - 控制设备是否可以通过 USB 连接访问外部存储设备。
-     **防盗模式** - 配置是否启用 Windows 防盗模式。
-     **操作中心通知** - 启用或禁用设备锁定屏幕上的操作中心通知（仅限 Windows 10 移动版）。
-     **Cortana** - 启用或禁用 Cortana 语音助手。
-     **语音录制** - 允许或阻止使用设备的语音录音机。

## <a name="password"></a>Password
-     **需要密码** - 需要最终用户输入密码才能访问设备。
-     **所需的密码类型** - 指定密码是否只能是数字或字母数字。
-     **最短密码长度** - 仅适用于 Windows 10 移动版。
-     **擦除设备前的登录失败次数** - 对于运行 Windows 10 的设备：如果该设备已启用 BitLocker，在超过指定的登录失败次数后将进入 BitLocker 恢复模式。 如果该设备未启用 BitLocker，则不会应用此设置。
对于运行 Windows 10 移动版的设备：超过指定的登录失败次数后，将擦除设备。
-     **屏幕锁定前的最大非活动状态分钟数** - 指定锁定屏幕前，设备必须处于空闲状态的时间长度。
-     **密码过期（天数）** - 指定必须更改设备密码之前的时间长度。
-     **防止重用以前的密码** - 指定设备记住的以前用过的密码数目。
-     **设备从空闲状态返回时需要输入密码** - 指定用户必须输入密码以解锁设备（仅限 Windows 10 移动版）。
-     **加密** - 启用对目标设备的加密（仅限 Windows 10 移动版）。
## <a name="app-store"></a>App Store

-     **应用商店（仅限移动版）** - 在 Windows 10 移动设备上启用或阻止使用应用商店。
## <a name="edge-browser"></a>Microsoft Edge 浏览器
-     **Microsoft Edge 浏览器（仅限移动版）** - 允许在设备上使用 Microsoft Edge Web 浏览器。
-     **SmartScreen** - 启用或禁用阻止欺诈网站的 SmartScreen。
-     **发送 do-not-track 标头** - 配置 Microsoft Edge 浏览器，将“不跟踪”标头发送到用户访问的网站。
-     **Cookie** - 允许浏览器将 Internet Cookie 保存到设备。
-     **JavaScript** - 允许脚本（如 Javascript）在 Microsoft Edge 浏览器中运行。
-     **弹出窗口** - 在浏览器中阻止弹出窗口。<br>（仅适用于 Windows 10 桌面版）。
-     **搜索建议** - 允许搜索引擎在你键入搜索短语时建议站点。
-     **将 Intranet 流量发送到 Internet Explorer** - 允许用户在 Internet Explorer 中打开 Intranet 网站。 <br>（仅限 Windows 10 桌面版）。
-     **自动填充** - 允许用户更改浏览器中的自动完成设置。<br>（仅限 Windows 10 桌面版）
-     **密码管理器** - 启用或禁用 Microsoft Edge 密码管理器功能。
-     **企业模式站点列表位置** - 指定在哪个位置可找到以企业模式打开的网站的列表。 用户无法编辑此列表。<br>（仅限 Windows 10 桌面版）。
## <a name="cloud-and-storage"></a>云和存储
-     **Microsoft 帐户** - 使用户可以将 Microsoft 帐户与设备关联。
-     **非 Microsoft 帐户** - 使用户可以将电子邮件帐户添加到不与 Microsoft 帐户相关联的设备。
-     **Microsoft 帐户的设置同步** - 允许设备和应用设置与 Microsoft 帐户关联以在设备之间进行同步。
## <a name="cellular-and-connectivity"></a>手机网络和连接性
-     **数据漫游** - 允许在访问数据时进行网络之间的漫游。
-     **通过手机网络使用 VPN** - 控制设备在连接到手机网络时是否能够访问 VPN 连接。
-     **通过手机网络漫游 VPN** - 控制设备在手机网络上漫游时是否能够访问 VPN 连接。
-     **蓝牙** - 控制用户是否可以在设备上启用和配置蓝牙。
-     **蓝牙可发现性** - 允许其他已启用蓝牙的设备可发现此设备。
-     **蓝牙广告** - 允许设备通过蓝牙接收广告。
-     **NFC** - 允许用户在设备上启用和配置近场通信功能。
-     **Wi-Fi** - 允许用户在设备上启用和配置 Wi-Fi（仅限 Windows 10 移动版）。
-     **自动连接到 Wi-Fi 热点** - 可让设备自动连接到免费 Wi-Fi 热点并自动接受该连接的任何条款和条件。
-     **手动配置 Wi-Fi** - 控制用户是否可以配置自己的 Wi-Fi 连接或是否只能使用 Wi-Fi 配置文件配置的连接（仅限 Windows 10 移动版）。
## <a name="defender"></a>Defender

-     **实时监控** - 启用对恶意软件、间谍软件和其他不需要的软件的实时扫描。
-     **行为监控** - 允许 Defender 检查设备上是否存在某些已知模式的可疑活动。
-     **网络检查系统 (NIS)** - 网络检查系统 (NIS) 通过使用 Microsoft Endpoint Protection 中心的已知漏洞的签名帮助检测和阻止恶意流量，从而保护设备免受基于网络的攻击。
-     **扫描所有下载** - 控制 Defender 是否扫描从 Internet 下载的所有文件。
-     **扫描 Microsoft Web 浏览器中加载的脚本** - 允许 Defender 扫描在 Internet Explorer 中使用的脚本。
-     **Defender 的最终用户访问权限** - 控制是否对最终用户隐藏 Windows Defender 用户界面。
此设置更改后，将在最终用户的 PC 下次重启时生效。
-     **签名更新间隔（小时）** - 指定 Defender 检查新签名文件的时间间隔。
-     **监视文件和程序活动** - 允许 Defender 监视设备上的文件和程序活动。
-     **删除已隔离恶意软件之前的天数** - 允许 Defender 按指定的天数继续跟踪已解决的恶意软件，以便可以手动检查之前受影响的设备。 如果你将天数设置为 **0**，则恶意软件将保留在隔离文件夹中，并且不会自动删除。
-     **在扫描期间限制 CPU 使用率** - 可让你限制允许扫描使用的 CPU 量（从 **1** 到 **100**）。
-     **扫描存档文件** - 允许 Defender 扫描存档的文件（如 Zip 或 Cab 文件）。
-     **扫描传入的电子邮件** - 允许 Defender 在电子邮件到达设备时扫描它们。
-     **完全扫描期间扫描可移动驱动器** - 允许 Defender 扫描可移动驱动器（如 U 盘）。
-     **完全扫描期间扫描映射的网络驱动器** - 允许 Defender 扫描映射网络驱动器上的文件。<br>如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。
-     **扫描从网络文件夹打开的文件** - 允许 Defender 扫描共享网络驱动器上的文件（例如，从 UNC 路径访问的那些文件）。
如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。
-     **Cloud 保护** - 允许或阻止 Microsoft Active Protection Service 接收来自你管理的设备的恶意软件活动的相关信息。 此信息用于在将来改进本服务。
-     **在示例提交前提示用户** - 控制是否自动向 Microsoft 发送可能需要 Microsoft 的进一步分析以确定其是否为恶意的文件。
-     **执行日常快速扫描的时间** - 允许计划每日在你选择的时间里发生的快速扫描。
-     **要执行的系统扫描类型** - 允许计划系统扫描时指定要执行的扫描级别。
## <a name="defender-exclusions"></a>Defender 排除项

-     **要从扫描和实时保护排除的文件和文件夹** - 向排除列表添加一个或多个文件和文件夹（如 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe**）。 不会在任何实时或计划的扫描中包括这些文件和文件夹。
-     **要从扫描和实时保护排除的文件扩展名** - 向排除列表添加一个或多个文件扩展名（如 **jpg** 或 **txt**）。 不会在任何实时或计划的扫描中包括具有这些扩展名的任何文件。
-     **要从扫描和实时保护排除的进程** - 向排除列表添加一个或多个类型为 **.exe**、**.com** 或 **.scr** 的进程。 不会在任何实时或计划的扫描中包括这些进程。

