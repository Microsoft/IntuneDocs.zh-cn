---
title: "适用于 Android 的 Intune 设备限制设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用来控制 Android 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 3ba986b624e602f05eb6ab25ec30e9d58173dbd8
ms.lasthandoff: 04/19/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 和 Samsung KNOX 标准版设备限制设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>常规

|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**照相机**|允许使用设备相机。|是|是|
|**复制和粘贴**|允许使用设备上的复制和粘贴功能。|否|是|
|**在应用之间共享剪贴板**|使用使用剪贴板在应用之间进行复制和粘贴。|否|是|
|**诊断数据提交**|阻止用户从设备提交诊断数据。|否|是|
|**恢复出厂设置**|允许用户对设备执行恢复出厂设置。|否|是|
|**地理位置**|允许设备利用位置信息（仅限 Samsung KNOX 标准版）。|否|是|
|**关机**|允许用户关闭设备电源。<br>如果禁用此设置，则对于 Samsung KNOX 标准版设备，“擦除设备前登录失败的次数”设置无效。|否|是|
|**屏幕捕获**|让用户以图像形式捕获屏幕内容。|否|是|
|**语音助手**|允许在设备上使用语音助手软件。|否|是|
|**YouTube**|允许在设备上使用 YouTube 应用。|否|是|
|**共享设备**|将托管的 Samsung KNOX 标准设备配置为共享。 在此模式下，最终用户可以使用其 Azure AD 凭据登录和注销设备，并且无论设备是否正在使用，都会对其集中管理。<br>当最终用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。|否|是|

## <a name="password"></a>Password

|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**密码**|需要最终用户输入密码才能访问设备。|是|是|
|**最短密码长度**|输入用户必须配置的最短密码长度（介于 4 到 16 个字符之间）。|是|是|
|**屏幕锁定前的最大非活动分钟数**|指定设备自动锁定之前处于非活动状态的分钟数。|是|是|
|**擦除设备前的登录失败次数**|指定在擦除设备前允许的登录失败次数。|是|是|
|**密码过期（天数）**|指定必须更改设备密码前的天数。|是|是|
|**所需的密码类型**|指定所需的密码复杂性级别以及是否可以使用生物识别设备。 选择：<br><br>    -     **设备默认值**<br>-     **低安全性生物识别**<br>    -     **至少为数字**<br>    -     **数字复杂度**（不允许重复或连续数字，如“1111”或“1234”）<sup>1</sup><br>    -     **至少为字母**<br>    -     **至少包含字母数字**<br>    -     **至少为字母数字与符号**|是|是|
|**防止重用以前的密码**|阻止最终用户创建以前使用过的密码。|是|是|
|**指纹解锁**|允许使用指纹解锁支持的设备。|否|是|
|**Smart Lock 和其他信任代理**|允许在兼容的 Android 设备上控制 Smart Lock 功能（Samsung KNOX Standard 5.0 及更高版本）。 如果设备处于可信位置（例如当它连接到特定蓝牙设备时，或者在 NFC 标记附近时），则此手机功能（有时称为信任代理）使你可以禁用或绕过设备锁屏界面密码。可以使用此设置防止用户配置 Smart Lock。|是（5.0 及更高版本）|否|
|**加密**|要求对设备上的文件进行加密。|是|是|

<sup>1</sup>向设备分配此设置时，请确保目标设备上的公司门户应用已更新至最新版本。

如果配置**数值复杂度**设置，然后将其分配到运行 5.0 之前的 Android 版本的设备，则适用以下行为。
- 如果公司门户应用正在运行 1704 以前的版本，则不会向设备应用任何 PIN 策略，并将在 Intune 门户中显示错误。
- 如果公司门户应用已更新至 1704 版本，则将仅应用简单的 PIN。 5.0 以前的 Android 版本不支持此设置。 在 Intune 门户中未显示错误。


## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**Google Play 商店**|允许用户访问设备上的 Google Play 商店|否|是|

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以配置以下列表之一：

**禁止的应用**列表 - 列出用户不得安装和运行的应用（未由 Intune 托管）。
**批准的应用**列表 - 列出允许用户安装的应用。 为了保持相容状态，用户不得安装未列出的应用。 自动允许由 Intune 托管的应用。
必须将包含受限制的应用设置的设备配置文件部署到用户组。

若要配置列表，请单击“添加”，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在相容应用和不相容应用列表中指定应用 URL，请执行以下步骤：

在 [Google Play 的应用部分](https://play.google.com/store/apps)中，搜索你想要使用的应用。

打开应用的安装页面，然后将 URL 复制到剪贴板。 你现在可以在符合或不符合要求的应用列表中使用这个 URL。

示例：搜索适用于 Microsoft Office Mobile 的 Google Play。 你使用的 URL 将为 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

### <a name="additional-options"></a>其他选项

还可以单击“导入”，填充 csv 文件中的列表（格式为 <*应用 URL*>,<*应用名称*>,<*应用发布者*>），或单击“导出”，创建包含受限制应用列表内容且格式相同的 csv 文件。        

## <a name="browser"></a>浏览器
|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**Web 浏览器**|指定是否可以使用设备的默认 Web 浏览器。|否|是|
|**自动填充**|允许使用 Web 浏览器的自动填充功能。|否|是|
|**Cookie**|允许设备 Web 浏览器使用 Cookie。|否|是|
|**Javascript**|允许设备 Web 浏览器运行 Java 脚本。|否|是|
|**弹出窗口**|允许使用 Web 浏览器中的弹出窗口阻止程序。|否|是|

## <a name="cloud-and-storage"></a>云和存储
|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**Google 备份**|允许使用 Google 备份。|否|是|
|**Google 帐户自动同步**|允许 Google 帐户设置自动同步。|否|是|
|**可移动存储**|允许设备使用可移动存储，如 SD 卡。|否|是|
|**对存储卡进行加密**|指定是否必须对设备存储卡进行加密。|否|是|

## <a name="cellular-and-connectivity"></a>手机网络和连接性
|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**数据漫游**|当设备处于移动电话网络中时允许数据漫游）。|否|是|
|**SMS/MMS 消息传送**|允许在设备上使用短信和彩信消息传送。|否|是|
|**语音拨号**|启用或禁用设备上的语音拨号功能。|否|是|
|**语音漫游**|当设备处于移动电话网络中时允许语音漫游。|否|是|
|**蓝牙**|允许在设备上使用蓝牙。|否|是|
|**NFC**|允许使用近场通信（如果设备支持）的操作。|否|是|
|**Wi-Fi**|允许使用设备的 Wi-Fi 功能。|否|是|
|**Wi-Fi Tethering**|允许在设备上使用 Wi-Fi Tethering。|否|是|

## <a name="kiosk"></a>Kiosk
|||||
|-|-|-|-|
|设置名|详细信息|Android 4.0+|Samsung KNOX 标准版|
|**选择托管应用**|进行浏览，然后选择当设备处于展台模式时可以运行的托管应用（目前尚不支持指定为指向应用商店的链接的应用）。 不允许在设备上运行其他应用。|否|是|
|**屏幕睡眠按钮**|启用或禁用设备上的屏幕睡眠唤醒按钮。|否|是|
|**音量按钮**|启用或禁用设备上的音量按钮。|否|是|

