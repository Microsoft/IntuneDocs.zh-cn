---
title: "适用于 Windows 10 设备的 Intune 自定义设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可以在 Windows 10 自定义配置文件中使用的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 647415914fb0f44807eff7baf7a56ea3a382f027
ms.lasthandoff: 02/18/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Windows 10 设备的自定义设备设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 使用适用于 Windows 10 和 Windows 10 移动版的 Microsoft Intune **自定义**配置文件来部署可用于控制设备功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 Windows 10 通过“[策略配置服务提供程序(策略 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)”提供许多设置。

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](how-to-configure-custom-settings.md)中的说明进行操作。
2. 在“创建配置文件”边栏选项卡上，选择“设置”添加&1; 个或多个 OMA-URI 设置。
3. 在“自定义 OMA-URI 设置”边栏选项卡上，单击“添加”可添加新值。 还可以单击“导出”创建逗号分隔值 (.csv) 文件中配置的所有值的列表。
4. 对于想要添加的每个 OMA URI 设置，请输入以下信息。 使用本主题中的列表了解可以使用的设置：
    - **设置名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **设置描述** -（可选）输入设置的描述。
    - **数据类型** -从以下各项选择：
        - **字符串**
        - **字符串 (XML)**
        - **日期和时间**
        - **整数**
        - **浮点**
        - **布尔值**
    - **OMA-URI（区分大小写）** - 指定想要为其提供设置的 OMA-URI。
    - **值** - 指定要与输入的 OMA-URI 关联的值。
5. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。
将创建配置文件并在“配置文件列表”边栏选项卡上显示。

## <a name="example"></a>示例
在以下屏幕截图中，已启用设置 **Connectivity/AllowVPNOverCellular**。 这样一来，Windows 10 设备在处于移动电话网络中时会打开 VPN 连接。

> ![包含 VPN 设置的自定义策略的示例](./media/custom-policy-example.png)


## <a name="policy-settings"></a>策略设置

