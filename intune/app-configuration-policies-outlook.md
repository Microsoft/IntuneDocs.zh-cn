---
title: Microsoft Intune 中适用于 iOS 和 Android 设备的 Outlook 设置
description: 创建配置策略以设置在 iOS 和 Android 设备上运行的 Microsoft Outlook 设置。
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 691029cc7b9fd8880c5440a84b95bbf2462920d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180317"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook 配置设置 

使用配置策略以设置在 iOS 和 Android 设备上运行的 Microsoft Outlook 设置。 

要为托管的 iOS 设备创建应用配置策略，请参阅[为托管的 iOS 设备添加应用配置策略](app-configuration-policies-use-ios.md)。 要为托管的 Android 设备创建应用配置策略，请参阅[为托管的 Android 设备添加应用配置策略](app-configuration-policies-use-android.md)。 

## <a name="configuration-settings"></a>配置设置

在 Intune 中添加配置策略时，可设置用于配置 Microsoft Outlook 的特定设置。 在“配置设置”窗格中，可设置电子邮件帐户配置。

### <a name="basic-authentication-email-account-settings"></a>基本身份验证电子邮件帐户设置
Outlook for iOS 和 Outlook for Android 使 Exchange 管理员能够将帐户配置“推送”到通过 ActiveSync 协议使用基本身份验证的本地用户。 有关详细信息，请参阅 [Outlook for iOS 和 Outlook for Android 中使用基本身份验证的帐户设置](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup)。 若要启用帐户设置配置，可以配置以下设置：

- **电子邮件服务器**：输入本地 Exchange Server 的主机名（例如，mail.contoso.com）。
- **电子邮件帐户名称**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (Azure AD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 您的选择包括：
  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **主 SMTP 地址**：获取格式为电子邮件地址的名称，如 `user1@contoso.com`
- **AAD 中的电子邮件地址属性**：选择生成用户的电子邮件地址的方式。 选择“用户主体名称”（`user1@contoso.com` 或 `user1`）以使用完整主体名称作为电子邮件地址，或选择“主 SMTP 地址”(`user1@contoso.com`) 以使用主 SMTP 地址登录到 Exchange。 建议选择“主 SMTP 地址”。
- **帐户域**：帐户的域（可选）。

## <a name="next-steps"></a>后续步骤
[在 Intune 中配置电子邮件设置](email-settings-configure.md)

