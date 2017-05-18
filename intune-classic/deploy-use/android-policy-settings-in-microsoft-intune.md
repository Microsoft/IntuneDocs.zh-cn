---

title: "Android 和 Samsung KNOX 策略设置 | Microsoft Docs"
description: "创建控制通过 Intune 管理的 Android 设备上的设置及功能的策略。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: 2da96c2ffb6cc826494972ab8c88ce62981eeae6


---

# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 和 Samsung KNOX 标准版策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供了一系列内置常规设置，你可以在 Android 设备上进行配置。 此外，还可指定开放移动联盟统一资源标识符 (OMA-URI) 值创建 Intune 未提供的自定义设置。

## <a name="general-configuration-policy"></a>常规配置策略

使用 Intune **Android 常规配置策略**为以下对象配置设置：

-   **移动设备安全设置** – 从让你能够控制设备上的一系列功能的预定义设置列表中选择。

-   **展台模式**（仅适用于 Samsung KNOX 标准版设备）– 锁定设备以只允许某些功能工作。 例如，你可以让设备只运行一个指定的托管应用，也可以禁用设备上的音量按钮。 这些设置可用于设备的演示模型，也可用于专门执行一个功能的设备（如销售点设备）。

-   **相容和不相容应用** - 指定在你的公司中相容或不相容的应用列表。 在 Android 和 iOS 设备上，“**不相容应用报告**”可用于查看你在列表中指定的应用对于用户已经安装的应用的相容性。 该报表不能实际阻止应用的安装。

> [!TIP]
> 你可以为用户配置条款和条件，确保他们确认其设备上的所有应用（包括个人应用）将会受到评估，不相容的应用将被阻止或报告为不相容。 用户必须接受这些条款和条件，然后才能注册其设备并使用公司门户获取应用。 有关使用条款和条件的详细信息，请参阅 [Microsoft Intune 中的条款和条件策略](terms-and-condition-policy-settings-in-microsoft-intune.md)。

