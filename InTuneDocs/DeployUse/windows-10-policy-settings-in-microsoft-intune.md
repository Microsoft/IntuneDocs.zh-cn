---
# required metadata

title: Windows 10 策略设置 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 Windows 10 策略设置

使用本主题中列出的策略设置帮助为已注册的 Windows 10 桌面版和 Windows 10 移动版设备配置设置。

## 常规配置策略设置

使用适用于 Windows 10 的 Microsoft Intune **常规配置策略**为已注册的 Windows 10 桌面版和 Windows 10 移动版设备配置常规设置：


### Password

|设置名|详细信息|
|----------------|----------------------|
|**需要密码才能解锁设备**|支持的设备上需要密码。|
|**所需的密码类型**|指定需要的密码类型，例如仅限数字或字母数字|
|**所需的密码类型** - **最小字符集数**|有以下四个字符集: 小写字母、大写字母、数字和符号。 此设置指定密码中必须包括多少个不同的字符集。|
|**最短密码长度**|指定设备密码必须包含的最少字符数。<br>（仅限 Windows 10 移动版）|
|**擦除设备前允许的重复登录失败次数**|如果此数目的登录尝试均失败，则擦除该设备。|
|**屏幕关闭前处于不活动状态的分钟数**|指定锁定屏幕之前，设备必须处于空闲状态的时间长度。|
|**密码过期(天)**|指定必须更改设备密码之前的时间长度。|
|**记住密码历史记录**|指定是否想要限制最终用户创建以前用过的密码。|
|**“记住密码历史记录”** - **“防止重用以前的密码”**|指定设备记住的以前用过的密码数目。|
|**允许图片密码和 PIN**|允许你使用图片上的简单手势或简单的 PIN 登录。<br>（仅限 Windows 10 桌面版）|
|**当设备从空闲状态返回时需要密码**|如果启用，则用户必须输入密码以将设备从空闲状态解锁。<br>（仅限 Windows 10 移动版）|

### 加密

|设置名|详细信息|
|----------------|----------------------|
|**需要对移动设备加密**|启用对目标设备的加密。<br>（仅限 Windows 10 移动版）|

### System (系统)

|设置名|详细信息|
|----------------|----------------------|
|**允许屏幕捕获**|让用户以图像形式捕获设备屏幕。<br>（仅限 Windows 10 移动版）|
|**允许手动取消注册**|允许用户手动从设备中删除工作区帐户。|
|**允许手动安装根证书**|指定用户是否可以手动安装根证书。<br>（仅限 Windows 10 移动版）|
|**允许将诊断和使用数据发送给 Microsoft**|确定从设备发送给 Microsoft 的诊断和使用情况数据的量。<br><br>**否** - 不将数据发送给 Microsoft<br>**基本** - 设备仅将有限的信息发送给 Microsoft<br>**增强** - 将增强的诊断数据发送给 Microsoft<br>**完全（建议）** - 发送与**增强**相同的数据，外加有关设备状态的其他数据|


### 帐户和同步

|设置名|详细信息|
|----------------|----------------------|---------------------|
|**支持 Microsoft 帐户**|使用户可以将 Microsoft 帐户与设备关联。|
|**允许手动添加非 Microsoft 帐户**|使用户可以将电子邮件帐户添加到不与 Microsoft 帐户相关联的设备。|
|**允许 Microsoft 帐户进行设置同步**|允许设备和应用设置与 Microsoft 帐户关联以在设备之间进行同步。|

### 电子邮件设置

|设置名|详细信息|
|----------------|----------------------|---------------------|
|**在 Windows Mail 应用程序中将 Microsoft 帐户设为可选**|进行这样的配置以免去在 Windows Mail 中需要使用 Microsoft 帐户这一要求。<br>仅限 Windows 10 桌面版|



### Microsoft Edge

