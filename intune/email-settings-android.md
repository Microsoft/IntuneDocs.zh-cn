---
title: Microsoft Intune 中的 Android 电子邮件设置 - Azure | Microsoft Docs
description: 创建使用 Exchange 服务器并从 Azure Active Directory 检索属性的设备配置电子邮件配置文件。 在 Android Samsung KNOX 设备上，使用 Microsoft Intune 启用 SSL 或 SMIME、通过证书或用户名/密码验证用户身份，以及同步电子邮件和日程安排。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94f907ee8805c5f0559e8751a7cd69bacf1612ee
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565497"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune 中用于配置电子邮件、身份验证和同步的 Android 设备设置

本文列出并介绍了可以在 Intune 中的 Android Samsung KNOX 设备上控制的各种电子邮件设置。 在移动设备管理 (MDM) 解决方案中，使用这些设置可配置电子邮件服务器、使用 SSL 加密电子邮件等。

作为 Intune 管理员，可以创建电子邮件设置，并将这些设置分配到 Android Samsung KNOX Standard 设备。

若要详细了解 Intune 中的电子邮件配置文件，请参阅[配置电子邮件设置](email-settings-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置配置文件](email-settings-configure.md#create-a-device-profile)。

## <a name="android-samsung-knox"></a>Android (Samsung KNOX)

- **电子邮件服务器**：输入 Exchange 服务器的主机名。 例如，输入 `outlook.office365.com`。
- **帐户名称**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (Azure AD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：
  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **用户名**：仅获取名称，如 `user1`
  - **sAM 帐户名称**：需要域，如 `domain\user1`。 sAM 帐户名仅用于 Android 设备。

    此外请输入：  
    - **用户域名源**：选择“AAD”(Azure Active Directory) 或“自定义”。

      选择从 AAD 获取属性时，请输入：
      - **AAD 中的用户域名属性**：选择获取用户的完整域名或 NetBIOS 名称属性

      选择使用自定义属性时，请输入：
      - **要使用的自定义域名**：输入 Intune 用于域名的值，如 `contoso.com` 或 `contoso`

- **来自 AAD 的电子邮件地址属性**： 此名称是从 Azure AD 获取 Intune 的电子邮件属性。 Intune 动态生成此配置文件使用的电子邮件地址。 选项包括：
  - **用户主体名称**：使用完整的主体名称（如 `user1@contoso.com` 或 `user1`）作为电子邮件地址。
  - **主 SMTP 地址**： 使用主 SMTP 地址，如`user1@contoso.com`，以登录到 Exchange。

- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

### <a name="security-settings"></a>安全设置

- **SSL**：发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时，使用安全套接字层 (SSL) 通信。
- **S/MIME**：使用 S/MIME 加密发送传出电子邮件。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

### <a name="synchronization-settings"></a>同步设置

- **要同步的电子邮件数**：选择要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。
- **同步计划**：选择设备的计划，以同步 Exchange 服务器中的数据。 你还可以选择“在邮件到达时”（在邮件到达时同步数据），或选择“手动”（设备用户必须启动同步）。

### <a name="content-sync-settings"></a>内容同步设置

- **要同步的内容类型**：选择要在设备上同步的内容类型。 “未配置”会禁用此设置。 设置为“未配置”时，如果最终用户在设备上启用同步，则当设备与 Intune 同步时，将再次禁用同步，因为策略已得到加强。 

  可以同步以下内容：  
  - **联系人**：选择“启用”可允许最终用户将联系人同步到自己的设备。
  - **日历**：选择“启用”可允许最终用户将日历同步到自己的设备。
  - **任务**：选择“启用”可允许最终用户将所有任务都同步到自己的设备。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android Enterprise（工作配置文件）](email-settings-android-enterprise.md)、[iOS](email-settings-ios.md)、[Windows 10 及更高版本](email-settings-windows-10.md)和 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 创建电子邮件配置文件。
