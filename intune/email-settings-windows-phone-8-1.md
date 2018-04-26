---
title: 适用于 Windows Phone 8.1 的 Microsoft Intune 电子邮件设置
titleSuffix: ''
description: 了解可用于在运行 Windows Phone 8.1 的设备上配置电子邮件连接的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4c10ba57930a7aa22fdc2b56f6450437eb613cd9
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Microsoft Intune 中适用于运行 Windows Phone 8.1 的设备的电子邮件配置文件设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可为运行 Windows Phone 8.1 的设备配置的电子邮件配置文件设置。


- **将所有设置仅应用于 Windows Phone 8.1** - 可以在 Intune 经典门户中配置此设置。 在 Azure 门户中无法更改此设置。 如果将此项设置为“已配置”，则任何设置仅应用于 Windows Phone 8.1 设备。 如果将此项设置为“未配置”，则这些设置也适用于 Windows 10 移动版设备。
- **电子邮件服务器** - Exchange 服务器的主机名。
- **帐户名称** - 电子邮件帐户的显示名称，它将显示在用户设备上。
- **AAD 中的用户名属性** - 这是 Active Directory (AD) 或 Azure AD 中的属性，用于生成此电子邮件配置文件的用户名。 选择“主 SMTP 地址”，例如 **user1@contoso.com**，或“用户主体名称”，例如 **user1** 或 **user1@contoso.com**。
- **AAD 中的电子邮件地址属性** - 每个设备上用户的电子邮件地址的生成方式。 选择“主 SMTP 地址”以使用主 SMTP 地址登录到 Exchange，或使用“用户主体名称”以使用完整主体名称作为电子邮件地址。


## <a name="security-settings"></a>安全设置

- **SSL** - 发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时，使用安全套接字层 (SSL) 通信。



## <a name="synchronization-settings"></a>同步设置

- **要同步的电子邮件数** - 选择要同步的电子邮件的天数，或选择“无限制”以同步所有可用的电子邮件。
- **同步计划** - 选择设备同步 Exchange Server 的数据所依据的计划。 你还可以选择“在邮件到达时”（在邮件到达时同步数据），或选择“手动”（设备用户必须启动同步）。

## <a name="content-sync-settings"></a>内容同步设置

- **要同步的内容类型** - 从以下项选择要同步到设备的内容类型：
    - **联系人**
    - **日历**
    - **任务**