|设置名|详细信息|
|----------------|----------------------|
|**允许 Web 浏览器**|允许在设备上使用 Edge Web 浏览器。<br>（仅限 Windows 10 移动版）|
|**允许在地址栏中显示搜索建议**|使搜索引擎在你键入搜索短语时可建议站点。|
|**允许将 Intranet 流量发送到 Internet Explorer**|允许用户在 Internet Explorer 中打开 intranet 网站。<br>（仅限 Windows 10 桌面版）|
|**允许使用 Do Not Track**|配置 Edge 浏览器以将“不跟踪”标题发送到用户访问的网站。|
|**启用 SmartScreen**|启用设备上的 SmartScreen 浏览器设置。|
|**允许使用活动脚本**|允许在 Edge 浏览器中运行 JavaScript 等脚本。|
|**允许弹出窗口**|启用或禁用浏览器弹出窗口阻止程序。<br>（仅限 Windows 10 桌面版）|
|**允许使用 Cookie**|允许或禁用 cookie。|
|**允许自动填充**|允许用户更改浏览器中的自动完成设置。<br>（仅限 Windows 10 桌面版）|
|**允许使用密码管理器**|启用或禁用 Edge 密码管理器功能。|
|**企业模式网站列表位置**|指定在哪里可以找到你想使用企业模式打开的网站的列表。 用户无法编辑此列表。<br>（仅限 Windows 10 桌面版）|

### 应用

|设置名|详细信息|
|----------------|----------------------|---------------------|
|**允许应用程序商店**|允许用户访问设备上的应用商店。<br>（仅限 Windows 10 移动版）|



### 移动电话

|设置名|详细信息|
|----------------|----------------------|---------------------|
|**允许数据漫游**|允许在访问数据时进行网络之间的漫游。|
|**允许通过移动电话网络使用 VPN**|控制设备在连接到移动电话网络时是否能够访问 VPN 连接。|
|**允许在通过移动电话网络漫游时使用 VPN**|控制设备在移动电话网络上漫游时是否能够访问 VPN 连接。|

### 硬件

|设置名|详细信息|
|----------------|----------------------|
|**允许照相机**|指定是否可以使用设备照相机。|
|**允许可移动存储**|指定外部存储设备（如 SD 卡）是否可以与该设备结合使用。|
|**允许 Wi-Fi**|允许使用设备的 Wi-Fi 功能。<br>（仅限 Windows 10 移动版）|
|**允许 Internet 共享**|允许在设备上使用 Internet 连接共享。|
|**允许手动配置 Wi-Fi**|控制用户是否可以配置自己的 Wi-Fi 连接或是否只能使用 Wi-Fi 配置文件配置的连接。<br>（仅限 Windows 10 移动版）|
|**允许自动连接到免费 Wi-Fi 热点**|可让设备自动连接到免费 Wi-Fi 热点并自动接受该连接的任何条款和条件。|
|**允许地理位置**|指定设备是否可以使用位置服务信息。|
|**允许 NFC**|允许设备使用其近场通信功能。|
|**允许蓝牙**|允许使用设备上的蓝牙功能。|
|**允许使用蓝牙可发现模式**|让其他已启用蓝牙的设备可发现此设备。|
|**允许使用蓝牙广告**|允许设备通过蓝牙接收广告。|
|**允许使用蓝牙可连接模式**|**重要提示：**Windows 10 不再支持此设置，并且将在以后删除此设置。|
|**允许重置手机**|控制用户是否可以出厂重置其设备。|
|**允许使用 USB 连接**|控制设备是否可以通过 USB 连接访问外部存储设备。|
|**允许使用防盗模式**|配置是否启用 Windows 防盗模式。|

### 功能

|设置名|详细信息|
|----------------|----------------------|---------------------|
|**允许复制和粘贴**|启用或禁用设备上的复制和粘贴功能。<br>（仅限 Windows 10 移动版）|
|**允许语音录制**|启用或禁用设备上的语音录制功能。<br>（仅限 Windows 10 移动版）|
|**允许使用 Cortana**|启用或禁用 Cortana 语音助手。|
|**允许操作中心通知**|启用或禁用设备锁定屏幕上的操作中心通知。<br>（仅限 Windows 10 移动版）|

### Defender

所有设置都仅适用于 Windows 10 桌面版。

