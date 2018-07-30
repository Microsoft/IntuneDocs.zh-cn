---
title: 适用于 Android 的 Microsoft Intune 设备限制设置
titlesuffix: ''
description: 了解可用来控制运行 Android 的设备上的设备设置和功能的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 100742b378b30eab84b28c01728b2b382dd5155c
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190650"
---
# <a name="microsoft-intune-android-and-samsung-knox-standard-device-restriction-settings"></a>Microsoft Intune Android 和 Samsung Knox Standard 设备限制设置 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可为运行 Android 的设备配置的所有 Microsoft Intune 设备限制设置。

>[!TIP]
>如果所需设置不可用，可能能够使用[自定义配置文件](custom-settings-android.md)来配置设备。

## <a name="general"></a>常规

- **相机** - 允许使用设备相机。
- **复制和粘贴(仅限 Samsung Knox)** - 允许对设备使用复制和粘贴功能。
- **应用间的剪贴板共享(仅限 Samsung Knox)** - 允许使用剪贴板在应用之间进行复制和粘贴。
- **诊断数据提交(仅限 Samsung Knox)** - 阻止用户从设备提交诊断数据。
- **恢复出厂设置(仅限 Samsung Knox)** - 允许用户对设备恢复出厂设置。
- **地理位置(仅限 Samsung Knox)** - 允许设备利用位置信息。
- **切断电源(仅限 Samsung Knox)** - 允许用户切断设备电源。<br>如果禁用，则无法设置**擦除设备前的登录失败次数**。
- **屏幕截图(仅限 Samsung Knox)** - 允许用户以图像形式捕获屏幕内容。
- **语音助手(仅限 Samsung Knox)** - 允许对设备使用语音助手软件。
- **YouTube (仅限 Samsung Knox)** - 允许对设备使用 YouTube 应用。
- **共享设备(仅限 Samsung Knox)** - 将托管 Samsung Knox Standard 设备配置为共享设备。 在此模式下，最终用户可以使用其 Azure AD 凭据登录和注销设备。 该设备仍然受管，无论是否正在使用。<br>与 SCEP 证书配置文件一起使用时，此功能允许最终用户与所有用户共享具有相同应用集的设备，但使用其自己的 SCEP 用户证书。用户注销时，会清除所有应用数据。  此功能仅限于 LOB 应用。
- **禁止更改日期和时间 (Samsung Knox)** - 阻止用户对设备更改日期和时间设置。 

## <a name="password"></a>密码

- 密码 - 需要最终用户输入密码才能访问设备。|Yes|Yes|

    > [!NOTE]
    > 在 MDM 注册期间，Samsung Knox 设备自动要求使用 4 位数的 PIN。 本机 Android 设备可能会自动要求 PIN 符合条件访问。

- **最短密码长度** - 输入用户必须配置的最短密码长度（介于 4 到 16 个字符之间）。
- **屏幕锁定前的最大非活动分钟数** - 指定设备自动锁定之前，必须处于空闲状态的分钟数。
- **擦除设备前登录失败的次数** - 指定在擦除设备前允许的登录失败次数。
- **密码过期(天)** - 指定必须更改设备密码前的天数。
-  所需的密码类型 - 指定所需的密码复杂性级别以及是否可以使用生物识别设备。 选择：
    - 设备默认值
    - **低安全性生物识别**
    - **至少为数字**
    - **数字复杂度** - 不允许使用重复或连续数字（例如，“1111”或“1234”）。<sup>1</sup>
    - **至少为字母**
    - **至少包含字母数字**
    - **至少为字母数字与符号**
- **防止重用以前的密码** - 阻止最终用户创建以前使用过的密码。
- **指纹解锁(仅限 Samsung Knox)** - 允许使用指纹解锁受支持的设备。
- **Smart Lock 和其他信任代理** - 允许对兼容的 Android 设备（Samsung Knox Standard 5.0 及更高版本）控制 Smart Lock 功能。 如果设备处于可信位置，则使用此手机功能（有时称为“信任代理”）可禁用或绕过设备锁屏界面密码。 例如，这可以在设备连接到特定蓝牙设备或靠近 NFC 标签时使用。 可以使用此设置防止用户配置 Smart Lock。
- **加密** - 要求对设备上的文件进行加密。

    > [!NOTE]
    > 如果强制执行了加密策略，则 Samsung Knox 设备要求用户设置六个字符的复杂密码作为设备密码。

<sup>1</sup> 向设备分配此设置之前，请确保将这些设备上的公司门户更新至最新版本。

如果配置**数值复杂度**设置，然后将其分配到运行 5.0 之前的 Android 版本的设备，则适用以下行为。
- 如果公司门户应用运行的版本低于 1704，则不会向设备应用任何 PIN 策略，并且 Azure 门户中会显示错误。
- 如果公司门户应用运行 1704 版本或更高版本，则只能应用简单的 PIN。 5.0 以前的 Android 版本不支持此设置。 Azure 门户中没有显示错误。


## <a name="google-play-store"></a>Google Play Store

