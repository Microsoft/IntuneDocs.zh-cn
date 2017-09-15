---
title: "Windows 10 策略设置"
description: "使用本主题中列出的策略设置可帮助你为已注册的 Windows 10 桌面版和 Windows 10 移动版设备配置内置和自定义设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f19b7e9d57350f90baca96562a99b2fde66f91a
ms.sourcegitcommit: 00352501833818a08479758ba1c9efdf7223e264
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2017
---
# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题包含的信息可帮助你了解可用于管理 Windows 10 设备的 Intune 策略设置。 有关本主题及过程，请参阅[使用 Microsoft Intune 策略管理设备上的设置和功能](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune)。

可以从两种策略类型中进行选择：

- **自定义策略**：使用适用于 Windows 10 和 Windows 10 移动版的 Microsoft Intune **自定义策略**来部署可用于控制设备上功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 Windows 10 提供了许多 CSP 设置，例如“[策略配置服务提供程序(策略 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)”。
- **常规配置策略**：如果想要从 Microsoft Intune 提供的内置列表中选择设置，则使用此策略类型。

## <a name="custom-policy-settings"></a>自定义策略设置

在自定义策略中提供以下设置。

### <a name="general-settings"></a>常规设置

输入名称和有助于在 Intune 控制台中识别该策略的描述（后者为可选）。

### <a name="oma-uri-settings"></a>OMA-URI 设置

对于要添加的每个 OMA URI 设置，请输入以下信息：

- **设置名称**：输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。 有关 URI 设置的详细信息，可以参阅[策略配置服务提供程序（策略 CSP）](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
- **设置描述** -（可选）输入设置的描述。
- **数据类型**：从以下数据类型中进行选择：
    - **字符串**
    - **字符串 (XML)**
    - **日期和时间**
    - **整数**
    - **浮点**
    - **布尔值**
- **OMA-URI（区分大小写）**：指定想要为其提供设置的 OMA-URI。
- **值**：指定要与输入的 OMA-URI 关联的值。

### <a name="example"></a>示例
在以下屏幕截图中，已启用设置 **Connectivity/AllowVPNOverCellular**。 这样一来，Windows 10 设备在处于移动电话网络中时会打开 VPN 连接。

> ![包含 VPN 设置的自定义策略的示例](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>如何查找可以配置的策略

可以在 Windows 文档库中的[配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中找到 Windows 10 支持的所有配置服务提供程序 (CSP) 的完整列表。

并非所有设置均兼容所有 Windows 10 版本。 Windows 主题中的表将告诉你各个 CSP 支持的版本。

此外，Intune 并不支持本主题中列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开适用于该设置的主题。 每个设置页面将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”或“替换”操作。

## <a name="general-configuration-policy-settings"></a>常规配置策略设置

使用适用于 Windows 10 的 Microsoft Intune **常规配置策略**为已注册的 Windows 10 桌面版和 Windows 10 移动版设备配置内置设置。

### <a name="password"></a>Password

|设置名|其他信息（如有需要）|
|----------------|----------------------|
|**需要密码才能解锁设备**|-|
|**所需的密码类型**|指定密码是否只能是字母数字或数字|
|**所需的密码类型** - **最小字符集数**| 指定密码中必需包含的字符集（小写字母、大写字母、数字和符号）数|
|**最短密码长度**|仅适用于 Windows 10 移动版|
|**擦除设备前允许的重复登录失败次数**。|对于运行 Windows 10 的设备：如果该设备已启用 BitLocker，在超过指定的登录失败次数后将进入 BitLocker 恢复模式。 如果该设备未启用 BitLocker，则不会应用此设置。<br>对于运行 Windows 10 移动版的设备：超过指定的登录失败次数后，将擦除设备。|
|**屏幕关闭前处于不活动状态的分钟数**|指定锁定屏幕之前，设备必须处于空闲状态的时间长度|
|**密码过期（天数）**|指定必须更改设备密码之前的时间长度|
|**记住密码历史记录**|指定是否限制用户创建以前用过的密码|
|**“记住密码历史记录”** - **“防止重用以前的密码”**|指定设备记住的以前用过的密码数目|
|**当设备从空闲状态返回时需要密码**|指定用户必须输入密码以解锁设备（仅限 Windows 10 移动版）|

### <a name="encryption"></a>加密

|设置名|其他信息（如有需要）|
|----------------|----------------------|
|**需要对移动设备加密**|启用对目标设备的加密<br>（仅限 Windows 10 移动版）|

### <a name="system"></a>System (系统)

|设置名|其他信息（如有需要）|
|----------------|----------------------|
|**允许屏幕捕获**|让用户以图像形式捕获设备屏幕（仅限 Windows 10 移动版）|
|**允许手动取消注册**|允许用户手动从设备中删除工作区帐户|
|**允许手动安装根证书**|适用于 Windows 10 移动版|
|**允许将诊断和使用数据发送给 Microsoft**|可能的值有：<br><br>**否** - 不将数据发送给 Microsoft<br>**基本** - 将有限的信息发送给 Microsoft<br>**增强** - 将增强的诊断数据发送给 Microsoft<br>**完全（建议）** - 发送与**增强**相同的数据，外加有关设备状态的其他数据|


### <a name="account-and-synchronization"></a>帐户和同步

|设置名|其他信息（如有需要）|
|----------------|----------------------|---------------------|
|**支持 Microsoft 帐户**|使用户可以将 Microsoft 帐户与设备关联|
|**允许手动添加非 Microsoft 帐户**|使用户可以将电子邮件帐户添加到不与 Microsoft 帐户相关联的设备|
|**允许 Microsoft 帐户进行设置同步**|允许设备和应用设置与 Microsoft 帐户关联以在设备之间进行同步|

### <a name="microsoft-edge"></a>Microsoft Edge

|设置名|其他信息（如有需要）|
|----------------|----------------------|
|**允许 Web 浏览器**|允许在设备上使用 Microsoft Edge Web 浏览器<br>（仅限 Windows 10 移动版）|
|**允许在地址栏中显示搜索建议**|允许搜索引擎在你键入搜索短语时建议站点|
|**允许将 Intranet 流量发送到 Internet Explorer**|允许用户在 Internet Explorer 中打开 Intranet 网站<br>（仅限 Windows 10 桌面版）|
|**允许使用 Do Not Track**|配置 Microsoft Edge 浏览器以将“不跟踪”标题发送到用户访问的网站|
|**启用 SmartScreen**||
|**允许使用活动脚本**|允许脚本（如 Javascript）在 Microsoft Edge 浏览器中运行|
|**允许弹出窗口**|仅适用于 Windows 10 桌面版|
|**允许使用 Cookie**||
|**允许自动填充**|允许用户更改浏览器中的自动完成设置<br>（仅限 Windows 10 桌面版）|
|**允许使用密码管理器**|启用或禁用 Microsoft Edge 密码管理器功能|
|**企业模式网站列表位置**|指定在哪个位置可找到以企业模式打开的网站的列表。 用户无法编辑此列表。<br>（仅限 Windows 10 桌面版）|

### <a name="apps"></a>应用

|设置名|其他信息（如有需要）|
|----------------|----------------------|---------------------|
|**允许应用程序商店**|仅适用于 Windows 10 移动版|



### <a name="cellular"></a>移动电话

|设置名|其他信息（如有需要）|
|----------------|----------------------|---------------------|
|**允许数据漫游**|允许在访问数据时进行网络之间的漫游|
|**允许通过移动电话网络使用 VPN**|控制设备在连接到移动电话网络时是否能够访问 VPN 连接|
|**允许在通过移动电话网络漫游时使用 VPN**|控制设备在移动电话网络上漫游时是否能够访问 VPN 连接|

### <a name="hardware"></a>硬件

|设置名|其他信息（如有需要）|
|----------------|----------------------|
|**允许照相机**|-|
|**允许可移动存储**|指定外部存储设备（如 SD 卡）是否可以与该设备结合使用|
|**允许 Wi-Fi**|仅适用于 Windows 10 移动版|
|**允许 Internet 共享**|允许在设备上使用 Internet 连接共享|
|**允许手动配置 Wi-Fi**|控制用户是否可以配置自己的 Wi-Fi 连接或是否只能使用 Wi-Fi 配置文件配置的连接<br>（仅限 Windows 10 移动版）|
|**允许自动连接到免费 Wi-Fi 热点**|可让设备自动连接到免费 Wi-Fi 热点并自动接受该连接的任何条款和条件|
|**允许地理位置**|指定设备是否可以使用位置服务信息|
|**允许 NFC**|允许设备使用其近场通信功能|
|**允许蓝牙**|-|
|**允许使用蓝牙可发现模式**|让其他已启用蓝牙的设备可发现此设备|
|**允许使用蓝牙广告**|允许设备通过蓝牙接收广告|
|**允许重置手机**|控制用户是否可以在设备上恢复出厂设置|
|**允许使用 USB 连接**|控制设备是否可以通过 USB 连接访问外部存储设备|
|**允许使用防盗模式**|配置是否启用 Windows 防盗模式|

### <a name="features"></a>功能

|设置名|其他信息（如有需要）|
|----------------|----------------------|---------------------|
|**允许复制和粘贴**|仅适用于 Windows 10 移动版|
|**允许语音录制**|仅适用于 Windows 10 移动版|
|**允许使用 Cortana**|启用或禁用 Cortana 语音助手|
|**允许操作中心通知**|启用或禁用设备锁定屏幕上的操作中心通知<br>（仅限 Windows 10 移动版）|

### <a name="windows-defender"></a>Windows Defender

所有设置都仅适用于 Windows 10 桌面版。

|设置名|其他信息（如有需要）|
|----------------|----------------------|---------------------|
|**允许实时监视**|启用对恶意软件、间谍软件和其他不需要的软件的实时扫描|
|**允许行为监视**|允许 Defender 检查设备上是否存在某些已知模式的可疑活动|
|**启用网络检查系统**|网络检查系统 (NIS) 通过使用 Microsoft Endpoint Protection 中心的已知漏洞的签名帮助检测和阻止恶意流量，从而保护设备免受基于网络的攻击|
|**扫描所有下载**|控制 Defender 是否扫描从 Internet 下载的所有文件|
|**允许脚本扫描**|允许 Defender 扫描在 Internet Explorer 中使用的脚本|
|**监视文件和程序活动**|允许 Defender 监视设备上的文件和程序活动|
|**跟踪已解决的恶意软件的天数**|允许 Defender 持续跟踪已解决的恶意软件，跟踪时间为你指定的天数，以便你可以手动检查之前受影响的设备。 如果你将天数设置为 **0**，则恶意软件将保留在隔离文件夹中，并且不会自动删除。 |
|**允许客户端 UI 访问**|控制是否对用户隐藏 Windows Defender 用户界面。<br>此设置更改后，在用户的电脑下次重启时生效。|
|**计划每日一次快速扫描**|允许计划每日在你选择的时间里发生的快速扫描|
|**计划系统扫描**|允许计划定期在选定日期和时间发生的完整或快速系统扫描|
|**在扫描期间限制 CPU 使用率**|可让你限制允许扫描使用的 CPU 量（从 **1** 到 **100**）|
|**扫描存档文件**|允许 Defender 扫描存档的文件（如 .zip 或 .cab 文件）。|
|**扫描电子邮件**|允许 Defender 在电子邮件到达设备时扫描它们|
|**扫描可移动驱动器**|允许 Defender 扫描可移动驱动器（如 U 盘）|
|**扫描映射的网络驱动器**|允许 Defender 扫描映射网络驱动器上的文件。<br>如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。|
|**扫描从网络共享文件夹中打开的文件**|允许 Defender 扫描共享网络驱动器上的文件（例如，从 UNC 路径访问的那些文件）。<br>如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。|
|**签名更新间隔**|指定 Defender 检查新签名文件的时间间隔。|
|**允许使用云保护**|允许或阻止 Microsoft Active Protection Service 接收来自你管理的设备的恶意软件活动的相关信息。 此信息用于在将来改进本服务。|
|**提示用户提交示例**|控制是否自动向 Microsoft 发送可能需要 Microsoft 的进一步分析以确定其是否为恶意的文件|
|**可能不需要的应用程序检测**|防止已注册的 Windows 桌面版设备运行被 Windows Defender 分类为可能不需要的软件。 你可以防止这些应用程序运行，或使用审核模式在安装了不需要的应用程序时进行报告。|
|**在运行扫描或使用实时保护时要排除的文件和文件夹**|向排除列表添加一个或多个文件和文件夹（如 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe**）。 不会在任何实时或计划的扫描中包括这些文件和文件夹。|
|**在运行扫描或使用实时保护时要排除的文件扩展名**|向排除列表添加一个或多个文件扩展名（如 **jpg** 或 **txt**）。 不会在任何实时或计划的扫描中包括具有这些扩展名的任何文件。|
|**在运行扫描或使用实时保护时要排除的进程**|向排除列表添加类型为 **.exe**、**.com** 或 **.scr** 的一个或多个进程。 不会在任何实时或计划的扫描中包括这些进程。|


### <a name="updates"></a>Updates

|设置名|其他信息（如有需要）|
|----------------|---------------|
|**允许自动更新**|允许自动更新。 配置以下设置之一以控制更新行为：<br />**通知下载**<br />**在维护时间自动安装**<br />**在维护时间自动安装并重启**<br />**在计划时间自动安装和重新启动**：请注意，选择此选项时，还可以配置以下设置：**禁止向最终用户发送通知**和**定义计划更新的安装日期**。<br>（仅限 Windows 10 桌面版）|
|**允许预发布功能**|允许 Microsoft 将预发行设置和功能部署到 Windows 10 设备。 你可以选择仅允许安装设置，或允许安装所有预发行设置和功能。|

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
