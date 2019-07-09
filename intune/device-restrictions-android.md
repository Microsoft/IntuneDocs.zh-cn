---
title: Microsoft Intune 中适用于 Android 的设备限制设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中查看可以控制和限制的所有 Android 设备设置的列表。 使用这些设置来控制密码、访问 Google Play、允许或禁止应用、控制浏览器设置、阻止应用、备份到 Google Cloud，以及控制邮件、声音、数据漫游、Wi-Fi 和蓝牙连接选项。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac25a0f3305cdfac9f3eeaa75b9e2106b3571b0
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572499"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Intune 中 Android 和 Samsung Knox Standard 设备限制设置列表

本文介绍可为运行 Android 的设备配置的所有 Microsoft Intune 设备限制设置。

>[!TIP]
>如果所需设置不可用，可能能够使用[自定义配置文件](custom-settings-android.md)来配置设备。

## <a name="general"></a>常规

- **照相机**：选择“阻止”  可阻止访问照相机。 “未配置”  则允许访问设备的照相机。
- **复制和粘贴(仅限 Samsung Knox)** ：选择“阻止”  可阻止复制和粘贴。 “未配置”  则允许使用设备上的复制和粘贴功能。
- **应用间的剪贴板共享(仅限 Samsung Knox)** ：选择“阻止”  可阻止使用剪贴板在应用之间进行复制和粘贴。 “未配置”  则允许使用剪贴板在应用之间进行复制和粘贴。
- **诊断数据提交(仅限 Samsung Knox)** ：选择“阻止”  可阻止用户从设备提交诊断数据。 “未配置”  则允许用户提交数据。
- **擦除(仅限 Samsung Knox)** ：允许用户在设备上运行[擦除](devices-wipe.md)操作。
- **地理位置(仅限 Samsung Knox)** ：选择“阻止”  可禁止设备使用位置信息。 “未配置”  则允许设备使用位置信息。
- **关闭电源(仅限 Samsung Knox)** ：选择“阻止”  可阻止用户关闭设备电源。 如果禁用此设置，则无法设置“擦除设备前的登录失败次数”  设置，并且也不会起作用。 “未配置”  则允许用户关闭设备电源。
- **屏幕捕获(仅限 Samsung Knox)** ：选择“阻止”  可阻止屏幕截图。 “未配置”  则允许用户将屏幕内容作为图像捕获。
- **语音助手(仅限 Samsung Knox)** ：选择“阻止”  可禁用 Samsung 语音服务。 “未配置”  则允许在设备上使用 Samsung 语音服务和应用。 此设置不适用于 Bixby 或用于朗读屏幕内容的辅助功能的语音助手。
- **YouTube (仅限 Samsung Knox)** ：选择“阻止”  可阻止用户使用 YouTube 应用。 “未配置”  则允许在设备上使用 YouTube 应用。
- **共享设备(仅限 Samsung Knox)** ：将托管 Samsung Knox Standard 设备配置为共享设备。 在设置为“允许”  后，最终用户可以使用其 Azure AD 凭据登录和注销设备。 该设备仍然处于托管状态，无论是否正在使用。</br>与 SCEP 证书配置文件一起使用时，此功能允许最终用户与所有用户共享具有相同应用的设备。 但每个用户都有其自己的 SCEP 用户证书。 用户注销时，会清除所有应用数据。 此功能仅限于 LOB 应用。 </br>“未配置”  则阻止多个最终用户在设备上使用其 Azure AD 凭据登录公司门户应用。
- **禁止更改日期和时间(Samsung Knox)** ：选择“阻止”  可阻止用户更改设备的日期和时间设置。 “未配置”  则允许用户更改日期和时间设置。

## <a name="password"></a>密码

- **密码**：选择“必需”  ，最终用户输入密码才能访问设备。 “未配置”  则允许用户无需输入密码即可访问设备。

    > [!NOTE]
    > 在 MDM 注册期间，Samsung Knox 设备自动要求使用 4 位数的 PIN。 本机 Android 设备可能会自动要求，必须有 PIN 才符合条件访问。

- **最短密码长度**：输入用户必须输入的最短密码长度（介于 4 到 16 个字符之间）。
- **屏幕锁定前的最大不活动分钟数**：输入在屏幕锁定前在设备上允许的最大不活动分钟数。 在设备上，最终用户设置的时间值不能大于在配置文件所配置的时间。 最终用户不能设置更低的时间值。 例如，如果配置文件设置为 15 分钟，则最终用户可将值设置为 5 分钟。 最终用户不得将值设置为 30 分钟。 
- **擦除设备前登录失败的次数**：输入在擦除设备前允许的登录失败次数。
- **密码过期(天数)** ：输入必须更改设备密码前的天数。
- **所需的密码类型**：输入所需的密码复杂性级别以及是否可以使用生物识别设备。 选项包括：
  - **设备默认值**
  - **低安全性生物识别**
  - **至少为数字**
  - **数字复杂度**：不允许使用重复或连续数字（例如，“1111”或“1234”）。<sup>1</sup>
  - **至少为字母**
  - **至少包含字母数字**
  - **至少为字母数字与符号**
