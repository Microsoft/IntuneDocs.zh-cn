---
title: "适用于 Android 的 Intune 设备限制设置"
titlesuffix: Azure portal
description: "了解可用来控制 Android 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97e125d768ca7b0cf58a2892d78675dfa42ef7ce
ms.sourcegitcommit: fa0f0402dfd25ec56a0df08c23708c7e2ad41120
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android 和 Samsung KNOX 标准版设备限制设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用这些具有 Android 设备限制策略的设置配置组织中的设备。

>[!TIP]
>如果所需设置不可用，可能能够使用[自定义配置文件](custom-settings-android.md)来配置设备。 

## <a name="general"></a>常规

- **相机** - 允许使用设备相机。
- 复制和粘贴（仅限 Samsung KNOX）- 允许使用设备上的复制和粘贴功能。
- 应用之间共享剪贴板（仅限 Samsung KNOX）- 允许使用剪贴板在应用之间进行复制和粘贴。
- 诊断数据提交（仅限 Samsung KNOX）- 阻止用户从设备提交诊断数据。
- 恢复出厂设置（仅限 Samsung KNOX）- 允许用户对设备执行恢复出厂设置。
- 地理位置（仅限 Samsung KNOX）- 允许设备利用位置信息）。
- 关闭电源（仅限 Samsung KNOX）- 允许用户关闭设备电源。<br>如果禁用，则无法设置**擦除设备前的登录失败次数**。
- 捕获屏幕（仅限 Samsung KNOX）- 让用户以图像形式捕获屏幕内容。
- 语音助手（仅限 Samsung KNOX）- 允许在设备上使用语音助手软件。
- YouTube（仅限 Samsung KNOX）- 允许在设备上使用 YouTube 应用。
- 共享设备（仅限 Samsung KNOX）- 将托管的 Samsung KNOX 标准设备配置为共享。 在此模式下，最终用户可以使用其 Azure AD 凭据登录和注销设备。 该设备仍然受管，无论是否正在使用。<br>与 SCEP 证书配置文件一起使用时，此功能允许最终用户与所有用户共享具有相同应用集的设备，但使用其自己的 SCEP 用户证书。用户注销时，会清除所有应用数据。  此功能仅限于 LOB 应用。

## <a name="password"></a>Password

- 密码 - 需要最终用户输入密码才能访问设备。|Yes|Yes|
- **最短密码长度** - 输入用户必须配置的最短密码长度（介于 4 到 16 个字符之间）。
- **屏幕锁定前的最大非活动分钟数** - 指定设备自动锁定之前，必须处于空闲状态的分钟数。
- **擦除设备前登录失败的次数** - 指定在擦除设备前允许的登录失败次数。
- **密码过期(天)** - 指定必须更改设备密码前的天数。
-  所需的密码类型 - 指定所需的密码复杂性级别以及是否可以使用生物识别设备。 选择：
    - **设备默认值**
    - **低安全性生物识别**
    - **至少为数字**
    - 数字复杂度 - 不允许重复或连续数字，如“1111”或“1234”<sup>1</sup>
    - **至少为字母**
    - **至少包含字母数字**
    - **至少为字母数字与符号**
- **防止重用以前的密码** - 阻止最终用户创建以前使用过的密码。
- 指纹解锁（仅限 Samsung KNOX） - 允许使用指纹解锁支持的设备。
- **Smart Lock 和其他信任代理** - 允许在兼容的 Android 设备上控制 Smart Lock 功能（Samsung KNOX Standard 5.0 及更高版本）。 如果设备处于可信位置，则使用此手机功能（有时称为“信任代理”）可禁用或绕过设备锁屏界面密码。 例如，这可以在设备连接到特定蓝牙设备或靠近 NFC 标签时使用。 可以使用此设置防止用户配置 Smart Lock。
- **加密** - 要求对设备上的文件进行加密。

<sup>1</sup> 向设备分配此设置之前，请确保将这些设备上的公司门户更新至最新版本。

如果配置**数值复杂度**设置，然后将其分配到运行 5.0 之前的 Android 版本的设备，则适用以下行为。
- 如果公司门户应用运行的版本低于 1704，则不会向设备应用任何 PIN 策略，并且 Azure 门户中会显示错误。
- 如果公司门户应用运行 1704 版本或更高版本，则只能应用简单的 PIN。 5.0 以前的 Android 版本不支持此设置。 Azure 门户中没有显示错误。


## <a name="google-play-store"></a>Google Play Store

- Google Play 商店（仅限 Samsung KNOX）- 允许用户在设备上访问 Google Play 商店。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，你可以配置以下适用于 Android 和 Samsung KNOX 标准版设备的列表之一：