- **Google Play 商店(仅限 Samsung Knox)** - 允许用户在设备上访问 Google Play 商店。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以为 Android 和 Samsung Knox Standard 设备配置下面的列表之一：

**禁止的应用**列表 - 列出如果用户安装和运行就会被报告的应用（未受 Intune 托管）。
**批准的应用**列表 - 列出允许用户安装的应用。 为了保持兼容性，用户不得安装其他应用。 自动允许由 Intune 托管的应用。
必须将包含受限制的应用设置的设备配置文件分配到用户组。

若要配置列表，请单击“添加”，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在相容应用和不相容应用列表中指定应用 URL，请执行以下步骤：

在 [Google Play 的应用部分](https://play.google.com/store/apps)中，搜索你想要使用的应用。

打开应用的安装页面，然后将 URL 复制到剪贴板。 你现在可以在符合或不符合要求的应用列表中使用这个 URL。

示例：在 [Google Play 的“应用”部分](https://play.google.com/store/apps)搜索“Microsoft Planner”。 使用以下 URL：https://play.google.com/store/apps/details?id=com.microsoft.planner。

### <a name="additional-options"></a>其他选项

你也可以单击**导入**，从 csv 文件中获取列表。 使用格式 <*应用 URL* *应用名称*>, <*应用发布者*>，或单击“导出”，导出包含受限制应用列表内容且格式相同的 csv 文件。      

## <a name="browser"></a>浏览器

- **Web 浏览器(仅限 Samsung Knox)** - 指定能否使用设备的默认 Web 浏览器。
- **自动填充(仅限 Samsung Knox)** - 允许使用 Web 浏览器的自动填充功能。
- **Cookie (仅限 Samsung Knox)** - 允许设备 Web 浏览器使用 Cookie。
- **Javascript (仅限 Samsung Knox)** - 允许设备 Web 浏览器运行 Java 脚本。
- **弹出窗口(仅限 Samsung Knox)** - 允许在 Web 浏览器中使用弹出窗口阻止程序。

## <a name="allow-or-block-apps"></a>允许或禁止应用

这些设置可用于指定能够在仅运行 Samsung Knox Standard 的设备上安装或启动的应用。
此外，还可以指定对设备用户隐藏的已安装应用。 用户无法运行这些应用。

- **允许安装的应用(仅限 Samsung Knox Standard)**
- **禁止启动的应用(仅限 Samsung Knox Standard)**
- **对用户隐藏的应用(仅限 Samsung Knox Standard)**

对于每个设置，使用下列项之一配置应用列表：

- **按包名称添加应用** - 主要用于业务线应用。 输入应用和应用包的名称。
- **按 URL 添加应用** - 输入应用的名称及其在 Google Play 商店中的 URL。
- **添加受管理应用** - 从 Intune 管理的应用列表中，选择所需的应用。

## <a name="cloud-and-storage"></a>云和存储

- **Google 备份(仅限 Samsung Knox)** - 允许使用 Google 备份。
- **Google 帐户自动同步(仅限 Samsung Knox)** - 允许自动同步 Google 帐户设置。
- **可移动存储(仅限 Samsung Knox)** - 允许设备使用可移动存储，如 SD 卡。
- **存储卡加密(仅限 Samsung Knox)** - 指定是否必须对设备存储卡进行加密。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- **数据漫游(仅限 Samsung Knox)** - 当设备在移动电话网络中时，允许数据漫游。
- **短信/彩信(仅限 Samsung Knox)** - 允许对设备使用短信和彩信。
- **语音拨号(仅限 Samsung Knox)** - 对设备启用或禁用语音拨号功能。
- **语音漫游(仅限 Samsung Knox)** - 当设备在移动电话网络中时，允许语音漫游。
- **蓝牙(仅限 Samsung Knox)** - 允许对设备使用蓝牙。
- **NFC (仅限 Samsung Knox)** - 允许对受支持的设备使用近场通信。
- **Wi-Fi (仅限 Samsung Knox)** - 允许对设备使用 Wi-Fi 功能。
- **Wi-Fi 网络共享连接(仅限 Samsung Knox)** - 允许对设备使用 Wi-Fi 网络共享连接。

## <a name="kiosk"></a>Kiosk

展台设置仅适用于 Samsung Knox Standard 设备和使用 Intune 管理的应用。

- **选择受管理应用** - 选择以下选项之一，添加一个或多个可以在设备处于展台模式时运行的受管理应用。 不允许在设备上运行其他应用。 预安装的浏览器不能定义为在设备处于展台模式下也允许运行的应用。 如果需要浏览器，请考虑使用 [Managed Browser](app-configuration-managed-browser.md)。
    - 按包名称添加应用
    - 按 URL 添加应用
    - 添加托管应用。
- **屏幕睡眠按钮** - 启用或禁用设备上的屏幕睡眠唤醒按钮。
- **音量按钮** - 启用或禁用设备上的音量按钮。


## <a name="next-steps"></a>后续步骤

继续使用[如何配置设备限制设置](device-restrictions-configure.md)中的说明，创建设备限制配置文件，然后进行分配。