- **防止重用以前的密码**：阻止最终用户创建以前使用过的密码。
- **指纹解锁(仅限 Samsung Knox)** ：选择“阻止”  可阻止使用指纹解锁设备。 “未配置”  则允许用户使用指纹解锁设备。
- **Smart Lock 和其他信任代理**：选择“阻止”  可阻止 Smart Lock 或其他信任代理调整锁定屏幕设置 (Samsung KNOX Standard 5.0+)。 此手机功能（有时称为“信任代理”）可以在设备处于可信任位置时禁用或绕过设备锁定屏幕密码。 例如，此功能可以在设备连接到特定蓝牙设备或靠近 NFC 标签时使用。 可以使用此设置防止用户配置 Smart Lock。
- **加密**：选择“必需”  ，以便对设备上的文件进行加密。 并非所有设备都支持加密。 要使用此功能，还需要执行以下操作： 
  1. 将“密码”  设置为“必需”  。
  2. 将“所需的密码类型”  设置为“至少为数字”  。
  3. 将“最短密码长度”  设置为 4 以正确报告此设置的符合性。

  > [!NOTE]
  > 如果强制执行了加密策略，则 Samsung Knox 设备要求用户设置六个字符的复杂密码作为设备密码。

<sup>1</sup> 向设备分配此设置之前，请确保将这些设备上的公司门户更新至最新版本。

如果将“所需的密码类型”设置  为“数字复杂度”  ，然后将其分配到运行 5.0 之前的 Android 版本的设备，则适用以下行为：

- 如果公司门户应用运行的版本低于 1704，则不会向设备应用任何 PIN 策略，并且 Azure 门户中会显示错误。
- 如果公司门户应用运行 1704 版本或更高版本，则只能应用简单的 PIN。 5\.0 以前的 Android 版本不支持此设置。 Azure 门户中不显示任何错误。

## <a name="google-play-store"></a>Google Play Store

- **Google Play 商店(仅限 Samsung Knox)** ：选择“阻止”  可阻止用户使用 Google Play 商店。 “未配置”  则允许用户访问设备上的 Google Play 商店。

## <a name="restricted-apps"></a>受限制的应用

使用这些设置可在设备上允许或阻止特定应用。 Android 和 Samsung Knox Standard 设备上支持此功能：

- **禁止的应用**：不想在设备上安装的不由 Intune 管理的应用列表。 如果用户安装此列表中的某个应用，Intune 会通知你。
- **批准的应用**：允许用户安装的应用列表。 为了保持兼容性，用户不得安装其他应用。 自动允许由 Intune 托管的应用。

若要将应用添加到这些列表，可以：

