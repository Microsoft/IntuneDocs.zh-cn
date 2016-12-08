---
title: "移动设备安全策略设置 | Microsoft Intune"
description: "使用 Intune 配置各种可部署到组织中的托管设备的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: a64336ad959daad9685bdfbef3c284a14e708894



---

# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的移动设备安全策略设置
> [!IMPORTANT]
> 现在，Microsoft Intune 针对每个设备平台都具有单独的配置策略。 这些策略包含可使用的最新设置。 你可以继续使用移动设备安全策略，并且任何现有的部署仍将起作用。 但是，你应计划尽快迁移到新的配置策略，因为以后会删除移动设备安全策略。

你可使用 Intune 移动设备安全策略配置各种可部署到组织中的托管设备的设置。 这些设置用于控制设备的功能和安全性。

可为下列设备类型创建和部署移动设备安全策略：

-   Windows RT 8.1 和注册的 Windows 8.1 设备

-   Windows RT

-   Windows Phone 8 和 Windows Phone 8.1

-   iOS

-   Android 和 Samsung KNOX 标准版

> [!NOTE]
> 某些设置并不适用于某些设备。 请参阅下表，获取可配置的设置的完整列表。
> 从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 公司门户应用的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 和 WinRT 平台的支持。 因此，将无法注册或更新任何 Windows Phone 8 或 WinRT 设备。 可以继续管理已注册的 Windows Phone 8、WinRT 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。

## <a name="security-settings"></a>安全设置

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要密码才可解锁移动设备**|否|否|是|是|是|
|**所需的密码类型**<br /><br />此设置指定需要的密码类型，例如仅限数字或字母数字。|是|是|是|是|否|
|**必填密码类型 – 字符集最小数量**<br /><br />有以下四个字符集：小写字母、大写字母、数字和符号。 此设置指定密码中必须包括多少个不同的字符集。 但是，对于 iOS 设备，此设置指定密码中必须包括的符号字符的数量。|是|是|是|是|否|
|**最短密码长度**|是|是|是|是|是|
|**允许简单密码**<br /><br />简单密码包括“0000”和“1234”。|否|否|是|是|否|
|**擦除设备前允许的重复登录失败次数**|是|是|是|是|是|
|**屏幕关闭前处于非活动状态的分钟数**1|是|是|是|是|是|
|**密码过期（天数）**|是|是|是|是|是|
|**记住密码历史记录**|是|是|是|是|是|
|**“记住密码历史记录”** – **“防止重用以前的密码”**|是|是|是|是|是|
|**密码质量**|否|否|否|否|是|
|**允许图片密码和 PIN**|是|是|否|否|否|
|**需要提供密码之前处于非活动状态的分钟数**|否|否|否|是|否|
|**允许指纹解锁**|否|否|否|iOS 7 及更高版本|否|
1对于 iOS 设备，配置“屏幕关闭前处于非活动状态的分钟数”和“需要提供密码之前处于非活动状态的分钟数”设置时，它们会按顺序应用。 例如，如果你设置的两个设置的值均为“5”  分钟，屏幕在 5 分钟后将自动关闭，然后再过 5 分钟后该设备将锁定。 但是，如果用户手动关闭屏幕，第二个设置将立即应用。 在相同的示例中，用户关闭屏幕后，该设备将在 5 分钟后锁定。

当你将密码长度策略部署到运行 Windows RT 的设备时，用户会被强制重置密码，即使他们当前的密码是符合策略要求的。

## <a name="encryption-settings"></a>加密设置

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要对移动设备加密**1<br /><br />对于 Windows Phone 8 设备，必须将其设置为 **“是”**。<br /><br />若要在 iOS 设备上启用加密，请启用设置 **“需要密码以解锁移动设备”**。|是|否|是|否|是|
|**需要对存储卡进行加密**<br /><br />此设置也适用于由 Exchange ActiveSync 托管的设备。|n/a|n/a|n/a <br />会对应用和关联的数据进行自动加密。|n/a|是|
1以下是运行 Windows 8.1 的设备的其他信息：

