---
title: 运行 Windows 8.1 的设备的 Microsoft Intune 设备限制设置
titleSuffix: ''
description: 了解可用于控制运行 Windows 8.1 的设备中设备设置和功能的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec832e6eb78df9b7ee977705e8b60c5ee2e898fa
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734773"
---
# <a name="microsoft-intune-windows-81-and-later-device-restriction-settings"></a>Microsoft Intune Windows 8.1 及更高版本设备限制设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文介绍可为运行 Windows 8.1 及更高版本的设备配置的 Microsoft Intune 设备限制设置。


## <a name="general"></a>常规

- **诊断数据提交** - 允许设备将诊断信息提交到 Microsoft。
- **防火墙** - 需要 Windows 防火墙处于打开状态。
- **用户帐户控制** - 需要在设备上使用用户帐户控制 (UAC)。

## <a name="password"></a>密码
- **所需密码类型** - 需要最终用户输入密码才能访问设备。
- **最短密码长度** - 配置密码所需的最小长度（以字符计算）。
- **擦除设备前的登录失败次数** - 如果登录尝试失败达到此次数，则擦除设备。
- **屏幕锁定前的最大非活动分钟数** - 指定需要密码以进行解锁之前，设备必须保持空闲的分钟数。
- **密码过期(天)** - 指定必须更改设备密码前的天数。
- **防止重用以前的密码** - 指定用户是否可以配置以前用过的密码。
- **图片密码和 PIN** - 允许使用图片密码和 PIN。 图片密码允许用户使用图片上的手势登录。 PIN 允许用户使用 4 位代码快速登录。
- **加密** - 要求对设备上的文件进行加密。<br>若要在运行 Windows 8.1 的设备上强制加密，必须在每台设备上安装 [用于 Windows 的 December 2014 MDM 客户端更新](https://support.microsoft.com/kb/3013816) 。
如果对 Windows 8.1 设备启用此设置，则该设备的所有用户必须都具有 Microsoft 帐户。
为了使加密有效，该设备必须满足 Microsoft [InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) 硬件认证要求。
在设备上强制加密时，恢复密钥仅可从用户的 Microsoft 帐户（从用户的 OneDrive 帐户访问）进行访问。 无法代表用户恢复此密钥。 



## <a name="browser"></a>浏览器
- **自动填充** - 允许用户更改浏览器中的自动完成设置。
- **欺诈警告** - 启用或禁用对潜在欺诈网站的警告。
- **SmartScreen** - 启用或禁用对潜在欺诈网站的警告。
- **JavaScript** - 允许浏览器运行脚本，如 Java 脚本。
- **弹出窗口** - 启用或禁用浏览器弹出窗口阻止程序。
- **发送 do-not-track 标头** - 将“do-not-track”标头发送到 Internet Explorer 中访问过的网站。
- **插件** - 允许用户向 Internet Explorer 添加插件。
- **在 Intranet 站点上使用单字条目** - 允许使用单字将 Internet Explorer 转到网站，如 Bing。
- **自动检测 Intranet 站点** - 帮助在 Internet Explorer 中配置 Intranet 站点的安全性。
- **Internet 安全级别** - 设置 Internet 站点的 Internet Explorer 安全级别。
- **Intranet 安全级别** - 设置 Intranet 站点的 Intranet Explorer 安全级别。
- **受信任站点的安全级别** - 配置受信任的站点区域的安全级别。
- **对受限站点实施高安全性** - 配置受限站点区域的安全级别。
- **企业模式菜单访问** - 允许用户从 Internet Explorer 访问企业模式菜单选项。
如果选择此设置，你还可以指定**日志记录报告位置**，其中包含指向一个报表的 URL，该报表显示了用户为其启用了企业模式访问的网站。
- **企业模式站点列表位置** – 指定活动状态下使用企业模式的网站列表的位置。

## <a name="cellular"></a>移动电话
- **数据漫游** - 当设备处于手机网络中时允许数据漫游。

## <a name="cloud-and-storage"></a>云和存储
- **工作文件夹 URL** - 设置工作文件夹的 URL，以允许跨设备同步文档。
- **不使用 Microsoft 帐户而访问 Windows Mail 应用** 允许在没有 Microsoft 帐户的情况下访问 Windows Mail 应用程序。
