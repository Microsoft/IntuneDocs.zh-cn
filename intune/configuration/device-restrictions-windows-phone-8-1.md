---
title: 适用于 Windows Phone 8.1 的 Microsoft Intune 设备限制设置
titleSuffix: ''
description: 了解可用于控制运行 Windows Phone 8.1 的设备中设备设置和功能的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc29a7a5026691371370b167a4445bfd70cc76bd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72489804"
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Microsoft Intune Windows Phone 8.1 设备限制设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文介绍可为运行 Windows Phone 8.1 的设备配置的 Microsoft Intune 设备限制设置。


## <a name="general"></a>常规

- **相机** - 允许或阻止设备的相机。
- **复制和粘贴** - 允许或阻止在设备上使用复制和粘贴功能。
- **可移动存储** - 允许设备使用可移动存储，如 SD 卡。
- **地理位置** - 允许设备利用位置信息。
- **Microsoft 帐户** - 允许或阻止用户将 Microsoft 帐户链接到设备。
- **屏幕捕获** - 让用户以图像文件形式捕获屏幕内容。
- **诊断数据提交** - 允许设备将诊断信息提交到 Microsoft。
- **自定义电子邮件帐户同步** - 允许设备连接到非 Microsoft 电子邮件帐户。

## <a name="password"></a>密码

- **密码** - 需要最终用户输入密码才能访问设备。
  - **所需的密码类型** - 指定需要的密码类型，例如仅限字母数字或数字。
  - **最短密码长度** - 指定密码中所需的最少字符数。
  - **简单密码** - 指定可使用如“0000”和“1234”之类的简单密码。
  - **擦除设备前登录失败的次数** - 指定在擦除设备前允许输入错误密码的次数。
  - **屏幕锁定前的最大非活动分钟数** - 指定屏幕自动锁定之前，设备必须处于空闲状态的时间。
  - **密码过期(天)** - 指定必须更改设备密码前的天数。
  - **防止重用以前的密码** - 指定需要记住多少个以前用过的密码。
- **加密** - 需要对支持的移动设备上的数据进行加密。

## <a name="app-store"></a>App Store

- **应用商店** - 允许用户从设备连接到应用商店。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以配置以下列表之一：

**阻止的应用**列表 - 列出用户不得安装和运行的应用（未由 Intune 托管）。
**允许的应用**列表 - 列出允许用户安装的应用。 自动允许由 Intune 托管的应用。

若要配置列表，请单击“添加”  ，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在允许和阻止的的应用列表中指定应用 URL，请使用以下格式：

在 [Windows Phone 应用商店](https://www.microsoft.com/store/apps/windows-phone)页面中，搜索想要使用的应用。

打开应用页面，并将该 URL 复制到剪贴板。 你现在可以在允许的或阻止的应用列表中将它用作 URL。

例如：在应用商店中搜索 Skype 应用。 要使用的 URL 为 `http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51`。



### <a name="additional-options"></a>其他选项

还可以单击“导入”  ，填充 csv 文件中的列表（格式为 <应用 URL  >,<应用名称  >,<应用发布者  >），或单击“导出”  ，创建包含受限制应用列表内容且格式相同的 csv 文件。


## <a name="browser"></a>浏览器

- **Web 浏览器** - 允许或阻止设备上的内置 Web 浏览器。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- **Wi-Fi** - 启用或禁用设备的 Wi-Fi 功能。
- **Wi-Fi Tethering** - 允许在设备上使用 Wi-Fi Tethering。
- **自动连接到 Wi-Fi 热点** - 允许设备自动连接到免费的 Wi-Fi 热点并自动接受任何使用条款。
- **Wi-Fi 热点报告** - 发送有关 Wi-Fi 连接的信息，以帮助用户发现附近的连接。
- **NFC** - 启用或禁用在支持近场通信的设备上使用近场通信的操作。
- **蓝牙** - 启用或禁用设备的蓝牙功能。