-   若要在运行 Windows 8.1 的设备上强制加密，必须在每台设备上安装 [用于 Windows 的 December 2014 MDM 客户端更新](http://support.microsoft.com/kb/3013816) 。

-   如果对 Windows 8.1 设备启用此设置，则该设备的所有用户必须都具有 Microsoft 帐户。

-   为了使加密正常工作，该设备必须满足 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 硬件认证要求。

-   在设备上强制加密时，恢复密钥仅可从用户的 Microsoft 帐户（从用户的 OneDrive 帐户访问）进行访问。 无法代表用户恢复此密钥。

## <a name="malware-settings"></a>恶意软件设置

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要网络防火墙**|是|否|否|否|否|
|**启用 SmartScreen**|是|否|否|否|否|

## <a name="system-settings"></a>系统设置

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**需要自动更新**|是|否|否|否|否|
|**需要自动更新 - 要自动安装的最小更新分类**<br /><br />选择将自动安装的更新分类：<br /><br />- **重要说明**。 安装归类为重要的所有更新。<br /><br />- **推荐**。 安装归类为重要或推荐的所有更新。|是|否|否|否|否|
|**允许屏幕捕获**|否|否|仅 Windows Phone 8.1|是|是（仅 Samsung KNOX 标准版）|
|**允许在锁定屏幕中使用控制中心**|否|否|否|iOS 7 及更高版本|否|
|**允许在锁定屏幕中使用通知视图**|否|否|否|iOS 7 及更高版本|否|
|**允许在锁定屏幕中使用今日视图**|否|否|否|iOS 7 及更高版本|否|
|**用户帐户控制**|是|否|否|否|否|
|**允许提交诊断数据**|是|否|仅 Windows Phone 8.1|是|是（仅 Samsung KNOX 标准版）|
|**允许使用不受信任的 TLS 证书**|否|否|否|是|否|
|**锁定时允许使用个人钱包软件**|否|否|否|是|否|
|**允许恢复出厂设置**|否|否|否|否|是（仅 Samsung KNOX 标准版）|


## <a name="cloud-settings-documents-and-data"></a>云设置 – 文档和数据

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许备份到 iCloud**|否|否|否|是|否|
|**允许将文档与 iCloud 同步**|否|否|否|是|否|
|**允许将照片流与 iCloud 同步**|否|否|否|是|否|
|**需要加密的备份**|否|否|否|是|否|
|**工作文件夹 URL**<br /><br />此设置设置工作文件夹的 URL，以允许跨设备同步文档。|是|否|否|否|否|
|**允许 Google 备份**|否|否|否|否|是（仅 Samsung KNOX 标准版）|

## <a name="cloud-settings-accounts-and-synchronization"></a>云设置 – 帐户和同步

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**支持 Microsoft 帐户**|否|否|仅 Windows Phone 8.1|否|否|
|**允许 Google 帐户自动同步**|否|否|否|否|是（仅 Samsung KNOX 标准版）|

## <a name="email-settings"></a>电子邮件设置

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许用户下载电子邮件附件**1|n/a|n/a|n/a|n/a|n/a|
|**电子邮件同步时间段** <br /><br />此设置也适用于由 Exchange ActiveSync 托管的设备。|n/a|n/a|n/a|n/a|n/a|
|**允许支持以上部分设置的移动设备与 Exchange (Exchange ActiveSync) 进行同步** <br /><br />此设置也适用于由 Exchange ActiveSync 托管的设备。|n/a|n/a|n/a|n/a|n/a|
|**在 Windows 邮件应用程序中将 Microsoft 帐户设为可选**|是|否|否|否|否|
|**允许自定义电子邮件帐户**|否|否|仅 Windows Phone 8.1|否|否|

## <a name="application-settings---browser"></a>应用设置 - 浏览器

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许 Web 浏览器**|否|否|仅 Windows Phone 8.1|是|是（仅 Samsung KNOX 标准版）|
|**允许自动填充**|是|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许使用弹出窗口阻止程序**|是|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许使用 Cookie**|否|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许使用插件**|是|否|否|否|否|
|**允许使用活动脚本**|是|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许使用欺诈警告**|是|否|否|是|否|
|**允许 Intranet 站点使用单字条目**<br /><br />（此设置允许使用一个词将 Internet Explorer 转到某个网站，例如“必应”。）|是|否|否|否|否|
|**允许自动检测 Intranet 网络**|是|否|否|否|否|
|**互联网的安全级别**|是|否|否|否|否|
|**Intranet 安全级别**|是|否|否|否|否|
|**受信任的站点的安全级别**|是|否|否|否|否|
|**受限制的站点的安全级别**|是|否|否|否|否|
|**发送“不跟踪”标头**|是|否|否|否|否|
|**允许企业模式菜单访问**|是|否|否|否|否|
|**企业模式网站列表位置**|是|否|否|否|否|

## <a name="application-settings---apps"></a>应用设置 - 应用程序

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许应用程序商店**|否|否|仅 Windows Phone 8.1|是|是（仅 Samsung KNOX 标准版）|
|**需要提供密码来访问应用程序商店**|否|否|否|是|否|
|**允许应用内购买**|否|否|否|是|否|
|**允许在其他非托管应用中使用托管文档**|否|否|否|iOS 7 及更高版本|否|
|**允许在其他托管应用中使用非托管文档**|否|否|否|iOS 7 及更高版本|否|
|**允许视频会议**|否|否|否|是|否|
|**允许媒体存储中有成人内容**|否|否|否|是|否|
|**允许应用安装**|否|否|否|iOS 6 和更高版本|否|

## <a name="application-settings---gaming"></a>应用设置 - 游戏

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许游戏中心好友**|否|否|否|是|否|
|**允许多玩家游戏**|否|否|否|是|否|

## <a name="device-capabilities-settings---hardware"></a>设备性能设置 - 硬件

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许照相机**|否|否|仅 Windows Phone 8.1|是|是|
|**允许可移动存储**|否|否|是|否|是（仅 Samsung KNOX 标准版）|
|**允许 Wi-Fi**|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许 Wi-Fi tethering**|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许自动连接到免费 Wi-Fi 热点**|否|否|仅 Windows Phone 8.1|否|否|
|**允许 Wi-Fi 热点报告**<br /><br />此设置发送有关 Wi-Fi 连接的信息，以帮助发现附近的连接。|否|否|仅 Windows Phone 8.1|否|否|
|**允许地理位置**<br /><br />此设置允许设备利用位置信息。|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许 NFC**<br /><br />此设置允许使用近场通信的操作。|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许蓝牙**|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许关闭电源**<br>如果禁用了此设置，则 Samsung KNOX 标准版设备的“擦除设备前允许重复登录失败的次数”设置不起作用。|否|否|否|否|是（仅 Samsung KNOX 标准版）|

## <a name="device-capabilities-settings---cellular"></a>设备性能设置 - 蜂窝网络

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许语音漫游**|否|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许数据漫游**|是|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许漫游时自动同步**|否|否|否|是|否|
|**允许 SMS/MMS 消息传送**|否|否|否|否|是（仅 Samsung KNOX 标准版）|

## <a name="device-capabilities-settings---features"></a>设备性能设置 - 功能

|设置名|Windows 8.1 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|iOS|Android 和 Samsung KNOX 标准版|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**允许使用语音助手**|否|否|否|是|是（仅 Samsung KNOX 标准版）|
|**锁定设备时允许使用语音助手**|否|否|否|是|否|
|**允许语音拨号**|否|否|否|是|是（仅 Samsung KNOX 标准版）|
|**允许复制和粘贴**|否|否|仅 Windows Phone 8.1|否|是（仅 Samsung KNOX 标准版）|
|**允许应用程序之间共享剪贴板**|否|否|否|否|是（仅 Samsung KNOX 标准版）|
|**允许 YouTube**|否|否|否|否|是（仅 Samsung KNOX 标准版）|

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO1-->