**禁止的应用**列表 - 列出如果用户安装和运行，就会被报告的应用（未受 Intune 管理）。
**批准的应用**列表 - 列出允许用户安装的应用。 为了保持兼容性，用户不得安装其他应用。 自动允许由 Intune 托管的应用。
必须将包含受限制的应用设置的设备配置文件分配到用户组。

若要配置列表，请单击“添加”，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在相容应用和不相容应用列表中指定应用 URL，请执行以下步骤：

在 [Google Play 的应用部分](https://play.google.com/store/apps)中，搜索你想要使用的应用。

打开应用的安装页面，然后将 URL 复制到剪贴板。 你现在可以在符合或不符合要求的应用列表中使用这个 URL。

示例：搜索适用于 Microsoft Office Mobile 的 Google Play。 使用 URL：**https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**。

### <a name="additional-options"></a>其他选项

你也可以单击**导入**，从 csv 文件中获取列表。 使用格式 <*应用 URL**应用名称*>, <*应用发布者*>，或单击“导出”，导出包含受限制应用列表内容且格式相同的 csv 文件。      

## <a name="browser"></a>浏览器

- Web 浏览器（仅限 Samsung KNOX）- 指定是否可以使用设备的默认 Web 浏览器。
- 自动填充（仅限 Samsung KNOX）- 允许使用 Web 浏览器的自动填充功能。
- Cookie（仅限 Samsung KNOX）- 允许设备 Web 浏览器使用 cookie。
- Javascript（仅限 Samsung KNOX）- 允许设备 Web 浏览器运行 Java 脚本。
- 弹出窗口（仅限 Samsung KNOX）- 允许使用 Web 浏览器中的弹出窗口阻止程序。

## <a name="allow-or-block-apps"></a>允许或禁止应用

这些设置可用于指定能够在仅运行 Samsung KNOX Standard 的设备上安装或启动的应用。
此外，还可以指定设备用户看不到的已安装应用。 用户无法运行这些应用。

- **可以安装的应用（仅限 Samsung KNOX Standard）**
- **禁止启动的应用（仅限 Samsung KNOX Standard）**
- **用户看不到的应用（仅限 Samsung KNOX Standard）**

对于每个设置，使用下列项之一配置应用列表：

- **按包名称添加应用** - 主要用于业务线应用。 输入应用和应用包的名称。 
- **按 URL 添加应用** - 输入应用的名称及其在 Google Play 商店中的 URL。
- **添加受管理应用** - 从 Intune 管理的应用列表中，选择所需的应用。

## <a name="cloud-and-storage"></a>云和存储

- Google 备份（仅限 Samsung KNOX）- 允许使用 Google 备份。
- Google 帐户自动同步（仅限 Samsung KNOX）- 允许将 Google 帐户设置为自动同步。
- 可移动存储（仅限 Samsung KNOX）- 允许设备使用可移动存储，如 SD 卡。
- 存储卡加密（仅限 Samsung KNOX）- 指定是否必须对设备存储卡进行加密。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- 数据漫游（仅限 Samsung KNOX）- 当设备在移动电话网络中时允许数据漫游。
- SMS/MMS 消息（仅限 Samsung KNOX）- 允许在设备上使用 SMS 和 MMS 消息。
- 语音拨号（仅限 Samsung KNOX）- 启用或禁用设备上的语音拨号功能。
- 语音漫游（仅限 Samsung KNOX）- 当设备在移动电话网络中时允许语音漫游。
- 蓝牙（仅限 Samsung KNOX）- 允许在设备上使用蓝牙。
- NFC（仅限 Samsung KNOX）- 允许在支持的设备上使用近场通信的操作。
- Wi-Fi（仅限 Samsung KNOX）- 允许在设备上使用 Wi-Fi 功能。
- Wi-Fi Tethering（仅限 Samsung KNOX）- 允许在设备上使用 Wi-Fi Tethering。

## <a name="kiosk"></a>Kiosk

展台设置仅适用于 Samsung KNOX Standard 设备和 Intune 管理的应用。

- **选择受管理应用** - 选择以下选项之一，添加一个或多个可以在设备处于展台模式时运行的受管理应用。 不允许在设备上运行其他应用。
    - 按包名称添加应用
    - 按 URL 添加应用
    - 添加托管应用。
- **屏幕睡眠按钮** - 启用或禁用设备上的屏幕睡眠唤醒按钮。
- **音量按钮** - 启用或禁用设备上的音量按钮。


## <a name="next-steps"></a>后续步骤

继续使用[如何配置设备限制设置](device-restrictions-configure.md)中的说明，创建设备限制配置文件，然后进行分配。
