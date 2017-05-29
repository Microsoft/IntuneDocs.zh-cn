---
title: "配置 Skycure 以使用 Azure Active Directory 单一登录 | Microsoft Docs"
description: "配置 Skycure 以使用 Azure Active Directory 单一登录 (SSO)"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: bf4cf8441a0ff53abf3f7830f0cdd955a4317fb0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>配置 Skycure 以使用 Azure Active Directory 单一登录 (SSO)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

将 Intune 与 Skycure 集成时，使用 Azure AD SSO。 其主要优势是：

-   **管理员**每次从 Microsoft 门户（Intune、Azure）和 Skycure 管理控制台登录和注销时，都可以使用相同的凭据，无需再次输入。

-   **最终用户**每次从 Skycure 应用登录或注销时，都可以使用相同的 Azure AD 凭据，无需再次键入。

下面是将 Skycure 与 Azure Active Directory 单一登录 (SSO) 集成的步骤。

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>检索 Azure Active Directory 租户 ID

需要检索 Azure AD 租户 ID。

1.  转到 [Azure 门户](https://portal.azure.com/)，然后使用你的凭据进行登录。

2.  看到“仪表板”后，选择“Azure Active Directory”。

![Azure AD 仪表板](../media/mtp/skycure-sso-1.png)

1.  “Azure Active Directory”边栏选项卡打开后，请选择“属性”。

![Azure AD 属性边栏选项卡](../media/mtp/skycure-sso-2.png)

1.  单击“Azure Active Directory 属性”边栏选项卡上“租户目录 ID”下的“复制图标”。

> 将复制的 Directory ID 值粘贴到文本文件中，以便以后使用。 稍后在 Skycure 和 Intune 集成过程中将需要 Directory ID 值。

![Azure AD 仪表板](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>允许 Skycure 与 Azure Active Directory 通信

1.  在浏览器中输入以下 URL。 输入此前复制到文本文件的 Azure Active Directory 租户 ID（而不是 **DIRECTORY_ID**）。

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  需要使用 Azure Active Directory 凭据登录。 单击“接受”以继续。

![Azure AD 登录页](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>创建 Skycure 的 Azure AD 安全组（可选）

你可能想要创建一个专用用户组，其中包含运行 Skycure 的用户（例如 Skycure 用户）。 通过报告分析 Skycure 活动时，这可能有用。

-   详细了解[如何创建一个组并在 Azure AD 中添加成员](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)。

> [!NOTE] 
> 此外，还可以使用现有的 Azure AD 安全组。

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>配置 Azure AD 帐户，将 Intune 与 Skycure 相集成

1.  在 [Skycure 管理控制台](https://aad.skycure.com/)中输入之前保存在文本文件中的 Azure Active Directory 租户 ID。

![Skycure 管理控制台 Azure AD 租户 ID 字段](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure 通过查询 Azure AD 验证 Azure AD 租户 ID 是否存在，确定存在后，管理员可以继续执行下一步，即基本设置。

## <a name="next-steps"></a>后续步骤

[下载 Skycure iOS 应用配置策略](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

