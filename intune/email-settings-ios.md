---
title: Microsoft Intune 中适用于 iOS 设备的电子邮件设置 - Azure | Microsoft Docs
description: 请参阅可配置的所有电子邮箱设置列表，并添加到 Microsoft Intune 中的 iOS 设备，包括使用 Exchange 服务器和从 Azure Active Directory 获取属性。 还可启用 SSL，使用证书或用户名/密码对用户进行身份验证，并使用 Microsoft Intune 中的设备配置文件在 iOS 设备上同步电子邮件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd1f24c7114e21239d19ca2e99fc05d125e675d9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845769"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Intune 中适用于 iOS 设备的电子邮件配置文件设置

在 Microsoft Intune 中，可以创建和配置电子邮件，以连接到电子邮件服务器，选择用户的身份验证方式，将 S/MIME 用于加密等等。

本文列出并说明适用于运行 iOS 的设备的所有电子邮件设置。 可以创建设备配置文件，将这些电子邮件设置推送或部署到 iOS 设备。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](email-settings-configure.md#create-a-device-profile)。

## <a name="email-settings"></a>电子邮件设置

- **电子邮件服务器**：输入 Exchange 服务器的主机名。
- **帐户名**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
- **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (AAD) 获取的属性。 Intune 将动态生成此配置文件使用的用户名。 选项包括：
  - **用户主体名称**：获取名称，如 `user1` 或 `user1@contoso.com`
  - **主 SMTP 地址**：获取格式为电子邮件地址的名称，如 `user1@contoso.com`
  - **SAM 帐户名**：需要域，如 `domain\user1`。

    此外请输入：  
    - **用户域名源**：选择“AAD”(Azure Active Directory) 或“自定义”。

      选择从 AAD 获取属性时，请输入：
      - **AAD 中的用户域名属性**：选择获取用户的“完整域名”或“NetBIOS 名称”属性

      选择使用自定义属性时，请输入：
      - **要使用的自定义域名**：输入 Intune 用于域名的值，如 `contoso.com` 或 `contoso`

- **AAD 中的电子邮件地址属性**：选择用户电子邮件地址的生成方式。 选择“用户主体名称”（`user1@contoso.com` 或 `user1`），使用完整的用户主体名称作为电子邮件地址。 选择**主 SMTP 地址** (`user1@contoso.com`)，使用主 SMTP 地址登录 Exchange。
- **身份验证方法**：选择“用户名和密码”或“证书”作为电子邮件配置文件所用的身份验证方法。 不支持 Azure 多重身份验证。
  - 如果已选择“证书”，请选择之前创建的、用于对 Exchange 连接进行身份验证的客户端 SCEP 或 PKCS 证书配置文件。
- **SSL**：选择“启用”后，可在发送电子邮件、接收电子邮件以及与 Exchange 服务器通信时使用安全套接字层 (SSL) 通信。
- **OAuth**：选择“启用”后，可在发送电子邮件、接收电子邮件以及与 Exchange 通信时使用 Open Authorization (OAuth) 通信。 如果 OAuth 服务器使用证书身份验证，请选择“证书”作为“身份验证方法”，并将证书包含在配置文件中。 否则，请选择“用户名和密码”作为“身份验证方法”。 使用 OAuth 时，请确保：

  - 确认电子邮件解决方案支持 OAuth 后，再将此配置文件提供给用户。 Office 365 Exchange online 支持 OAuth。 本地 Exchange 和其他合作伙伴或第三方解决方案可能不支持 OAuth。 可为新式身份验证配置本地 Exchange，请参阅 [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/)（发布适用于 Exchange 内部部署的混合新式身份验证）博客文章。

    如果电子邮件配置文件使用 Oauth，并且电子邮件服务不支持，则会显示“重新输入密码”选项。 例如，当用户在 Apple 的设备设置中选择“重新输入密码”时，没有任何反应。

  - 启用 OAuth 后，最终用户将拥有支持多重身份验证 (MFA) 的不同“新式身份验证”电子邮件登录体验。 

  - 某些组织会禁用最终用户执行[自助应用程序访问](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access)。 在这种情况下，新式身份验证登录可能会失败，除非管理员创建“iOS 帐户”企业应用，并授予用户访问 Azure AD 中的应用的权限。

    默认操作是使用[应用程序访问面板](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction)的“添加应用”功能添加应用程序，而无需经过业务审批。 有关详细信息，请参阅[将用户分配给应用程序](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications)。

  > [!NOTE]
  > 启用 OAuth 时，会发生以下情况：  
  > 1. 已指定的设备将发布新的配置文件。
  > 2. 系统会提示最终用户再次输入其凭据。

- **S/MIME**：选择“启用 S/MIME”后，用户可在 iOS 本机邮件应用程序中登录和/或加密电子邮件。 

  如果对电子邮件使用 S/MIME，可确认发件人的真实性以及邮件的完整性和保密性。

  - **已启用 S/MIME 签名**：选择“启用”后，允许用户可对所输入帐户的传出电子邮件进行数字签名。 签名可帮助收件人确定邮件来自特定发件人，而不是来自假扮的发件人。 选择“禁用”后，不允许用户对邮件进行数字签名。
    - **允许用户更改设置**：选择“启用”后，用户可更改 S/MIME 签名行为。 选择“禁用”后，防止用户更改所配置的 S/MIME 签名设置。 在 iOS 12 和更高版本中可用。

  - **S/MIME 签名证书**：选择用于签名电子邮件的现有 PKCS 或 SCEP 证书配置文件。
    - **允许用户更改设置**：选择“启用”后，用户可更改签名证书。 选择“禁用”后，防止用户更改签名证书，并强制用户使用所配置的证书。 在 iOS 12 和更高版本中可用。

  - **默认加密**：选择“启用”后，可将加密所有邮件作为默认行为。 选择“禁用”后，不会将加密所有邮件作为默认行为。
    - **允许用户更改设置**：选择“启用”后，允许用户更改默认加密行为。 选择“禁用”后，防止用户更改加密默认行为，并强制用户使用所配置的设置。 在 iOS 12 和更高版本中可用。

  - **强制按每封邮件加密**：“按每封邮件加密”允许用户选择哪些电子邮件需要在发送前进行加密。 选择“启用”后，可在创建新电子邮件时显示“按每封邮件加密”选项。 然后，用户可以选择加入或选择退出“按每封邮件加密”。 选择“禁用”后，可阻止显示“按每封邮件加密”选项。

    如果已启用“默认加密”设置，则启用“按每封邮件加密”允许用户选择退出加密每封邮件。 如果已禁用“默认加密”设置，则启用“按每封邮件加密”允许用户选择加入加密每封邮件。

  - **S/MIME 加密证书**：选择用于加密电子邮件的现有 PKCS 或 SCEP 证书配置文件。
    - **允许用户更改设置**：选择“启用”后，用户可更改加密证书。 选择“禁用”后，防止用户更改加密证书，并强制用户使用所配置的证书。 在 iOS 12 和更高版本中可用。
- **要同步的电子邮件数**：选择你想要同步的电子邮件的天数。 或选择“无限制”以同步所有可用的电子邮件。
- **允许将邮件转移到其他电子邮件帐户**：选择“启用”后，用户可在其设备上配置的不同帐户间转移电子邮件。
- **允许从第三方应用程序发送电子邮件**：选择“启用”后，用户可选择此配置文件作为发送电子邮件的默认帐户。 该选项允许第三方应用程序在本机电子邮件应用中打开电子邮件，例如将文件附加到电子邮件。
- **同步最近使用的电子邮件地址**：选择“启用”后，用户可将设备上最近使用的电子邮件地址的列表与服务器同步。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

在 [Android](email-settings-android.md)、[Windows 10](email-settings-windows-10.md) 和 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 设备上配置电子邮件设置。
