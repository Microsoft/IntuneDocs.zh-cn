---
title: Microsoft Intune 中适用于 iOS 设备的电子邮件设置 - Azure | Microsoft Docs
description: 创建使用 Exchange 服务器的设备配置电子邮件配置文件，并从 Azure Active Directory 检索属性。 还可启用 SSL，使用证书或用户名/密码对用户进行身份验证，并使用 Microsoft Intune 在 iOS 设备上同步电子邮件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6fd10ab6a1e9dd7249e2ae1d4bf558d190276ed
ms.sourcegitcommit: b0ee8626191961dc07f9f7f9d8e6a5fb09c63350
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51505872"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>适用于 iOS 设备的电子邮件配置文件设置 - Intune

使用电子邮件配置文件设置来配置运行 iOS 的设备。

> [!IMPORTANT]
> 我们即将对本文介绍的 S/MIME 功能进行一些改进。 因此，Intune 暂不提供 S/MIME 功能。 我们将在这项功能发布后删除此说明。

## <a name="email-settings"></a>电子邮件设置

- **电子邮件服务器**：输入 Exchange 服务器的主机名。
- **帐户名称**：输入电子邮件帐户的显示名称。 该名称将显示在用户的设备上。
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

- **AAD 中的电子邮件地址属性**：选择生成用户的电子邮件地址的方式。 选择“用户主体名称”（`user1@contoso.com` 或 `user1`），使用完整的用户主体名称作为电子邮件地址。 选择**主 SMTP 地址** (`user1@contoso.com`)，使用主 SMTP 地址登录 Exchange。
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

- S/MIME：选择“启用 S/MIME”后，可使用 S/MIME 签名发送传出的电子邮件。 启用后，还可以加密发送给收件人（可以接收加密电子邮件）的电子邮件，并解密接收自发件人的电子邮件。
  - 如果选择“证书”，请选择现有 PKCS 证书配置文件以验证 Exchange 连接和/或加密电子邮件通信。
- **要同步的电子邮件数**：选择要同步的电子邮件的天数。 或选择“无限制”以同步所有可用的电子邮件。
- **允许将消息移动到其他电子邮件帐户**：选择“启用”后，用户可在其设备上配置的不同帐户间移动电子邮件。
- **允许从第三方应用程序发送电子邮件**：选择“启用”后，用户可选择此配置文件作为发送电子邮件的默认帐户。 该选项允许第三方应用程序在本机电子邮件应用中打开电子邮件，例如将文件附加到电子邮件。
- 同步最近使用的电子邮件地址：选择“启用”后，用户可将设备上最近使用的电子邮件地址的列表与服务器同步。

## <a name="next-steps"></a>后续步骤
[在 Intune 中配置电子邮件设置](email-settings-configure.md)
