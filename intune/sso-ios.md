---
title: 配置 Microsoft Intune for iOS 设备 SSO
titlesuffix: ''
description: 了解如何配置 Microsoft Intune for iOS 设备 SSO。
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
ms.openlocfilehash: 8f19320df9a9728cdd77e608fc0ad219272a731f
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>配置 Microsoft Intune for iOS 设备 SSO

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

大多数业务线 (LOB) 应用需要某种级别的用户身份验证，才能支持安全性。 在许多情况下，这需要用户多次输入同一凭据，这可能会让用户感到失望。 为改善用户体验，开发人员可以创建使用 SSO 的应用，从而减少用户必须提供凭据的次数。

要充分利用 iOS 设备 SSO，必须具备以下条件：

- 一个应用，其编写目的是在 iOS 设备上查找 SSO 有效负载中的用户凭据存储。
- Intune 配置有 iOS 设备 SSO。

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>配置 Intune for iOS 设备 SSO


1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
4. 在“管理”部分的“设备配置”窗格上，选择“配置文件”。
5. 在“配置文件”窗格上，选择“创建配置文件”。
6. 提供名称和描述，并配置下列设置：
   - **平台**：选择“iOS”。
   - **配置文件类型**：选择“设备功能”。
7. 在“设备功能”窗格上，选择“单一登录”。

   ![“单一登录”页](./media/sso-blade.png)

8. 使用以下摘要表格，帮助填写“单一登录”窗格上的字段。 有关详细信息，请参阅表格后的各节。

   |字段  |注意|
   |---------|---------|
   |**来自 AAD 的用户名属性**|Intune 为 AAD 中的每个用户查看的属性，并在生成安装于设备上的 XML 有效负载之前填充相应字段（如 UPN）。|
   |**领域**|URL 的域部分。|
   |**使用 SSO 的 URL 前缀**|组织中要求用户进行 SSO 身份验证的任何 URL|
   |**使用 SSO 的应用**|最终用户设备上使用 SSO 有效负载的应用。|
   |**凭据续订证书**|如果使用证书进行身份验证，则选择作为身份验证证书部署给用户的 SCEP 或 PFX 证书。|

以下各节详细介绍了每个 SSO 字段。

### <a name="username-attribute-from-aad-and-realm"></a>来自 AAD 和领域的用户名属性

- 如果对此字段选择了“用户主体名称”，则按如下方式进行分析：

   ![用户名属性](media/User-name-attribute.png)

   还可以选择使用在“领域”文本框中键入的文本覆盖该领域。

   例如，Contoso 可能有几个子区域，如欧洲、亚洲和北美。 它们可能希望其亚洲用户使用 SSO 有效负载，并且该应用要求 UPN 采用 username@asia.contoso.com 格式。在此情况下，如果选择“用户主体名称”，则每个用户的领域默认是从 AAD 中获取的，该领域可能只是 contoso.com。因此，可以专为亚洲用户创建此有效负载并使用值 asia.contoso.com 覆盖领域。现在，最终用户的 UPN 会变为 username@asia.contoso.com，而不再是 username@contoso.com。

- 如果选择“设备 ID”，则 Intune 会自动选择 Intune 设备 ID。

   默认情况下，应用只需使用设备 ID。 但如果应用使用除设备 ID 以外的领域，则可在“领域”文本框中键入该领域。

   > [!NOTE]
   > 如果使用设备 ID，则默认将领域留空。

### <a name="url-prefixes-that-will-use-single-sign-on"></a>使用 SSO 的 URL 前缀

在此处键入组织中存在的、要求用户进行身份验证的任何 URL。

例如，用户连接到任何这些站点时，iOS 设备会使用 SSO 凭据，而用户不需要输入任何其他凭据。 但是，如果已启用多重身份验证，则用户必须输入第二重身份验证。

> [!NOTE]
> 这些 URL 必须采用正确格式化的 FQDN。 Apple 要求这些 URL 采用 `http://<yourURL.domain>` 格式

匹配模式的 URL 必须以 `http://` 或 `https://` 开头。 系统将执行简单的字符串匹配，因此 URL 前缀 `http://www.contoso.com/` 与 `http://www.contoso.com:80/` 不匹配。 但是，在 iOS 9.0 或更高版本中，单个通配符 \* 可用于指定所有匹配的值。 例如，`http://*.contoso.com/` 同时匹配 `http://store.contoso.com/` 和 `http://www.contoso.com`。
模式 `http://.com` 和 `https://.com` 分别匹配所有的 HTTP 和 HTTPS URL。

### <a name="apps-that-will-use-single-sign-on"></a>使用 SSO 的应用

指示最终用户设备上可使用 SSO 有效负载的应用。

`AppIdentifierMatches` 数组必须包含与应用程序包 ID 匹配的字符串。 这些字符串可以是完全匹配项（例如：`com.contoso.myapp`），也可以通过使用 \* 通配符指定捆绑 ID 的前缀匹配项。 通配符必须位于句点字符 (.) 后，并可能只在字符串末尾出现一次（例如：`com.contoso.*`）。 如果包括通配符，则程序包 ID 以前缀开头的任何应用都将被授予对帐户的访问权限。

“应用名称”字段用于添加一个用户友好名称，帮助识别程序包 ID。

### <a name="credential-renewal-certificate"></a>凭据续订证书

如果使用证书（而非密码）对最终用户进行身份验证，则使用此字段选择作为身份验证证书部署给用户的 SCEP 或 PFX 证书。 通常，这是针对其他配置文件（例如 VPN、Wi-Fi 或电子邮件）部署给用户的相同证书。

## <a name="next-steps"></a>后续步骤

有关其他设备功能配置信息，请参阅[如何在 Microsoft Intune 中配置设备功能设置](device-features-configure.md)。
