---
title: Microsoft Intune 中的 Android Enterprise 电子邮件设置 - Azure | Microsoft Docs
description: 创建使用 Exchange 服务器并从 Azure Active Directory 检索属性的设备配置电子邮件配置文件。 在 Android 工作配置文件设备上，使用 Microsoft Intune 启用 SSL 或 SMIME、通过证书或用户名/密码对用户进行身份验证，以及同步电子邮件和日程安排。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92d81e383a9964aaecbdd151397879236ffcb726
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72493555"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune 中用于配置电子邮件、身份验证和同步的 Android Enterprise 设备设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出并介绍了可以在 Android Enterprise 设备上控制的各种电子邮件设置。 在移动设备管理 (MDM) 解决方案中，使用这些设置可配置电子邮件服务器、使用 SSL 加密电子邮件等。

Intune 管理员可以为工作配置文件中的 Android Enterprise 设备创建并分配电子邮件设置。

若要详细了解 Intune 中的电子邮件配置文件，请参阅[配置电子邮件设置](email-settings-configure.md)。

## <a name="before-you-begin"></a>开始之前

创建[设备配置文件](email-settings-configure.md#create-a-device-profile)（选择工作配置文件）或创建[应用配置策略](../apps/app-configuration-policies-use-android.md)。

## <a name="android-enterprise"></a>Android Enterprise

- **电子邮件应用**：选择“Gmail”或“Nine Work”  
- **电子邮件服务器**：Exchange 服务器的主机名。 例如，输入 `outlook.office365.com`。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (Azure AD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：

  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **用户名**：仅获取名称，如 `user1`

- **AAD 中的电子邮件地址属性**：此名称是 Intune 从 Azure AD 获取的电子邮件属性。 Intune 动态生成此配置文件使用的电子邮件地址。 选项包括：
  - **用户主体名称**：使用完整的主体名称（如 `user1@contoso.com` 或 `user1`）作为电子邮件地址。
  - **主 SMTP 地址**：使用主 SMTP 地址（如 `user1@contoso.com`）登录 Exchange。

- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法   。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件  。
- **SSL**：选择“启用”可以在发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时使用安全套接字层 (SSL) 通信  。
- **要同步的电子邮件数**：选择要同步的电子邮件的时间量。 或选择“无限制”  ，以同步所有可用的电子邮件。
- **要同步的内容类型**（仅限 Nine Work）：选择要在设备上同步的数据。 选项包括：
  - **联系人**：选择“启用”可允许最终用户将联系人同步到自己的设备  。
  - **日历**：选择“启用”可允许最终用户将日历同步到自己的设备  。
  - **任务**：选择“启用”可允许最终用户将所有任务都同步到自己的设备  。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android Samsung Knox](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 及更高版本](email-settings-windows-10.md)和 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 设备创建电子邮件配置文件。