|设置名|详细信息|
|-|-|
|**允许实时监视**|启用对恶意软件、间谍软件和其他不需要的软件的实时扫描。|
|**允许行为监视**|允许 Defender 检查设备上是否存在某些已知模式的可疑活动。|
|**启用网络检查系统**|网络检查系统 (NIS) 通过使用 Microsoft Endpoint Protection 中心的已知漏洞的签名帮助检测和阻止恶意流量，从而保护设备免受基于网络的攻击。|
|**扫描所有下载**|控制 Defender 是否扫描从 Internet 下载的所有文件。|
|**允许脚本扫描**|允许 Defender 扫描在 Internet Explorer 中使用的脚本。|
|**监视文件和程序活动**|启用此设置以允许 Defender 监视设备上的文件和程序活动。|
|**跟踪已解决的恶意软件的天数**|允许 Defender 持续跟踪已解决的恶意软件，跟踪时间为你指定的天数，以便你可以手动检查之前受影响的设备。 如果你将天数设置为 **0**，则恶意软件将保留在隔离文件夹中，并且不会自动删除。 |
|**允许客户端 UI 访问**|控制是否对最终用户隐藏 Windows Defender 用户界面。<br>此设置更改后，将在最终用户的 PC 下次重启时生效。|
|**计划每日一次快速扫描**|使你可以计划每日在你选择的时间里发生的快速扫描。|
|**计划系统扫描**|可让你计划定期在选定日期和时间发生的完整或快速系统扫描。|
|**在扫描期间限制 CPU 使用率**|可让你限制允许扫描使用的 CPU 量（从 **1** 到 **100**）|
|**扫描存档文件**|允许 Defender 扫描存档的文件（如 Zip 或 Cab 文件）。|
|**扫描电子邮件**|允许 Defender 在电子邮件到达设备时扫描它们。|
|**扫描可移动驱动器**|允许 Defender 扫描可移动驱动器（如 USB 记忆棒）。|
|**扫描映射的网络驱动器**|允许 Defender 扫描映射网络驱动器上的文件。<br>如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。|
|**扫描从网络共享文件夹中打开的文件**|允许 Defender 扫描共享网络驱动器上的文件（例如，从 UNC 路径访问的那些文件。<br>如果驱动器上的文件是只读的，则 Defender 将无法删除在它们中找到的任何恶意软件。|
|**签名更新间隔**|指定 Defender 检查新签名文件的时间间隔。|
|**允许使用云保护**|允许或阻止 Microsoft Active Protection Service 接收来自你管理的设备的恶意软件活动的相关信息。 此信息用于在将来改进本服务。|
|**提示用户提交示例**|控制是否自动向 Microsoft 发送可能需要 Microsoft 的进一步分析以确定其是否为恶意的文件。|
|**在运行扫描或使用实时保护时要排除的文件和文件夹**|向排除列表添加一个或多个文件和文件夹（如 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe**）。 不会在任何实时或计划的扫描中包括这些文件和文件夹。|
|**在运行扫描或使用实时保护时要排除的文件扩展名**|向排除列表添加一个或多个文件扩展名（如 **jpg** 或 **txt**）。 不会在任何实时或计划的扫描中包括具有这些扩展名的任何文件。|
|**在运行扫描或使用实时保护时要排除的进程**|向排除列表添加类型为 **.exe**、**.com** 或 **.scr** 的一个或多个进程。 不会在任何实时或计划的扫描中包括这些进程。| 


### 更新设置

|设置名|详细信息|
|----------------|---------------|
|**允许自动更新**|启用此设置以允许自动更新。 然后，配置以下设置之一以控制更新行为：<br /><br />**通知下载**<br /><br />**在维护时间自动安装**<br /><br />**在维护时间自动安装并重启**<br /><br />**在计划时间自动安装和重新启动****注意：**选择此选项时，还可以配置以下设置：**禁止向最终用户发送通知**和**定义计划更新的安装日期**。<br>（仅限 Windows 10 桌面版）|

## 自定义策略设置
使用 Windows 10 和 Windows 10 移动版的 Microsoft Intune **自定义配置策略**来部署可用于控制 Windows 10 和 Windows 10 移动版设备上的功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在使你能够部署不能与 Intune 常规配置策略一起配置的 Windows 10 设置。



### 自定义策略常规设置

|设置名|详细信息|
    |----------------|--------------------|
    |**Name**|输入策略的唯一名称，以帮助你在 Intune 控制台中识别它。|
    |**说明**|提供对策略的说明以及可帮助你查找策略的其他相关信息。|

### 自定义策略 OMA-URI 设置

|设置名|详细信息|
    |--------|--------------------|
    |**设置名**|输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。|
    |**设置描述**|提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。|
    |**数据类型**|选择将在其中指定此 OMA-URI 设置的日期类型。 选择：<br /><br />-   **字符串**<br />-   **字符串 (XML)**<br />-   **日期和时间**<br />-   **整数**<br />-   **浮点**<br />-   **布尔值**|
    |**OMA-URI（区分大小写）**|指定需为其提供设置的 OMA-URI。|
    |**值**|指定要与之前指定的 OMA-URI 关联的值。|


## Windows 10 设备的自定义 URI 设置
本主题列出了可以在 Microsoft Intune **Windows 10 自定义策略**中为 Windows 10 和 Windows 10 移动设备配置的设置。

