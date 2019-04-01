---
title: Microsoft Intune 中的 Android Enterprise 电子邮件设置 - Azure | Microsoft Docs
description: 创建使用 Exchange 服务器并从 Azure Active Directory 检索属性的设备配置电子邮件配置文件。 在 Android 工作配置文件设备上，使用 Microsoft Intune 启用 SSL 或 SMIME、通过证书或用户名/密码对用户进行身份验证，以及同步电子邮件和日程安排。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b6c6c6e3e999e44ad6a07b4d8bdc1ddf9c400cf7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565445"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune 中用于配置电子邮件、身份验证和同步的 Android Enterprise 设备设置

本文列出并介绍了可以在 Android Enterprise 设备上控制的各种电子邮件设置。 在移动设备管理 (MDM) 解决方案中，使用这些设置可配置电子邮件服务器、使用 SSL 加密电子邮件等。

Intune 管理员可以为工作配置文件中的 Android Enterprise 设备创建并分配电子邮件设置。

若要详细了解 Intune 中的电子邮件配置文件，请参阅[配置电子邮件设置](email-settings-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](email-settings-configure.md#create-a-device-profile)，并选择工作配置文件。

## <a name="android-enterprise"></a>Android Enterprise

- **电子邮件应用**：选择“Gmail”或“Nine Work”
- **电子邮件服务器**：Exchange 服务器的主机名。 例如，输入 `outlook.office365.com`。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (Azure AD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：

  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **用户名**：仅获取名称，如 `user1`

- **来自 AAD 的电子邮件地址属性**： 此名称是从 Azure AD 获取 Intune 的电子邮件属性。 Intune 动态生成此配置文件使用的电子邮件地址。 选项包括：
  - **用户主体名称**：使用完整的主体名称（如 `user1@contoso.com` 或 `user1`）作为电子邮件地址。
  - **主 SMTP 地址**： 使用主 SMTP 地址，如`user1@contoso.com`，以登录到 Exchange。

- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **SSL**：选择“启用”可以在发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时使用安全套接字层 (SSL) 通信。
- **要同步电子邮件量**： 选择你想要同步的电子邮件的时间量。 或选择“无限制”，以同步所有可用的电子邮件。
- **要同步的内容类型**（仅限 Nine Work): 选择你想要同步的设备上的数据。 选项包括：
  - **联系人**：选择“启用”可允许最终用户将联系人同步到自己的设备。
  - **日历**：选择“启用”可允许最终用户将日历同步到自己的设备。
  - **任务**：选择“启用”可允许最终用户将所有任务都同步到自己的设备。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android Samsung Knox](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 及更高版本](email-settings-windows-10.md)和 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 设备创建电子邮件配置文件。
