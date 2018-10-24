---
title: Microsoft Intune 中适用于 iOS 和 Android 设备的 Outlook 设置
description: 创建配置策略以设置在 iOS 和 Android 设备上运行的 Microsoft Outlook 设置。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828666"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook 配置设置 

使用配置策略以设置在 iOS 和 Android 设备上运行的 Microsoft Outlook 设置。 

要为托管的 iOS 设备创建应用配置策略，请参阅[为托管的 iOS 设备添加应用配置策略](app-configuration-policies-use-ios.md)。 要为托管的 Android 设备创建应用配置策略，请参阅[为托管的 Android 设备添加应用配置策略](app-configuration-policies-use-android.md)。 

## <a name="configuration-settings"></a>配置设置

在 Intune 中添加配置策略时，可设置用于配置 Microsoft Outlook 的特定设置。 在“配置设置”窗格中，可设置电子邮件帐户配置。

### <a name="email-account-settings"></a>电子邮件账户设置

以下配置设置特定于 Microsoft Outlook。

- **电子邮件服务器**：输入 Exchange 服务器的主机名。
- **电子邮件帐户名称**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (AAD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：
  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **主 SMTP 地址**：获取格式为电子邮件地址的名称，如 `user1@contoso.com`
  - **sAM 帐户名称**：需要域，如 `domain\user1`。

    此外请输入：  
    - **用户域名源**：选择“AAD”(Azure Active Directory) 或“自定义”。

      选择从 AAD 获取属性时，请输入：
      - **AAD 中的用户域名属性**：选择获取用户的完整域名或 NetBIOS 名称属性

      选择使用自定义属性时，请输入：
      - **要使用的自定义域名**：输入 Intune 用于域名的值，如 `contoso.com` 或 `contoso`

- **AAD 中的电子邮件地址属性**：选择生成用户的电子邮件地址的方式。 选择“用户主体名称”（`user1@contoso.com` 或 `user1`）以使用完整主体名称作为电子邮件地址，或选择“主 SMTP 地址”(`user1@contoso.com`) 以使用主 SMTP 地址登录到 Exchange。
- **帐户域**：帐户的域（可选）。

## <a name="next-steps"></a>后续步骤
[在 Intune 中配置电子邮件设置](email-settings-configure.md)