|策略名称和 URI|详细信息|
|---------------|------------|-----------|
|**允许自动更新**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|仅限桌面版<br>**数据类型：** 整数<br />**值：** **0** - **5**（默认值：**1**）|
|**计划安装日期**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|仅限移动版<br>**数据类型：** 整数<br />**值：**<br>**0** - 每天（默认值）<br>**1** - 星期日<br>**2** - 星期一<br>**3** - 星期二<br>**4** - 星期三<br>**5** - 星期四<br>**6** - 星期五<br>**7** - 星期六|
|**计划安装时间**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** – **23** 小时（**0** 表示午夜）（默认值：**3**）|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**0** - 用户不能设置密码的宽限期计时器；值设置为“每次”<br>**1** - 用户可以设置密码的宽限期计时器（默认值）|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**0** – 不允许**使用 Wi-Fi 连接**。<br>**1** – **允许使用 Wi-Fi 连接**（默认值）|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|桌面版和移动版<br>**数据类型：** 整数<br />**值：** **0** – 不允许 Internet 共享，**1** – 允许 Internet 共享（默认值）|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**0** –只允许 MDM 预配的 Wi-Fi 连接。<br>**1** - 除 MDM 已预配的网络外，允许添加新网络 SSID（默认值）|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|桌面版和移动版<br>**数据类型：** 整数<br />**值：**<br>**“0”** - 不允许（Enterprise 版仅设置）<br>**“1”** - 有限<br>**2** – 完全（默认值）<br>**3** - 完全和诊断信息|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**“0”** - 不允许<br>**1** - 仅设置（默认值）<br>**2**- 设置和实验|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**0** - 不允许防盗模式<br>**1** - 用户首选项（默认值）|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**0** - 不允许 VPN 使用手机网络<br>**1** - VPN 可以使用任何连接，包括手机网络（默认值）|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**0** – 不允许用户打开蓝牙。<br>**1** – 保留。 用户可以启用和配置蓝牙（在适用于 MDM、EAS 的 Windows Phone 8.1、Windows 10 桌面版或 Windows 10 移动版中不受支持）<br>**2** - 允许。 用户可以启用和配置蓝牙（默认值）|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** – 不允许漫游，**1** - 允许漫游（默认值）|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|仅限移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**、**1**（默认值）|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**、**1**（默认值）|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**（默认值）、**1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**“0”** - 不允许<br>“打开扩展词典”已禁用。<br>用户不可：<br>-添加新的“打开扩展词典”<br />-添加新的搜索集成配置文件<br>-使用云候选功能<br>-发送用户注册的字。<br>**1** - 允许<br>默认情况下，可以添加和使用“打开扩展词典”。 此外，默认可以使用搜索集成功能。<br>用户可：<br>使用云候选功能。|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 误转换日志记录已禁用。<br>**1** - 误转换日志记录已启用（默认值）|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 不筛选任何字符（默认值）<br>**1** - 对除 Shift JIS 字符之外的所有字符进行筛选|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br />**0** - 不筛选任何字符（默认值）<br>**1** - 对除 JIS0208 字符之外的所有字符进行筛选|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 不筛选任何字符（默认值）<br>**1** - 对除 JIS0208 字符或 EUDC 字符之外的所有字符进行筛选|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**“0”** - 严格，针对成人内容的最高筛选<br>**1** - 适度，针对成人内容的中等筛选（不筛选有效的搜索结果 - 默认值）|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**强制开始大小**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|仅限移动版<br />**数据类型：** 整数<br />**值：**<br>**0** - 允许用户更改大小（默认值）<br>**1** - 强制非全屏<br>**2** - 强制全屏|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**0**：不推迟升级（保留在当前分支 (CB) 内 - 默认值）<br>**1**：允许推迟更新和升级（设备遵循当前业务分支 (CBB) 规则）<br />有关详细信息，请参阅：<br>[Windows 10 维护服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|桌面版和移动版<br>**说明：**将软件更新延迟至多 4 周的策略<br />**数据类型：** 整数<br />**值：**<br> **0**：立即应用更新（默认）<br>**1** - **4**：延迟与软件更新的周数。<br />有关详细信息，请参阅：<br>[Windows 10 维护服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|桌面版和移动版<br>**说明：**将功能升级延迟至多 8 个月的策略<br />**数据类型：** 整数<br />**值：**<br>**0**：立即应用更新（默认）<br>**1** - **8**：延迟功能升级的月数。<br />有关详细信息，请参阅：<br>[Windows 10 维护服务简介](https://technet.microsoft.com/library/mt598226.aspx)<br>[Windows 10 部署规划](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|桌面版和移动版<br>**说明：**允许设备在 5 周内停止接收更新和升级。<br />**数据类型：** 整数<br />**值：**<br>**0**：立即应用更新（默认）<br>**1**：暂停更新和升级（将在 5 周后过期）|

## <a name="windows-defender-settings"></a>Windows Defender 设置

|策略名称和 URI|详细信息|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** – 监视所有文件（默认值）<br>**“1”** - 监视传入的文件<br>**“2”** - 监视传出的文件|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - **90** – 表示保留恶意软件的时间<br>**默认：** **0** – 永久保留在隔离文件夹中，并且不会自动删除|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**1** – 快速扫描（默认值）<br>**2** - 完全扫描|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 每天（默认值）<br>**1** - 星期一<br>**2** - 星期二<br>**3** - 星期三<br>**4** - 星期四<br>**5** - 星期五<br>**6** - 星期六<br>**7** - 星期日<br>**“8”** - 没有计划的扫描|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 上午 12:00<br>**“60”** - 上午 1:00<br>**120** – 凌晨 2:00（默认值）<br>**“180”** - 上午 3:00<br>**“240”** - 上午 4:00<br>**“300”** - 上午 5:00<br>**“360”** - 上午 6:00<br>**“420”** - 上午 7:00<br>**“480”** - 上午 8:00<br>**“540”** - 上午 9:00<br>**“600”** - 上午 10:00<br>**“660”** - 上午 11:00<br>**“720”** - 中午 12:00<br>**“780”** - 下午 1:00<br>**“840”** - 下午 2:00<br>**“900”** - 下午 3:00<br>**“960”** - 下午 4:00<br>**“1020”** - 下午 5:00<br>**“1080”** - 下午 6:00<br>**“1140”** - 下午 7:00<br>**“1200”** - 下午 8:00<br>**“1260”** - 下午 9:00<br>**“1320”** - 下午 10:00<br>**“1381”** - 维护时段|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|仅限桌面版<br>**数据类型：** 整数<br />**值：**<br>**0** - 上午 12:00<br>**“60”** - 上午 1:00<br>**120** – 凌晨 2:00（默认值）<br>**“180”** - 上午 3:00<br>**“240”** - 上午 4:00<br>**“300”** - 上午 5:00<br>**“360”** - 上午 6:00<br>**“420”** - 上午 7:00<br>**“480”** - 上午 8:00<br>**“540”** - 上午 9:00<br>**“600”** - 上午 10:00<br>**“660”** - 上午 11:00<br>**“720”** - 中午 12:00<br>**“780”** - 下午 1:00<br>**“840”** - 下午 2:00<br>**“900”** - 下午 3:00<br>**“960”** - 下午 4:00<br>**“1020”** - 下午 5:00<br>**“1080”** - 下午 6:00<br>**“1140”** - 下午 7:00<br>**“1200”** - 下午 8:00<br>**“1260”** - 下午 9:00<br>**“1320”** - 下午 10:00<br>**“1380”** - 下午 11:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - **100**（默认值：**50**）|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|仅限桌面版<br />**数据类型：** 整数<br>**值：** **0** - 不允许（默认值），**1** – 允许|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许（默认值），**1** – 允许|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** – 不允许，**1** – 允许（默认值）– 在 RTP 已启用并设置为允许时也会运行|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 不以某个间隔检查签名<br>**1** - 每隔&1; 小时检查一次签名<br>**2** – 每隔 2 小时检查一次<br>**24** – 每天检查一次<br>**默认值：** 8 – 每隔 8 小时检查一次|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** - 不允许，**1** – 允许（默认值）|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0** - 始终提示（提示）<br>**“1”** - 自动发送安全示例<br>**“2”** - 从不发送<br>**“3”** - 自动发送所有示例|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|仅限桌面版<br />**数据类型：**字符串<br />**值：**<br>*&lt;以分号分隔的扩展名列表&gt;*，如 **obj;lib**<br>**默认值：**未排除任何扩展名|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|仅限桌面版<br />**数据类型：**字符串<br />**值：**<br />&lt;以分号分隔的路径列表&gt;<br />示例：**c:\test;c:\test1.exe**<br />**默认值：** 未排除任何路径|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|仅限桌面版<br />**数据类型：**字符串<br />**值：**<br>&lt;以分号分隔的路径列表&gt;<br>示例：**c:\test.exe;c:\test1.exe**<br>**默认值：** 未排除任何进程|

## <a name="edge-browser-settings"></a>Microsoft Edge 浏览器设置

|策略名称和 URI|详细信息|
|---------------|------------|-----------|
|**允许使用浏览器**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|仅限移动版<br />**数据类型：** 整数<br />**值：** **0**：浏览禁用，**1**浏览启用（默认值）|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0**：不显示建议，**1**：显示建议（默认值）|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|仅限桌面版<br />**数据类型：** 整数<br />**值：**<br>**0**：已禁用（在 Microsoft Edge 浏览器中打开 Intranet 站点 - 默认值））<br>**1** – 已启用（在 Internet Explorer 中打开 Intranet 站点）。|
|**允许使用 Do Not Track**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|桌面版和移动版）<br />**数据类型：** 整数<br />**值：** **0** – 已禁用（不发送 DNT - 默认值），**1** – 已启用（发送 DNT）|
|**配置 SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|桌面版和移动版<br />**数据类型：** 整数<br />**值：** **0** – 不允许，**1** – 允许（默认值）|
|**允许弹出窗口**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** – 阻止弹出窗口（默认值），**1** – 允许弹出窗口|
|**允许使用 Cookie**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**0** – 允许所有网站的 cookie（默认值）<br>**1** – 阻止仅第三方 cookie<br>**2** – 阻止所有 cookie|
|**允许保存密码**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|桌面版和移动版<br />**数据类型：** 整数<br />**值：**<br>**0** – 禁用密码管理器； <br>**1** – 启用密码管理器（默认值）|
|**允许自动填充**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|仅限桌面版<br />**数据类型：** 整数<br />**值：** **0** – 已禁用（默认值），**1** – 已启用|
|**配置企业站点列表**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|仅限桌面版<br />**数据类型：**字符串<br />**值：<br>**0** – 未配置<br>**1** – 使用 IE 的企业模式站点列表（如果已配置，默认值）<br>**2** – 指定企业站点列表的位置|

