---
title: "适用于 iOS 设备的 Intune 电子邮件设置 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解 iOS 设备上可用于配置电子邮件连接的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f16c9dfb41cb2cfe07ce473a131dac767dee9c74
ms.openlocfilehash: 255a5e8c8b430e15aba989e1ce805f7d627f0e0c


---

# <a name="email-profile-settings-for-ios-devices-in-intune-azure-preview"></a>Intune Azure 预览版中适用于 iOS 设备的电子邮件配置文件设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **电子邮件服务器** - Exchange 服务器的主机名。
- **帐户名称** - 电子邮件帐户的显示名称，它将显示在用户设备上。
- **AAD 中的用户名属性** - 这是 Active Directory (AD) 或 Azure AD 中的属性，将用于生成此电子邮件配置文件的用户名。 选择“主 SMTP 地址”，例如 **user1@contoso.com**，或“用户主体名称”，例如 **user1** 或 **user1@contoso.com**。
- **AAD 中的电子邮件地址属性** - 每个设备上用户的电子邮件地址的生成方式。 选择“主 SMTP 地址”以使用主 SMTP 地址登录到 Exchange，或使用“用户主体名称”以使用完整主体名称作为电子邮件地址。
- **身份验证方法** - 选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。
    - 如果已选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **SSL** - 发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时，使用安全套接字层 (SSL) 通信。
- **S/MIME** - 使用 S/MIME 加密发送传出电子邮件。
    - 如果已选择“证书”，请选择之前创建的、将用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **要同步的电子邮件数** - 选择要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。
- **允许将消息移动到其他电子邮件帐户** - 此选项允许用户在其设备上已配置的不同帐户间移动电子邮件。
- **允许从第三方应用程序发送电子邮件** - 允许用户选择此配置文件作为用于发送电子邮件的默认帐户，并允许第三方应用程序在本机电子邮件应用中打开电子邮件，例如，将文件附加到电子邮件。
- **同步最近使用的电子邮件地址** - 此功能允许用户将设备上最近使用的电子邮件地址的列表与服务器同步。



<!--HONumber=Feb17_HO1-->


