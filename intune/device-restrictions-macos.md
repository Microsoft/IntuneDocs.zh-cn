---
title: Microsoft Intune 中的 macOS 设备设置 - Azure | Microsoft Docs
titlesuffix: ''
description: 添加、配置或创建 macOS 设备上的设置可限制设置密码要求等功能、控制锁屏、使用内置应用、添加限制使用或批准使用的应用、处理蓝牙设备、连接到云进行备份和存储、启用展台模式、添加域以及控制用户如何与 Microsoft Intune 中的 Safari Web 浏览器交互。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4fa6a68d1b5a8d2ccf87587ecab36c7807770d48
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565343"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>便于使用 Intune 允许或限制功能的 macOS 设备设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出并介绍了可以在 macOS 设备上控制的各种设置。 在移动设备管理 (MDM) 解决方案中，请通过这些设置允许使用或禁用功能、设置密码规则、允许使用或限制使用特定应用等。

我们将这些设置添加到 Intune 中的设备配置配置文件中，然后分配或部署到 macOS 设备。

## <a name="before-you-begin"></a>在开始之前

[创建设备限制配置文件](device-restrictions-configure.md#create-the-profile)。

## <a name="general"></a>常规

- **阻止定义查找**：“阻止”可阻止用户突出显示某个字词，然后在设备上查找其定义。 “未配置”（默认）允许访问定义查找功能。
- **阻止听写**：“阻止”可阻止用户通过语音输入输入文本。 “未配置”（默认）允许用户使用听写输入。
- **阻止内容缓存**： 选择**未配置**（默认值） 以启用内容缓存。 缓存存储应用数据、 web 浏览器数据、 下载和更多本地设备上的内容。 选择**块**来防止此数据存储在缓存中。

  在 macOS 上的内容缓存的详细信息，请参阅[管理 Mac 上的内容缓存](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac)（将打开另一个网站）。

  此功能适用于：  
  - macOS 10.13 及更高版本

- **延迟 （仅限监管模式） 的软件更新**： 当设置为**未配置**（默认值），软件更新显示在设备上为 Apple 释放它们。 例如，如果 macOS 更新在特定日期中获取由 Apple 发布的然后该更新很自然地显示发布日期围绕在设备上。

  **启用**允许延迟时软件更新显示在设备上，从 0-90 天。 此设置不会控制何时更新或未安装。 

  - **延迟软件更新的可见性**： 输入一个介于 0-90 天。 延迟到期时，用户会收到通知，通知更新到触发延迟时可用的最早版本的操作系统。

    例如，如果 macOS update 上可用**1 月 1 日**，并**延迟可见性**设置为**5 天**，然后更新未显示为设备上可用的更新。 上**第六个天**以下版本中，更新可用，且最终用户可以安装它。

    此功能适用于：  
    - macOS 10.13.4 及更高版本

## <a name="password"></a>密码

- **密码**：选择“必需”，最终用户输入密码才能访问设备。 **未配置**（默认值） 不需要密码，而不会强制任何限制，例如阻止简单密码，或设置最小长度。
  - **所需密码类型**：指定密码是否可以仅由数值组成，还是必须为字母数字（包含字母和数字）。 仅在 Mac OS X 10.10.3 及更高版本上支持此设置。
  - **密码中的非字母数字字符数**：指定密码中必须包含的复杂字符数（0 至 4）。<br>复杂字符是一个符号，例如“?”。
  - **最短密码长度**：输入用户必须配置的最短密码长度（介于 4 到 16 个字符之间）。
  - **简单密码**：允许使用简单密码，如 0000 或 1234。
  - **要求提供密码前，屏幕锁定后的最大分钟数**：指定在需要密码来进行解锁之前，计算机必须保持非活动状态的时间。
  - **屏幕锁定前的最大非活动状态分钟数**：指定锁定屏幕前，计算机必须处于空闲状态的时间长度。
  - **密码过期（天数）**：指定用户在多少天之后必须更改密码（1 到 255 天）。
  - **阻止重用以前的密码**：输入以前用过的不能重用的密码数，从 1 到 24。

- **阻止用户修改密码**： 选择**块**停止中添加或删除正在更改的密码。 “未配置”（默认）允许添加、更改或删除密码。
- **阻止指纹解锁**：选择“阻止”可阻止使用指纹解锁设备。 “未配置”（默认）允许用户使用指纹解锁设备。

- **阻止密码自动填充**：选择“阻止”可阻止在 macOS 上使用自动填充密码功能。 选择**块**还会产生以下影响：

  - 系统不会提示用户在 Safari 或任何应用中使用已保存的密码。
  - 自动强密码处于禁用状态，不建议用户使用强密码。

  “未配置”（默认）允许这些请求。

- **阻止密码接近度请求**：选择“阻止”，则用户的设备不会从附近的设备请求密码。 “未配置”（默认）允许这些密码请求。

- **阻止密码共享**：“阻止”可阻止使用 AirDrop 在设备之间共享密码。 “未配置”（默认）允许共享密码。

## <a name="built-in-apps"></a>内置应用

- **阻止 Safari 自动填充**：“阻止”可禁用设备上 Safari 中的自动填充功能。 “未配置”（默认）允许用户更改 Web 浏览器中的自动完成设置。
- **阻止照相机**：选择“阻止”可阻止访问设备上的照相机。 “未配置”（默认）允许访问设备的照相机。
- **阻止 Apple Music**：“阻止”可将音乐应用还原为经典模式并禁用音乐服务。 “未配置”（默认）允许使用 Apple Music 应用。
- **块突出 Internet 搜索结果**:**块**阻止聚焦从 Internet 搜索中返回任何结果。 “未配置”（默认）允许 Spotlight 搜索连接到 Internet 以提供搜索结果。
- **块文件传输使用 iTunes**:**块**禁用共享服务的应用程序文件。 可在 macOS 10.13 及更高版本。 **未配置**（默认值） 允许应用程序文件共享服务。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以配置以下列表之一：

- **禁止的应用**列表：列出用户不得安装和运行的应用（未由 Intune 托管）。 用户不会阻止安装已禁止的应用，但如果是这样，它将被报告为管理员。
- **批准的应用**列表：列出允许用户安装的应用。 用户不得安装未列出的应用。 自动允许由 Intune 托管的应用。 不会阻止用户安装的应用程序不在已批准列表上。 但是，如果是这样，它将被报告为管理员。

若要配置列表，请单击“添加”，然后指定你选择的名称、应用发布者（可选）和该应用的捆绑 ID（例如 *com.apple.calculator*）。

## <a name="connected-devices"></a>已连接的设备

- **阻止 AirDrop**：“阻止”可阻止在设备上使用 AirDrop。 “未配置”（默认）允许使用 AirDrop 功能与附近的设备交换内容。
- **块 Apple Watch 自动解锁**:**块**防止用户解锁其 Apple Watch 使用其 macOS 设备。 **未配置**（默认值） 允许用户解锁其 Apple Watch 使用 macOS 设备。

## <a name="cloud-and-storage"></a>云和存储

- **阻止 iCloud 密钥链同步**：选择“阻止”可禁止将密钥链中存储的凭据同步到 iCloud。 “未配置”（默认）允许用户同步这些凭据。
- **阻止 iCloud 文档同步**:**块**阻止 iCloud 文档和数据进行同步。 “未配置”（默认）允许将文档和键值同步到 iCloud 存储空间。
- **阻止 iCloud 邮件备份**:**块**阻止 iCloud 向 macOS 邮件应用程序进行同步。 **未配置**（默认值） 允许邮件同步到 iCloud。
- **阻止 iCloud 联系人备份**:**块**iCloud 可防止将设备联系人同步。 **未配置**（默认值） 允许使用 iCloud 的联系人同步。
- **阻止 iCloud 备份日历**:**块**阻止 iCloud 向 macOS 日历应用程序进行同步。 **未配置**（默认值） 允许日历同步到 iCloud。
- **阻止 iCloud 备份提醒**:**块**阻止 iCloud 同步到 macOS 提醒应用。 **未配置**（默认值） 允许提醒同步到 iCloud。
- **阻止 iCloud 书签备份**:**块**阻止 iCloud 同步设备的书签。 **未配置**（默认值） 允许书签同步到 iCloud。
- **阻止 iCloud 说明备份**:**块**阻止 iCloud 同步设备说明。 **未配置**（默认值） 允许说明同步到 iCloud。

## <a name="domains"></a>Domains

- **电子邮件域 URL**：向列表添加一个或多个 URL。 当用户从所配置的域以外的域接收电子邮件时，该电子邮件在 MacOS 邮件应用中被标记为不受信任。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

你也可以限制上的设备功能和设置[iOS](device-restrictions-ios.md)设备。