如果想要使用 Windows 自定义 URI 策略，则必须向 Intune 注册所有设备。

### 策略 URI 设置

|策略名称|详细信息|
|---------------|------------|-----------|
|**​运行自动更新**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - **5**（默认值：**1**）|
|**计划安装日期**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 每天（默认值）<br>**1** - 星期日<br>**2** - 星期一<br>**3** - 星期二<br>**4** - 星期三<br>**5** - 星期四<br>**6** - 星期五<br>**7** - 星期六|
|**计划安装日期**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – **23** 小时（**0** 表示午夜）（默认值：**3**）|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 用户不能设置密码的宽限期计时器，且值设置为“每次”<br>**1** - 用户可以设置密码的宽限期计时器（默认值）|
|**WiFi/AllowWiFi**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 不允许**使用 Wi-Fi 连接**。<br>**1** – **允许使用 Wi-Fi 连接**（默认值）|
|**WiFi/AllowInternetSharing**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许 Internet 共享。<br>**1** - 允许 Internet 共享（默认值）|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**WiFi/AllowManualWiFiConfiguration**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** –只允许 MDM 预配的 Wi-Fi 连接。<br>**1** - 除 MDM 已预配的网络外，允许添加新网络 SSID（默认值）|
|**System/AllowLocation**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**System/AllowTelemetry**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许（Enterprise 版仅设置）<br>**“1”** - 有限<br>**2** – 完全（默认值）<br>**3** -  完全和诊断信息|
|**System/AllowExperimentation**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** - 仅设置（默认值）<br>**2**- 设置和实验|
|**Security/AntiTheftMode**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 不允许防盗模式<br>**1** - 用户首选项（默认值）|
|**Connectivity/AllowUSBConnection**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**System/AllowUserToResetPhone**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Connectivity/AllowCellularDataRoaming**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Connectivity/AllowVPNOverCellular**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 不允许 VPN 使用手机网络<br>**1** - VPN 可以使用任何连接，包括手机网络（默认值）|
|**Connectivity/AllowVPNRoamingOverCellular**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Connectivity/AllowVPNRoamingOverCellular**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Connectivity/AllowBluetooth**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 不允许用户打开蓝牙。<br>**1** – 保留。 用户可以启用和配置蓝牙（在适用于 MDM、EAS 的 Windows Phone 8.1、Windows 10 桌面版或 Windows 10 移动版中不受支持）<br>**2** - 允许。 用户可以启用和配置蓝牙（默认值）|
|**Experience/AllowScreenCapture**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Experience/AllowTaskSwitcher**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Experience/AllowVoiceRecording**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Experience/AllowSyncMySettings**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许漫游<br>**1** - 允许漫游（默认值）|
|**Experience/AllowManualMDMUnenrollment**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Accounts/AllowMicrosoftAccountConnection**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Security/AllowManualRootCertificateInstallation**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Security/AllowAddProvisioningPackages**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Search/DisableBackoff**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**（默认值）<br>**1**|
|**Search/PreventRemoteQueries**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**<br>**1**（默认值）|
|**Search/AllowUsingDiacritics**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br> **0**（默认值）<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**（默认值）<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**（默认值）<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**<br>**1**（默认值）|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**（默认值）<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Security/RequireProvisioningPackageSignature**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**（默认值）<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**TextInput/AllowIMENetworkAccess**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>“打开扩展词典”已禁用。<br>用户不可：<br>添加新的“打开扩展词典”<br /><br />添加新的搜索集成配置文件<br>使用云候选功能<br>发送用户注册的字<br>此外：<br>在启用此策略设置之前已添加的打开扩展词典不用于转换。<br>不使用在启用此策略设置之前已安装的搜索集成配置文件。<br>**1** - 允许<br>默认情况下，可以添加和使用“打开扩展词典”。 此外，默认可以使用搜索集成功能。<br>用户可：<br>使用云候选功能<br>发送用户注册的字。|
|**TextInput/AllowIMELogging**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 误转换日志记录已关闭。 自动优化的数据和输入历史记录数据不会保存到文件。<br>**1** - 误转换日志记录已启用。 自动优化的数据和输入的历史记录数据会保存到文件（默认值）|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**TextInput/AllowJapaneseIVSCharacters**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**TextInput/AllowJapaneseUserDictionary**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 不筛选任何字符（默认值）<br>**1** - 对除 Shift JIS 字符之外的所有字符进行筛选|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br /><br />**0** - 不筛选任何字符（默认值）<br>**1** - 对除 JIS0208 字符之外的所有字符进行筛选|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 不筛选任何字符（默认值）<br>**1** - 对除 JIS0208 字符或 EUDC 字符之外的所有字符进行筛选|
|**TextInput/AllowInputPanel**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Bluetooth/AllowDiscoverableMode**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Bluetooth/AllowAdvertising**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowDataSense**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowVPN**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowWorkplace**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowDateTime**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowLanguage**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowRegion**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowSignInOptions**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowYourAccount**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowPowerSleep**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Settings/AllowAutoPlay**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Experience/AllowCortana**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**Search/SafeSearchPermissions**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 严格，针对成人内容的最高筛选<br>**1** - 适度，针对成人内容的中等筛选（不筛选有效的搜索结果 - 默认值）|
|**Experience/AllowCopyPaste**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**强制开始大小**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 允许用户更改大小（默认值）<br>**1** - 强制非全屏<br>**2** - 强制全屏|
|**Update/RequireDeferUpgrade**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：不推迟升级（保留在当前分支 (CB) 内 - 默认值）<br>**1**：允许推迟更新和升级（设备遵循当前业务分支 (CBB) 规则）<br /><br />有关详情，请参阅：<br>[Windows 10 服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>（桌面版和移动版）|**说明：**将软件更新延迟至多 4 周的策略<br /><br />**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br> **0**：立即应用更新（默认）<br>**1** - **4**：延迟与软件更新的周数。<br /><br />有关详情，请参阅：<br>[Windows 10 服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>（桌面版和移动版）|**说明：**将功能升级延迟至多 8 个月的策略<br /><br />**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：立即应用更新（默认）<br>**1** - **8**：延迟功能升级的月数。<br /><br />有关详情，请参阅：<br>[Windows 10 服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>（桌面版和移动版）|**说明：**允许 CBB 计算机在 5 周内停止接收更新和升级。 更新出现问题时应使用此设置。<br /><br />**URI 完整路径：**./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：立即应用更新（默认）<br>**1**：暂停更新和升级（将在 5 周后过期）|

### Windows Defender URI 设置

|策略名称|详细信息|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowBehaviorMonitoring**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowIntrusionPreventionSystem**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowIOAVProtection**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowScriptScanning**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowOnAccessProtection**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**RealTimeScanDirection**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 监视所有文件（双向 - 默认值）<br>**“1”** - 监视传入的文件<br>**“2”** - 监视传出的文件|
|**DaysToRetainCleanedMalware**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - **90** – 表示保留恶意软件的时间<br>**默认值：****0** – 永久保留在隔离文件夹中，并且不会自动删除|
|**AllowUserUIAccess**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**ScanParameter**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**1** – 快速扫描（默认值）<br>**2** - 完全扫描|
|**ScheduleScanDay**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 每天（默认值）<br>**1** - 星期一<br>**2** - 星期二<br>**3** - 星期三<br>**4** - 星期四<br>**5** - 星期五<br>**6** - 星期六<br>**7** - 星期日<br>**“8”** - 没有计划的扫描|
|**ScheduleScanTime**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 上午 12:00<br>**“60”** - 上午 1:00<br>**120** – 凌晨 2:00（默认值）<br>**“180”** - 上午 3:00<br>**“240”** - 上午 4:00<br>**“300”** - 上午 5:00<br>**“360”** - 上午 6:00<br>**“420”** - 上午 7:00<br>**“480”** - 上午 8:00<br>**“540”** - 上午 9:00<br>**“600”** - 上午 10:00<br>**“660”** - 上午 11:00<br>**“720”** - 中午 12:00<br>**“780”** - 下午 1:00<br>**“840”** - 下午 2:00<br>**“900”** - 下午 3:00<br>**“960”** - 下午 4:00<br>**“1020”** - 下午 5:00<br>**“1080”** - 下午 6:00<br>**“1140”** - 下午 7:00<br>**“1200”** - 下午 8:00<br>**“1260”** - 下午 9:00<br>**“1320”** - 下午 10:00<br>**“1381”** - 维护时段|
|**ScheduleQuickScanTime**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 上午 12:00<br>**“60”** - 上午 1:00<br>**120** – 凌晨 2:00（默认值）<br>**“180”** - 上午 3:00<br>**“240”** - 上午 4:00<br>**“300”** - 上午 5:00<br>**“360”** - 上午 6:00<br>**“420”** - 上午 7:00<br>**“480”** - 上午 8:00<br>**“540”** - 上午 9:00<br>**“600”** - 上午 10:00<br>**“660”** - 上午 11:00<br>**“720”** - 中午 12:00<br>**“780”** - 下午 1:00<br>**“840”** - 下午 2:00<br>**“900”** - 下午 3:00<br>**“960”** - 下午 4:00<br>**“1020”** - 下午 5:00<br>**“1080”** - 下午 6:00<br>**“1140”** - 下午 7:00<br>**“1200”** - 下午 8:00<br>**“1260”** - 下午 9:00<br>**“1320”** - 下午 10:00<br>**“1380”** - 下午 11:00|
|**AVGCPULoadFactor**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**数据类型：** 整数<br /><br />**允许的值：0** - **100**（默认值：**50**）|
|**AllowArchiveScanning**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowEmailScanning**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**数据类型：** 整数<br>**允许的值：**<br>**0** – 不允许（默认值）<br>**“1”** - 允许|
|**AllowFullScanRemovableDriveScanning**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 不允许（默认值）<br>**“1”** - 允许|
|**AllowFullScanOnMappedNetworkDrives**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**AllowScanningNetworkFiles**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）– 在 RTP 已启用并设置为允许时也会运行|
|**SignatureUpdateInterval**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不以某个间隔检查签名<br>**1** - 每隔 1 小时检查一次签名<br>**“2”** - 每隔 2 小时等间隔检查一次签名<br>**“24”** - 每隔一天检查一次签名<br>**默认值：** 8 - 每隔 8 小时检查一次签名|
|**AllowCloudProtection**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**“0”** - 不允许<br>**1** – 允许（默认值）|
|**SubmitSamplesConsent**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** - 始终提示（提示）<br>**“1”** - 自动发送安全示例<br>**“2”** - 从不发送<br>**“3”** - 自动发送所有示例|
|**ExcludedExtensions**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**数据类型：**字符串<br /><br />**允许的值：**<br>*&lt;以分号分隔的扩展名列表&gt;*，如 **obj;lib**<br>**默认值：**未排除任何扩展名|
|**ExcludedPaths**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**数据类型：**字符串<br /><br />**允许的值：**<br /><br />*&lt;以分号分隔的路径列表&gt;*<br /><br />示例：**c:\test;c:\test1.exe**<br /><br />**默认值：** 未排除任何路径|
|**ExcludedProcesses**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**数据类型：**字符串<br /><br />**允许的值：**<br>*&lt;以分号分隔的路径列表&gt;*<br>示例：**c:\test.exe;c:\test1.exe**<br>**默认值：** 未排除任何进程|

### Edge 浏览器 URI 设置

|策略名称|详细信息|
|---------------|------------|-----------|
|**允许使用浏览器**<br>（仅限移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：已关闭浏览<br>**1**：已打开浏览（默认值）|
|**AllowSearchSuggestionsinAddressBar**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：不显示搜索建议<br>**1**：显示搜索建议（默认值）|
|**SendIntranetTraffictoInternetExplorer**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0**：已禁用（在 Edge 浏览器中打开 Intranet 站点 - 默认值））<br>**1** – 已启用（在 Internet Explorer 中打开 Intranet 站点）。|
|**允许使用 Do Not Track**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 已禁用（不发送 DNT - 默认值）<br>**1** – 已启用（不发送）|
|**配置 SmartScreen**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 不允许<br>**1** – 允许（默认值）|
|**允许弹出窗口**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 阻止弹出窗口（默认值）<br>**1** – 允许弹出窗口|
|**允许使用 Cookie**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 不阻止。 允许所有网站的 cookie（默认）<br>**1** – 阻止仅第三方 cookie<br>**2** – 阻止所有 cookie|
|**允许保存密码**<br>（桌面版和移动版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 禁用密码管理器； <br>**1** – 启用密码管理器（默认值）|
|**允许自动填充**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**数据类型：** 整数<br /><br />**允许的值：**<br>**0** – 已禁用（默认值）<br>**1** – 已启用|
|**配置企业站点列表**<br>（仅限桌面版）|**URI 完整路径：**./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**数据类型：**字符串<br /><br />**允许的值：<br>0** – 未配置<br>**1** – 如果进行了配置，则使用 IE 的企业模式站点列表（默认值）<br>**2** – 指定企业站点列表位置|

### 另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Jun16_HO1-->


