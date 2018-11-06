---
title: 在 Microsoft Intune 中添加适用于 iOS 设备的单一登录 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建、配置、允许，或支持 iOS 设备使用单一登录 (SSO) 而不是密码，对组织的资源和数据进行身份验证。 若要使用 SSO，请创建设备配置文件，并输入 UPN、设备 ID、应用和证书，对用户和设备进行身份验证。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992003"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>在 Microsoft Intune 中使用单一登录 iOS 设备

大多数业务线 (LOB) 应用需要某种级别的用户身份验证，才能支持安全性。 在许多情况下，此类身份验证需要用户多次输入同一凭据，这可能会让用户感到失望。 为改善用户体验，开发人员可以创建使用单一登录 (SSO) 的应用，从而减少用户必须输入凭据的次数。

本文介绍如何使用 Microsoft Intune 中的设备配置文件，为 iOS 设备启用单一登录。

## <a name="before-you-begin"></a>在开始之前

确保拥有一个应用，其编写目的是在 iOS 设备上查找单一登录有效负载中的用户凭据存储。

## <a name="create-the-sso-profile"></a>创建 SSO 配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `ios sso profile`。
    - **说明**：输入带重要术语的说明，帮助在列表中查找配置文件。
    - **平台**：选择“iOS”。
    - **配置文件类型**：选择“设备功能”。

4. 选择“单一登录”。

    ![“单一登录”页](./media/sso-blade.png)

5. 输入以下设置： 

    - **来自 AAD 的用户名属性**：Intune 为 Azure AD 中的每个用户寻找此属性。 然后，Intune 在生成安装于设备上的 XML 有效负载之前填充相应字段（如 UPN）。 选项包括：
    
        - **用户主体名称**：通过以下方式分析 UPN：

            ![用户名属性](media/User-name-attribute.png)

            还可以使用在“领域”文本框中键入的文本覆盖该领域。

            例如，Contoso 可能有几个子区域，如欧洲、亚洲和北美。 它们可能希望其亚洲用户使用 SSO 有效负载，并且该应用要求 UPN 采用 `username@asia.contoso.com` 格式。 在此情况下，如果选择“用户主体名称”，则每个用户的领域默认是从 Azure AD 中获取的，该领域可能是 contoso.com。 因此，可以专为亚洲用户创建此有效负载并使用值 asia.contoso.com 覆盖领域。 现在，最终用户的 UPN 会变为 username@asia.contoso.com，而不是 username@contoso.com。

        - **Intune 设备 ID**：Intune 会自动选择 Intune 设备 ID。 

            默认情况下，应用只需使用设备 ID。 但如果应用使用领域和设备 ID，则可在“领域”文本框中键入该领域。

            > [!NOTE]
            > 如果使用设备 ID，则默认将领域留空。

    - **领域**：URL 的域部分。
    
    - **使用单一登录的 URL 前缀**：添加组织中要求用户进行单一登录身份验证的任何 URL。 

        例如，用户连接到任何这些站点时，iOS 设备会使用单一登录凭据。 用户不需要输入任何其他凭据。 但是，如果已启用多重身份验证，则用户必须输入第二重身份验证。

        > [!NOTE]
        > 这些 URL 必须采用正确格式化的 FQDN。 Apple 要求这些 URL 采用 `http://<yourURL.domain>` 格式。

        匹配模式的 URL 必须以 `http://` 或 `https://` 开头。 系统将执行简单的字符串匹配，因此 URL 前缀 `http://www.contoso.com/` 与 `http://www.contoso.com:80/` 不匹配。 但是，在 iOS 10.0 或更高版本中，单个通配符 \* 可用于输入所有匹配的值。 例如，`http://*.contoso.com/` 同时匹配 `http://store.contoso.com/` 和 `http://www.contoso.com`。

        模式 `http://.com` 和 `https://.com` 分别匹配所有的 HTTP 和 HTTPS URL。
    
    - **使用单一登录的应用**：在可以使用单一登录的用户设备上添加应用。 

        `AppIdentifierMatches` 数组必须包含与应用程序包 ID 匹配的字符串。 这些字符串可以是完全匹配项（例如：`com.contoso.myapp`），也可以通过使用 \* 通配符输入捆绑 ID 的前缀匹配项。 通配符必须位于句点字符 (.) 后，并可能只在字符串末尾出现一次（例如：`com.contoso.*`）。 如果包括通配符，则程序包 ID 以前缀开头的任何应用都将被授予对帐户的访问权限。

        使用应用名称输入一个用户友好名称，帮助识别捆绑 ID。
    
    - **凭据续订证书**：如果使用证书（而不是密码）进行身份验证，则选择作为身份验证证书部署给用户的 SCEP 或 PFX 证书。 通常，这是针对其他配置文件（例如 VPN、Wi-Fi 或电子邮件）部署给用户的相同证书。

6. 选择“确定” > “确定” > “创建”以保存更改，并创建配置文件。 创建完成后，该配置文件将显示在“设备配置 - 配置文件”列表中。 

## <a name="next-steps"></a>后续步骤

有关其他设备功能配置信息，请参阅[如何在 Microsoft Intune 中配置设备功能设置](device-features-configure.md)。

向 iOS 设备[分配此配置文件](device-profile-assign.md)。
