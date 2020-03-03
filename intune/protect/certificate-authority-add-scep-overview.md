---
title: 在 Microsoft Intune 中使用第三方证书颁发机构 (CA) 和 SCEP - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，可以添加供应商或第三方证书颁发机构 (CA)，以使用 SCEP 协议向移动设备颁发证书。 在此概述中，Azure Active Directory (Azure AD) 应用程序授予了 Microsoft Intune 验证证书的权限。 然后，在 SCEP 服务器的安装程序中使用 AAD 应用程序的应用程序 ID、身份验证密钥和租户 ID 来颁发证书。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85aac54a81d81dc138dd12612db183aae839b72b
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77575981"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>使用 SCEP 在 Intune 中添加合作伙伴证书颁发机构

将第三方证书颁发机构 (CA) 与 Intune 配合使用。 第三方 CA 可以使用简单证书注册协议 (SCEP) 向移动设备预配新证书或续订证书，并且可以支持 Windows、iOS/iPadOS、Android 和 macOS 设备。

使用此功能分两个部分：开源代码 API 和 Intune 管理员任务。

**第 1 部分 - 使用开源代码 API**  
Microsoft 创建了与 Intune 集成的 API。 通过该 API，可验证证书、发送成功或失败通知，以及使用 SSL（特别是 SSL 套接字工厂）与 Intune 进行通信。

[Intune SCEP API 公共 GitHub 存储库](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)中提供了该 API，你可以下载和在解决方案中使用。 SCEP 向设备预配证书之前，将此 API 与第三方 SCEP 服务器配合使用，以针对 Intune 运行自定义质询验证。

[与 Intune SCEP 管理解决方案集成](scep-libraries-apis.md)可提供有关使用 API、其方法以及测试构建的解决方案的详细信息。

**第 2 部分 - 创建应用程序和配置文件**  
使用 Azure Active Directory (Azure AD) 应用程序，可以将权限委托给 Intune 来处理来自设备的 SCEP 请求。 Azure AD 应用程序包括在开发者创建的 API 解决方案中使用的应用程序 ID 和身份验证密钥值。 然后，管理员使用 Intune 创建和部署 SCEP 证书配置文件，从而可以在设备上查看有关部署状态的报表。

本文从管理员角度概述了此功能，包括创建 Azure AD 应用程序。

## <a name="overview"></a>概述

以下步骤概述了如何在 Intune 中使用 SCEP 证书：

1. 在 Intune 中，管理员创建 SCEP 证书配置文件，然后将用户或设备作为此配置文件的目标。
2. 设备签入到 Intune。
3. Intune 会创建唯一的 SCEP 质询。 它还会添加其他完整性检查信息，例如预期的主题和 SAN 应该如何。
4. Intune 会对质询和完整性检查信息进行加密和签名，然后使用 SCEP 请求将此信息发送到设备。
5. 设备根据从 Intune 推送的 SCEP 证书配置文件在设备上生成证书签名请求 (CSR) 和公钥/私钥对。
6. 向第三方 SCEP 服务器终结点发送 CSR 和已加密/签名的质询。
7. SCEP 服务器会将 CSR 和质询发送到 Intune。 然后，Intune 会验证签名，解密有效负载，并将 CSR 与完整性检查信息进行比较。
8. Intune 会向 SCEP 服务器发回响应，并说明质询验证是否成功。  
9. 如果质询验证成功，则 SCEP 服务器会向设备颁发证书。

下图显示了第三方 SCEP 与 Intune 集成的详细流程：

> [!div class="mx-imgBorder"]
> ![第三方认证机构 SCEP 与 Microsoft Intune 集成的方式](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>设置第三方 CA 集成

### <a name="validate-third-party-certification-authority"></a>验证第三方证书颁发机构

在将第三方证书颁发机构与 Intune 集成之前，请确认使用的 CA 支持 Intune。 [第三方 CA 合作伙伴](#third-party-certification-authority-partners)（在本文中）包含列表。 还可以查看证书颁发机构的指南以获取详细信息。 CA 可能包括特定于其实现的设置说明。

### <a name="authorize-communication-between-ca-and-intune"></a>授权 CA 与 Intune 之间的通信

要允许第三方 SCEP 服务器使用 Intune 运行自定义质询验证，请在 Azure AD 中创建应用。 此应用对 Intune 授予委托权限以验证 SCEP 请求。

确保具有注册 Azure AD 应用所需的权限。 请参阅 Azure AD 文档中的[所需权限](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)。

#### <a name="create-an-application-in-azure-active-directory"></a>在 Azure Active Directory 中创建应用程序  

1. 在 [Azure 门户](https://portal.azure.com)中转到“Azure Active Directory” > “应用注册”，然后选择“新建注册”    。  

2. 在“注册应用程序”  页上，指定以下详细信息：  
   - 在“名称”  部分中，输入一个有意义的应用程序名称。  
   - 对于“支持的帐户类型”  部分，选择“任何组织目录中的帐户”  。  
   - 对于“重定向 URI”  ，保留 Web 的默认值，然后指定第三方 SCEP 服务器的登录 URL。  

3. 选择“注册”  以创建应用程序并打开新应用的“概述”页。  

4. 在应用的“概述”  页上，复制“应用程序(客户端)ID”  值并记录该值以供将来使用。 稍后将需要此值。  

5. 在应用的导航窗格中，转到“管理”下的“证书和密码”   。 选择“新建客户端密码”  按钮。 在“说明”中输入值，选择“截止期限”的任何选项  ，然后选择“添加”  以生成客户端密码的值  。 
   > [!IMPORTANT]  
   > 在离开此页面之前，使用第三方 CA 实现复制客户端密码的值并记录该值以供将来使用。 不再显示此值。 请务必查看有关他们希望如何配置应用程序 ID、身份验证密钥和租户 ID 的第三方 CA 指南。  

6. 记录租户 ID  。 租户 ID 是帐户中 @ 符号后面的域文本。 例如，如果帐户是 *admin@name.onmicrosoft.com* ，则租户 ID 是 name.onmicrosoft.com  。  

7. 在应用的导航窗格中，转到“管理”下的“API 权限”   ，然后选择“添加权限”  。  

8. 在“请求获取 API 权限”  页上，选择“Intune”  ，然后选择“应用程序权限”  。 选中 scep_challenge_provider  对应的复选框（SCEP 质询验证）。  

   选择“添加权限”  以保存此配置。  

9. 停留在“API 权限”  页上，然后依次选择“为 Microsoft 授予管理员同意”  、“是”  。  
   
   将完成 Azure AD 中的应用注册过程。





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>配置和部署 SCEP 证书配置文件
以管理员身份创建针对用户或设备的 SCEP 证书配置文件。 然后，分配配置文件。

- [创建 SCEP 证书配置文件](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [分配证书配置文件](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>删除证书

取消注册或擦除设备时，会删除证书。 不会撤销证书。

## <a name="third-party-certification-authority-partners"></a>第三方证书颁发机构合作伙伴
以下第三方证书颁发机构支持 Intune：

- [Entrust Datacard](https://go.entrustdatacard.com/pki/intune/)
- [EJBCA GitHub 开放源代码版本](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

如果第三方 CA 有兴趣将产品与 Intune 集成，请查看 API 指南：

- [Intune SCEP API GitHub 存储库](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [适用于第三方 CA 的 Intune SCEP API 指南](scep-libraries-apis.md)

## <a name="see-also"></a>另请参阅

- [配置证书配置文件](certificates-scep-configure.md)
- [Intune SCEP API GitHub 存储库](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [适用于第三方 CA 的 Intune SCEP API 指南](scep-libraries-apis.md)