如果你寻找的设置没有在本主题中出现，你可能能够使用 Android 自定义策略创建它，该自定义策略允许你使用 OMA-URI 设置来控制设备。 有关详细信息，请参阅本主题后面的“[自定义策略设置](#custom-policy-settings)”。

### <a name="password-settings"></a>密码设置

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|-|----------------|----------------|
|**需要密码才可解锁移动设备**|指定支持的设备上是否需要密码。|是|是|
|**最短密码长度**|指定密码的最短长度。|是|是|
|**擦除设备前允许的重复登录失败次数**|指定在擦除设备前允许的登录失败次数。|是|是|
|**屏幕关闭前处于不活动状态的分钟数**|指定设备自动锁定之前处于非活动状态的分钟数。|是|是|
|**密码过期（天数）**|指定必须更改密码前的天数。|是|是|
|**记住密码历史记录**|指定要记住的以前所用密码的数量。|是|是|
|**“记住密码历史记录”** - **“防止重用以前的密码”**|防止重用以前的密码。|是|是|
|**密码质量**|指定所需的密码复杂性级别以及是否可以使用生物识别设备。|是|是|
|**允许指纹解锁**|允许使用指纹对设备解锁。|否|是|
|**允许 Smart Lock 和其他信任代理**<br>（Android 5 及更高版本）|让你控制兼容 Android 设备上的 Smart Lock 功能。 如果设备处于可信位置（例如当它连接到特定蓝牙设备时，或者在 NFC 标记附近时），则此手机功能（有时称为信任代理）使你可以禁用或绕过设备锁屏界面密码。可以使用此设置防止用户配置 Smart Lock。|是|否|

### <a name="encryption-settings"></a>加密设置

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|---|-------------|----------------|
|**需要对移动设备加密**|要求对移动设备上的文件进行加密。|是|是|
|**需要对存储卡进行加密**|指定是否必须对设备存储卡进行加密。|否|是|

### <a name="system-settings"></a>系统设置

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|---|-------------|----------------|
|**允许屏幕捕获**|让用户以图像形式捕获屏幕内容。|否|是|
|**允许提交诊断数据**|允许设备将诊断信息提交到 Google。|否|是|
|**允许恢复出厂设置**|允许用户对设备执行恢复出厂设置。|否|是|

### <a name="cloud-settings---documents-and-data"></a>云设置 - 文档和数据

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|----|------------------------|----------------|
|**允许 Google 备份**|允许使用 Google 备份。|否|是|

### <a name="cloud-settings---accounts-and-synchronization"></a>云设置 - 帐户和同步

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|-----|-----------|----------------|
|**允许 Google 帐户自动同步**|允许 Google 帐户设置自动同步。|否|是|

### <a name="application-settings---browser"></a>应用设置 - 浏览器

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|-----|-----------|----------------|
|**允许 Web 浏览器**|指定是否可以使用设备的默认 Web 浏览器。|否|是|
|**允许自动填充**|允许使用 Web 浏览器的自动填充功能。|否|是|
|**允许使用弹出窗口阻止程序**|允许使用 Web 浏览器中的弹出窗口阻止程序。|否|是|
|**允许使用 Cookie**|允许设备 Web 浏览器使用 Cookie。|否|是|
|**允许使用活动脚本**|允许设备 Web 浏览器使用活动脚本。|否|是|

### <a name="application-settings---apps"></a>应用设置 - 应用程序

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|----|------------|----------------|
|**允许 Google Play 商店**|允许用户访问设备上的 Google Play 商店。|否|是|

### <a name="device-capabilities-settings---hardware"></a>设备性能设置 - 硬件

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|-----|-----------|----------------|
|**允许照相机**|允许使用设备相机。|是|是|
|**允许可移动存储**|允许设备使用可移动存储，如 SD 卡。|否|是|
|**允许 Wi-Fi**|允许使用设备的 Wi-Fi 功能。|否|是|
|**允许 Wi-Fi tethering**|允许在设备上使用 Wi-Fi Tethering。|否|是|
|**允许地理位置**|允许设备利用位置信息。|否|是|
|**允许 NFC**|允许使用近场通信（如果设备支持）的操作。|否|是|
|**允许蓝牙**|允许在设备上使用蓝牙。|否|是|
|**允许关闭电源**|允许用户关闭设备电源。<br /><br />如果禁用了此设置，则 Samsung KNOX 标准版设备的“擦除设备前允许重复登录失败的次数”设置不起作用。|否|是|

### <a name="device-capabilities-settings---cellular"></a>设备性能设置 - 蜂窝网络

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|---|-------------|----------------|
|**允许语音漫游**|当设备处于移动电话网络中时允许语音漫游。|否|是|
|**允许数据漫游**|当设备处于移动电话网络中时允许数据漫游。|否|是|
|**允许 SMS/MMS 消息传送**|允许在设备上使用短信和彩信消息传送。|否|是|

### <a name="device-capabilities-settings---features"></a>设备性能设置 - 功能

|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|----------------|----|------------|----------------|
|**允许使用语音助手**|允许在设备上使用语音助手软件。|否|是|
|**允许语音拨号**|启用或禁用设备上的语音拨号功能。|否|是|
|**允许复制和粘贴**|允许使用设备上的复制和粘贴功能。|否|是|
|**允许应用程序之间共享剪贴板**|使用使用剪贴板在应用之间进行复制和粘贴。|否|是|
|**允许 YouTube**|允许在设备上使用 YouTube。|否|是|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>相容和不相容应用的设置
在“**相容和不相容应用**”列表中，指定使用以下信息的相容或不相容应用列表：

> [!NOTE]
> 单个策略只能包含一个相容应用列表或一个不相容应用列表。 不能在同一策略中同时指定两个列表。

|设置名|详细信息|
|----------------|--------------------|
|**用户安装列出的应用时报告不相容情况**|列出未由 Intune 托管的、你不希望用户安装和运行的应用。 如果用户安装其中的任一应用，不合规应用报告中将列出该应用。|
|**用户安装列出的应用时不报告不相容情况**|列出要允许运行的应用。 为了保持合规状态，用户不得安装未列出的任何应用。 自动允许由 Intune 托管的应用。|
|**添加**|将应用添加到选定的列表。 在应用商店中指定应用的名称、应用发布者（可选）和应用的 URL。<br /><br />有关详细信息，请参阅本主题后面的“[指定应用商店的 URL](#specify-urls-to-app-stores)”。|
|**导入应用**|导入你已在逗号分隔值文件中指定的应用列表。 在文件中使用格式、应用程序名称、发布者和应用 URL。|
|**编辑**|允许你编辑选定应用的名称、发布者和 URL。|
|**删除**|从列表中删除选定的应用。|

必须将包含合规和不合规应用设置的策略部署到用户组。

### <a name="kiosk-mode-settings"></a>展台模式设置
为“Samsung KNOX 标准版设备”指定以下设置：

|设置名|详细信息|
|----------------|--------------------|
|**选择当设备处于展台模式时可以运行的托管应用**|选择“**浏览**”，然后选择当设备处于展台模式时可以运行的托管应用（目前尚不支持指定为指向应用商店的链接的应用）。 不允许在设备上运行其他应用。|
|**允许使用音量按钮**|启用或禁用设备上的音量按钮。|
|**允许使用屏幕睡眠唤醒按钮**|启用或禁用设备上的屏幕睡眠唤醒按钮。|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>相容和不相容应用的参考信息

#### <a name="monitor-compliant-and-noncompliant-apps"></a>监视相容和不相容应用
使用“不相容应用报告”  查看允许和阻止的应用的相容性。

###### <a name="to-run-the-noncompliant-apps-report"></a>运行不相容应用报告

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“报告”&gt;“不合规应用报告”。

2.  选择要进行检查的设备组。 然后，选择是否要检查相容应用和/或不相容应用。 最后，选择“**查看报告**”。

#### <a name="specify-urls-to-app-stores"></a>指定应用商店的 URL
若要在相容应用和不相容应用列表中指定应用 URL，请执行以下步骤：

在 [Google Play 的应用部分](https://play.google.com/store/apps)中，搜索你想要使用的应用。

打开应用的安装页面，然后将 URL 复制到剪贴板。 你现在可以在符合或不符合要求的应用列表中使用这个 URL。

示例：搜索适用于 Microsoft Office Mobile 的 Google Play。 你使用的 URL 将为 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

## <a name="custom-policy-settings"></a>自定义策略设置
使用 Microsoft Intune 的 **Android 自定义配置策略**来部署可用于控制 Android 设备功能的 OMA URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在使你能够部署不能使用 Intune 策略配置的 Android 设置。
Intune 目前支持有限数量的 Android 自定义策略。 请参阅本主题的示例，查找可配置的策略。

### <a name="general-settings"></a>常规设置

|设置名|详细信息|
    |----------------|--------------------|
    |**Name**|输入 Android 自定义策略的唯一名称，以帮助你在 Intune 控制台中识别它。|
    |**描述**|提供对 Android 自定义策略的概述以及可帮助你查找它的其他相关信息。|

### <a name="oma-uri-settings"></a>OMA-URI 设置

   |设置名|详细信息|
    |--------|--------------------|
    |**设置名称**|输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。|
    |**设置描述**|提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。|
    |**数据类型**|选择将在其中指定此 OMA-URI 设置的日期类型。 从“**字符串、字符串 (XML)、日期和时间、整数、浮点**”，或者“**布尔值**”中进行选择。|
    |**OMA-URI（区分大小写）**|指定需为其提供设置的 OMA-URI。|
    |**值**|指定要与之前指定的 OMA-URI 关联的值。|

### <a name="examples"></a>示例

- [创建具有预共享密钥的 Wi-Fi 配置文件](pre-shared-key-wi-fi-profile.md)
- [使用自定义策略创建适用于 Android 设备的 per-app VPN 配置文件](per-app-vpn-for-android-pulse-secure.md)
- [使用自定义策略允许和阻止适用于 Samsung KNOX 设备的应用](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Jan17_HO4-->