- 添加  想要应用的 Google Play 商店 URL。 例如，要添加适用于 Android 的 Microsoft 远程桌面应用，请输入 `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`。 若要查找应用的 URL，请打开 [Google Play 商店](https://play.google.com/store/apps)，并搜索该应用。 例如，搜索 `Microsoft Remote Desktop Play Store` 或 `Microsoft Planner`。 选择应用并复制 URL。
- 导入包含应用详细信息的 CSV 文件，包括 URL。 使用 <应用 url  >, <应用名称  >, <应用发行者  > 格式。 或，导出  包含相同格式的受限应用列表的现有列表。

> [!IMPORTANT]
> 必须将使用受限制的应用设置的设备配置文件分配到用户组。

## <a name="browser"></a>浏览器

- **Web 浏览器(仅限 Samsung Knox)** ：选择“阻止”  可阻止在设备上使用默认 Web 浏览器。 “未配置”  则允许使用设备的默认 Web 浏览器。
- **自动填充(仅限 Samsung Knox)** ：选择“阻止”  可阻止在浏览器中自动填充文本。 “未配置”  则允许使用 Web 浏览器的自动填充功能。
- **Cookie (仅限 Samsung Knox)** ：选择希望如何在设备上处理网站的 cookie。 选项包括：
  - Allow
  - 阻止所有 cookie
  - 允许访问的网站的 cookie
  - 允许当前网站的 cookie
- **Javascript (仅限 Samsung Knox)** ：选择“阻止”  可阻止 Web 浏览器运行 Java 脚本。 “未配置”  则允许设备 Web 浏览器运行 Java 脚本。
- **弹出窗口(仅限 Samsung Knox)** ：选择“阻止”  可阻止 Web 浏览器中的弹出窗口。 “未配置”  则允许 Web 浏览器中的弹出窗口。

## <a name="allow-or-block-apps"></a>允许或禁止应用

使用这些设置允许、阻止或隐藏在 Samsung Knox Standard 设备上运行特定应用。 用户无法打开或运行隐藏的应用。

选项包括：

- **允许安装的应用(仅限 Samsung Knox Standard)**
- **禁止启动的应用(仅限 Samsung Knox Standard)**
- **对用户隐藏的应用(仅限 Samsung Knox Standard)**

对于每个设置，添加应用列表。 选项包括：

- **按包名称添加应用**：主要用于业务线应用。 输入应用和应用包的名称。
- **按 URL 添加应用**：输入应用名称及其在 Google Play 商店中的 URL。
- **添加商店应用**：在 Intune 中管理的现有应用列表中选择一个应用。

## <a name="cloud-and-storage"></a>云和存储

- **Google 备份(仅限 Samsung Knox)** ：选择“阻止”  可阻止设备同步到 Google 备份。 “未配置”  则允许使用 Google 备份。
- **Google 帐户自动同步(仅限 Samsung Knox)** ：选择“阻止”  可在设备上阻止 Google 帐户自动功能。 “未配置”  则允许自动同步 Google 帐户设置。
- **可移动存储(仅限 Samsung Knox)** ：选择“阻止”  可阻止设备使用可移动存储。 “未配置”  则允许设备使用可移动存储，如 SD 卡。
- **存储卡加密(仅限 Samsung Knox)** ：选择“必需”  强制加密存储卡。 “未配置”  则允许使用未加密的存储卡。 并非所有设备都支持存储卡加密。 若要进行确认，请咨询设备制造商。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- **数据漫游(仅限 Samsung Knox)** ：选择“阻止”  可阻止通过移动电话网络进行数据漫游。 “未配置”  则允许设备在处于移动电话网络时进行数据漫游。
- **短信/彩信(仅限 Samsung Knox)** ：选择“阻止”  可阻止在设备上使用短信。 “未配置”  则允许在设备上使用短信和彩信消息传送。
- **语音拨号(仅限 Samsung Knox)** ：选择“阻止”  可阻止用户在设备上使用语音拨号功能。 “未配置”  则允许在设备上使用语音拨号。
- **语音漫游(仅限 Samsung Knox)** ：选择“阻止”  可阻止通过移动电话网络进行语音漫游。 “未配置”  则允许设备在处于移动电话网络时进行语音漫游。
- **蓝牙(仅限 Samsung Knox)** ：选择“阻止”  可阻止在设备上使用蓝牙。 “未配置”  则允许在设备上使用蓝牙。
- **NFC (仅限 Samsung Knox)** ：选择“阻止”  可阻止近场通信 (NFC) 技术。 “未配置”  则允许在支持的设备上使用近场通信的操作。
- **Wi-Fi (仅限 Samsung Knox)** ：选择“阻止”  可阻止在设备上使用 Wi-Fi。 “未配置”  则允许设备的 Wi-Fi 功能。
- **Wi-Fi Tethering (仅限 Samsung Knox)** ：选择“阻止”  可阻止在设备上使用 Wi-Fi Tethering。 “未配置”  则允许在设备上使用 Wi-Fi Tethering。

## <a name="kiosk"></a>Kiosk

展台设置仅适用于 Samsung Knox Standard 设备和使用 Intune 管理的应用。

- 添加要在设备处于展台模式时运行的应用。 在展台模式下，仅运行所添加的应用，未添加的应用不会运行。 当设备处于展台模式时，预安装的浏览器不会作为应用运行。 如果需要浏览器，请考虑使用 [Managed Browser](app-configuration-managed-browser.md)。

  应用选项：

  - **按包名称添加应用**：主要用于业务线应用。 输入应用和应用包的名称。
  - **按 URL 添加应用**：输入应用名称及其在 Google Play 商店中的 URL。
  - **添加商店应用**：在 Intune 中管理的现有应用列表中选择一个应用。

- **屏幕睡眠按钮**：选择“阻止”  可阻止或隐藏屏幕睡眠按钮。 “未配置”  则允许在设备上使用屏幕睡眠唤醒按钮。
- **音量按钮**：选择“阻止”  可阻止用户通过禁用音量按钮来调节音量。 “未配置”  则允许使用设备上音量按钮。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android 企业](device-restrictions-android-for-work.md#dedicated-device-settings)和 [Windows 10](kiosk-settings.md) 设备创建展台配置文件。
