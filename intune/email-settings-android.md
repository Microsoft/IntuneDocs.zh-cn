---
title: Microsoft Intune 中的 Android 和 Android Enterprise 电子邮件设置 - Azure | Microsoft Docs
description: 创建使用 Exchange 服务器并从 Azure Active Directory 检索属性的设备配置电子邮件配置文件。 在 Android 和 Android 工作配置文件设备上，使用 Microsoft Intune 启用 SSL 或 SMIME、通过证书或用户名/密码对用户进行身份验证，以及同步电子邮件和日程安排。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ffe25f7e4870f2ea6969d1261f33c69362d75469
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032021"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>用于在 Intune 中配置电子邮件、身份验证和同步的 Android 和 Android Enterprise 设备设置

本文列出并介绍了可以在 Android 和 Android Enterprise 设备上控制的各种电子邮件设置。 在移动设备管理 (MDM) 解决方案中，使用这些设置可配置电子邮件服务器、使用 SSL 加密电子邮件等。

Intune 管理员可以为以下 Android 设备创建并分配电子邮件设置：

- Android Samsung Knox Standard
- Android Enterprise

## <a name="before-you-begin"></a>开始之前

[创建设备配置配置文件](email-settings-configure.md)。

## <a name="android-samsung-knox"></a>Android (Samsung KNOX)

- **电子邮件服务器**：输入 Exchange 服务器的主机名。
- **帐户名**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (AAD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：
  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **用户名**：仅获取名称，如 `user1`
  - **SAM 帐户名**：需要域，如 `domain\user1`。 sAM 帐户名仅用于 Android 设备。 不支持 Android Enterprise。

    此外请输入：  
    - **用户域名源**：选择“AAD”(Azure Active Directory) 或“自定义”。

      选择从 AAD 获取属性时，请输入：
      - **AAD 中的用户域名属性**：选择获取用户的“完整域名”或“NetBIOS 名称”属性

      选择使用自定义属性时，请输入：
      - **要使用的自定义域名**：输入 Intune 用于域名的值，如 `contoso.com` 或 `contoso`

- **AAD 中的电子邮件地址属性**：选择用户电子邮件地址的生成方式。 选择“用户主体名称”（`user1@contoso.com` 或 `user1`）以使用完整主体名称作为电子邮件地址，或选择“主 SMTP 地址”(`user1@contoso.com`) 以使用主 SMTP 地址登录到 Exchange。

- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

### <a name="security-settings"></a>安全设置

- **SSL**：发送电子邮件、接收电子邮件以及与 Exchange Server 通信时，请使用安全套接字层 (SSL) 通信。
- **S/MIME**：发送使用 S/MIME 加密的传出电子邮件。
  - 如果选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

### <a name="synchronization-settings"></a>同步设置

- **要同步的电子邮件数**：选择要同步多少天的电子邮件，或选择“无限制”同步所有可用电子邮件。
- **同步计划**：选择设备同步 Exchange 服务器中数据的计划。 你还可以选择“在邮件到达时”（在邮件到达时同步数据），或选择“手动”（设备用户必须启动同步）。

### <a name="content-sync-settings"></a>内容同步设置

- **要同步的内容类型**：选择要从以下项同步到设备的内容类型：
  - **联系人**
  - **日历**
  - **任务**

## <a name="android-enterprise"></a>Android Enterprise

- **电子邮件应用**：选择“Gmail”或“Nine Work”
- **电子邮件服务器**：Exchange 服务器的主机名。
- **AAD 中的用户名属性**：此名称是 Active Directory (AD) 或 Azure AD 中的属性，用于生成此电子邮件配置文件的用户名。 选择“主 SMTP 地址”（如 user1@contoso.com）或“用户主体名称”（如 user1 或 user1@contoso.com）。
- **AAD 中的电子邮件地址属性**：每个设备上用户电子邮件地址的生成方式。 选择“用户主体名称”，使用完整的用户主体名称作为电子邮件地址，或者选择“用户名”。
- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
  - 如果已选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **SSL**：发送电子邮件、接收电子邮件以及与 Exchange Server 通信时，请使用安全套接字层 (SSL) 通信。
- **要同步的电子邮件数**：选择要同步多少天的电子邮件，或选择“无限制”同步所有可用电子邮件。
- **要同步的内容类型**（仅限 Nine Work）：选择要从以下项同步到设备的内容类型：
  - **联系人**
  - **日历**
  - **任务**

## <a name="next-steps"></a>后续步骤
[在 Intune 中配置电子邮件设置](email-settings-configure.md)
