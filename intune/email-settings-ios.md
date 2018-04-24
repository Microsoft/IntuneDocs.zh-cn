---
title: 适用于 iOS 设备的 Microsoft Intune 电子邮件设置
titleSuffix: ''
description: 了解可用于在运行 iOS 的设备上配置电子邮件设置的 Microsoft Intune 设置。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7b050e94114b0d3c9dcec765f4dd6e7700a801f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>Microsoft Intune 中适用于运行 iOS 的设备的电子邮件配置文件设置 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可为运行 iOS 的设备配置的电子邮件配置文件设置。

## <a name="email-settings"></a>电子邮件设置

- **电子邮件服务器** - Exchange 服务器的主机名。
- **帐户名称** - 电子邮件帐户的显示名称，它将显示在用户设备上。
- **AAD 中的用户名属性** - 这是 Active Directory (AD) 或 Azure AD 中的属性，用于生成此电子邮件配置文件的用户名。 选择“主 SMTP 地址”，例如 **user1@contoso.com**，或“用户主体名称”，例如 **user1** 或 **user1@contoso.com**。
- **AAD 中的电子邮件地址属性** - 每个设备上用户的电子邮件地址的生成方式。 选择“主 SMTP 地址”以使用主 SMTP 地址登录到 Exchange，或使用“用户主体名称”以使用完整主体名称作为电子邮件地址。
- **身份验证方法** - 选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
    - 如果已选择“证书”，请选择之前创建的、用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **SSL** - 发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时，使用安全套接字层 (SSL) 通信。
- **S/MIME** - 使用 S/MIME 签名发送传出的电子邮件。
    - 如果已选择“证书”，请选择之前创建的、用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **要同步的电子邮件数** - 选择要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。
- **允许将消息移动到其他电子邮件帐户** - 此选项允许用户在其设备上已配置的不同帐户间移动电子邮件。
- **允许从第三方应用程序发送电子邮件** - 允许用户选择此配置文件作为用于发送电子邮件的默认帐户，并允许第三方应用程序在本机电子邮件应用中打开电子邮件，例如，将文件附加到电子邮件。
- **同步最近使用的电子邮件地址** - 此功能允许用户将设备上最近使用的电子邮件地址的列表与服务器同步。
