---
title: "适用于 Android 的 Intune 设备限制设置 |Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可用来控制 Android 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: a003b2b16e05c2d071bb7dbaaf564e24d0cf5823
ms.lasthandoff: 02/16/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 和 Samsung KNOX 标准版设备限制设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>常规
-     **相机** - 允许使用设备相机。
-     **复制和粘贴** - 允许使用设备上的复制和粘贴功能。
-     **应用之间共享剪贴板** - 允许使用剪贴板在应用之间进行复制和粘贴（仅限 Samsung KNOX 标准版）。
-     **诊断数据提交** - 阻止用户从设备提交诊断数据。    
-     **恢复出厂设置** - 允许用户对设备执行恢复出厂设置。
-     **地理位置** - 允许设备利用位置信息（仅限 Samsung KNOX 标准版）。
-     **关闭电源** - 允许用户关闭设备电源。<br>如果禁用此设置，则对于 Samsung KNOX 标准版设备，“擦除设备前登录失败的次数”设置无效。
-     **捕获屏幕** - 让用户以图像形式捕获屏幕内容。
-     **语音助手** - 允许在设备上使用语音助手软件（仅限 Samsung KNOX 标准版）。
-     **YouTube** - 允许在设备上使用 YouTube 应用（仅限 Samsung KNOX 标准版）。

## <a name="password"></a>Password
-     **需要密码** - 需要最终用户输入密码才能访问设备。
-     **最短密码长度** - 输入用户必须配置的最短密码长度（介于 4 到 16 个字符之间）。
-     **屏幕锁定前的最大非活动分钟数** - 指定设备自动锁定之前，必须处于空闲状态的分钟数。
-     **擦除设备前登录失败的次数** - 指定在擦除设备前允许的登录失败次数。
-     **密码过期(天)** - 指定必须更改设备密码前的天数。
-     **需要的密码类型** - 指定所需的密码复杂性级别以及是否可以使用生物识别设备。
-     **防止重用以前的密码** - 阻止最终用户创建以前使用过的密码。
-     **指纹解锁** - 允许使用指纹解锁支持的设备。
-     **Smart Lock 和其他信任代理** - 允许在兼容的 Android 设备上控制 Smart Lock 功能（Samsung KNOX Standard 5.0 及更高版本）。 如果设备处于可信位置（例如当它连接到特定蓝牙设备时，或者在 NFC 标记附近时），则此手机功能（有时称为信任代理）使你可以禁用或绕过设备锁屏界面密码。可以使用此设置防止用户配置 Smart Lock。
-     **加密** - 要求对设备上的文件进行加密。

## <a name="google-play-store"></a>Google Play Store

-     **Google Play store** - 允许用户在设备上访问 Google Play store（仅限 Samsung KNOX 标准版）。

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
-     **Web 浏览器** - 指定是否可以使用设备的默认 Web 浏览器。
-     **自动填充** - 允许使用 Web 浏览器的自动填充功能。
-     **Cookie** - 允许设备 Web 浏览器使用 Cookie。
-     **Javascript** -允许设备 Web 浏览器运行 Java 脚本。
-     **弹出窗口** - 允许使用 Web 浏览器中的弹出窗口阻止程序。

## <a name="cloud-and-storage"></a>云和存储
-     **Google 备份** - 允许使用 Google 备份。
-     **Google 帐户自动同步** - 允许将 Google 帐户设置为自动同步。
-     **可移动存储** - 允许设备使用可移动存储，如 SD 卡（仅限 Samsung KNOX 标准版）。
-     **存储卡加密** - 指定是否必须对设备存储卡进行加密。

## <a name="cellular-and-connectivity"></a>手机网络和连接性
-     **数据漫游** - 当设备在移动电话网络中时允许数据漫游（仅限 Samsung KNOX 标准版）。
-     **SMS/MMS 消息** - 允许在设备上使用 SMS 和 MMS 消息（仅限 Samsung KNOX 标准版）。
-     **语音拨号** - 启用或禁用设备上的语音拨号功能（仅限 Samsung KNOX 标准版）。
-     **语音漫游** - 当设备在移动电话网络中时允许语音漫游（仅限 Samsung KNOX 标准版）。
-     **蓝牙** - 允许在设备上使用蓝牙（仅限 Samsung KNOX 标准版）。
-     **NFC** - 允许使用近场通信（如果设备支持）的操作（仅限 Samsung KNOX 标准版）。
-     **Wi-Fi** - 允许在设备上使用 Wi-Fi 功能（仅限 Samsung KNOX 标准版）。
-     **Wi-Fi Tethering** - 允许在设备上使用 Wi-Fi Tethering（仅限 Samsung KNOX 标准版）。

## <a name="kiosk"></a>Kiosk
-     **选择托管应用** - 进行浏览，然后选择当设备处于展台模式时可以运行的托管应用（目前尚不支持指定为指向应用商店的链接的应用）。 不允许在设备上运行其他应用。
-     **屏幕睡眠按钮** - 启用或禁用设备上的屏幕睡眠唤醒按钮。
-     **音量按钮** - 启用或禁用设备上的音量按钮。

