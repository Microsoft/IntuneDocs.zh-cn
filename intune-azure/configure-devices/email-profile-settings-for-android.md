---
title: "Android 设备的 Intune 电子邮件设置 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可用于在 Android 设备上配置电子邮件连接的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4d3458cc-fcaa-4648-b13f-bf1f0616c1c5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 29a4346a04470192553ad2d4f0962a2a21d637ec
ms.lasthandoff: 02/16/2017


---

# <a name="email-profile-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Android 设备的电子邮件配置文件设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **电子邮件服务器** - Exchange 服务器的主机名。
- **帐户名称** - 电子邮件帐户的显示名称，它将显示在用户设备上。
- **AAD 中的用户名属性** - 这是 Active Directory (AD) 或 Azure AD 中的属性，将用于生成此电子邮件配置文件的用户名。 选择“主 SMTP 地址”（如 user1@contoso.com）或“用户主体名称”（如 user1 或 user1@contoso.com）。
- **AAD 中的电子邮件地址属性** - 每个设备上用户的电子邮件地址的生成方式。 选择“主 SMTP 地址”以使用主 SMTP 地址登录到 Exchange，或使用“用户主体名称”以使用完整主体名称作为电子邮件地址。
- **身份验证方法** - 选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
    - 如果已选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

## <a name="security-settings"></a>安全设置

- **SSL** - 发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时，使用安全套接字层 (SSL) 通信。
- **S/MIME** - 使用 S/MIME 加密发送传出电子邮件。
    - 如果已选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。

## <a name="synchronization-settings"></a>同步设置

- **要同步的电子邮件数** - 选择要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。
- **同步计划** - 选择设备同步 Exchange Server 的数据所依据的计划。 你还可以选择“在邮件到达时”（在邮件到达时同步数据），或选择“手动”（设备用户必须启动同步）。

## <a name="content-sync-settings"></a>内容同步设置

- **要同步的内容类型** - 从以下项选择要同步到设备的内容类型：
    - **联系人**
    - **日历**
    - **任务**

