---
title: 在 Microsoft Intune 中使用移动设备的派生凭据 - Azure | Microsoft Docs
description: 将移动设备上的派生凭据用作 Intune VPN、电子邮件、Wi-Fi 配置文件、应用程序以及 S/MIME 和加密的身份验证方法。 派生凭据是 NIST 《特殊出版物 800-157》准则的实现。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4d0772f9a0afce0607d0193bfb82ea6bd22709d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73445319"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>在 Microsoft Intune 中使用派生凭据

本文适用于运行 iOS 的设备 

在需要通过智能卡进行身份验证或加密和签名的环境中，现可以使用 Intune 为移动设备预配派生自用户智能卡的证书。 该证书称为派生凭据  。 Intune [支持多个派生凭据颁发者](#supported-issuers)，但每次每个租户只能应用一个颁发者。

派生凭据实现美国国家标准与技术研究院 (NIST) 关于派生个人身份验证 (PIV) 凭据的准则（属于《特殊出版物 (SP) 800-157》）。

**借助 Intune 的实现**：

- Intune 管理员将其租户配置为应用受支持派生凭据颁发者。 无需在派生凭据颁发者的系统中配置任何 Intune 特定设置。

- Intune 管理员将“派生凭据”指定为以下对象的身份验证方法   ：

  - Wi-Fi、VPN 和电子邮件（其中包括 iOS 本机邮件应用）等常见配置文件类型

  - 应用身份验证

  - S/MIME 签名和加密

- 用户在计算机上使用智能卡获取派生凭据，以便向派生凭据颁发者进行身份验证。 然后，颁发者将派生自其智能卡的凭据颁发给移动设备。

- 设备收到派生凭据之后，在应用或资源访问配置文件需要派生凭据时，使用它进行身份验证以及 S/MIME 签名和加密。 

## <a name="prerequisites"></a>必备条件

将租户配置为使用派生凭据之前，请查看以下信息。

### <a name="supported-platforms"></a>受支持的平台

Intune 支持以下 OS 平台上的派生凭据：

- iOS/iPadOS

### <a name="supported-issuers"></a>支持的颁发者

Intune 支持每个租户一个派生凭据颁发者。 可以将 Intune 配置为应用以下颁发者：

- **DISA Purebred**： https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**： https://www.entrustdatacard.com/
- **Intercede**： https://www.intercede.com/

有关应用不同颁发者的关键详细信息，请查看该颁发者的指南<!-- , including the issuers end-user workflow-->。 更多信息，请参阅本文中的[派生凭据计划](#plan-for-derived-credentials)。

> [!IMPORTANT]  
> 如果删除租户中的派生凭据颁发者，则通过该颁发者设置的派生凭据将会失效。
>
> 请参阅下文的[更改派生凭据颁发者](#change-the-derived-credential-issuer)。

### <a name="company-portal-app"></a>公司门户应用

计划在将注册派生凭据的设备上部署 Intune 公司门户应用。 设备用户使用公司门户应用来开始凭据注册流程。

对于 iOS 设备，请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)。

## <a name="plan-for-derived-credentials"></a>派生凭据计划

设置派生凭据颁发者之前，请了解以下注意事项。

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) 查看所选派生凭据颁发者的文档  

配置颁发者之前，查看该颁发者的文档，以了解其系统如何将派生凭据交付设备。

根据所选颁发者，注册时可能需要工作人员帮助用户完成该流程。 还应查看当前的 Intune 配置，以确保其不会阻止设备或用户完成凭据请求所需的访问。

例如，可以使用条件访问来阻止通过不合规设备访问电子邮件。 如果依靠电子邮件通知来告知用户开始派生凭据注册流程，则用户可能只有在符合策略之后才会收到这些说明。

同样，部分派生凭据请求工作流需要使用设备摄像头来扫描屏幕上的 QR 码。 此代码将该设备链接到针对具有用户智能卡凭据的派生凭据颁发者所发出的身份验证请求。 如果设备配置策略禁止使用摄像头，则用户将无法完成派生凭据注册请求。

常规信息：

- 每次只能为每个租户配置一个颁发者，该颁发者将适用于租户中的所有用户和受支持设备。

- 向用户应用要求提供派生凭据的策略时，才会通知用户必须注册派生凭据。

- 可以通过公司门户的应用通知和/或电子邮件进行通知。 如果选择使用电子邮件通知并启用了条件访问，则设备不合规的用户可能不会接收到电子邮件通知。

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) 查看所选颁发者的最终用户工作流

下面是每个受支持合作伙伴的关键注意事项。  了解这些信息，以确保 Intune 策略和配置不会阻止用户和设备成功注册该颁发者的派生凭据。

#### <a name="disa-purebred"></a>DISA Purebred

查看 [DISA Purebred 的用户工作流](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred)。 此工作流的关键要求包括以下内容：

- 用户需要访问可在其中使用智能卡向颁发者进行身份验证的计算机或网亭。

- 将注册派生凭据的设备必须安装 Intune 公司门户应用。

- 使用 Intune 在将注册派生凭据的设备上[部署 DISA Purebred 应用](#deploy-the-disa-purebred-app)。 必须通过 Intune 部署此应用，以便进行管理，并使其可与 Intune 公司门户应用配合使用。 设备用户使用此应用来完成派生凭据请求。

- DISA Purebred 应用需要[按应用的 VPN](../configuration/vpn-settings-configure.md)，以确保应用在注册派生凭据期间可以访问 DISA Purebred。

- 设备用户在注册流程中必须使用实时代理。 用户在注册流程中会收到限时的一次性密码。

有关获取和配置 DISA Purebred 应用的信息，请参阅下文的[部署 DISA Purebred 应用](#deploy-the-disa-purebred-app)。

#### <a name="entrust-datacard"></a>Entrust Datacard

查看 [Entrust Datacard 的用户工作流](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard)。 此工作流的关键要求包括以下内容：

- 用户需要访问可在其中使用智能卡向颁发者进行身份验证的计算机或网亭。

- 将注册派生凭据的设备必须安装 Intune 公司门户应用。

- 使用设备相机扫描 QR 码，该 QR 码会将身份验证请求链接到移动设备的派生凭据请求。

#### <a name="intercede"></a>Intercede

查看 [Intercede 的用户工作流](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede)。 此工作流的关键要求包括以下内容：

- 用户需要访问可在其中使用智能卡向颁发者进行身份验证的计算机或网亭。

- 将注册派生凭据的设备必须安装 Intune 公司门户应用。

- 使用设备相机扫描 QR 码，该 QR 码会将身份验证请求链接到移动设备的派生凭据请求。

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) 将受信任的根证书部署到设备

将受信任的根证书与派生凭据一起使用，以验证派生凭据证书链是否有效且受信任。 即便策略不直接进行引用，也需要受信任的根证书。 请参阅[在 Microsoft Intune 中为设备配置证书配置文件](certificates-configure.md)。

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) 提供有关如何获取派生凭据的最终用户说明

创建指南，告知用户如何开始派生凭据注册流程，并引导其完成你所选择的颁发者的派生凭据注册工作流。

建议提供用于托管指南的 URL。 为租户配置派生凭据颁发者时指定此 URL，即可在公司门户应用中提供此 URL。 如果你不指定自己的 URL，Intune 将提供指向通用详细信息的链接。 这些详细信息无法涵盖所有方案，因此对你的环境而言可能并不准确。

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) 部署需要派生凭据的 Intune 策略

新建要求使用派生凭据的策略或编辑现有策略。 派生凭据取代了适用于应用身份验证、Wi-Fi、VPN、电子邮件以及 S/MIME 签名和加密的其他身份验证方法。

避免要求使用派生凭据来访问获取派生凭据的流程，因为这可能使用户无法完成请求。

## <a name="set-up-a-derived-credential-issuer"></a>设置派生凭据颁发者

创建要求使用派生凭据的策略之前，请在 Intune 控制台中设置凭据颁发者。 派生凭据颁发者是租户范围的设置。 租户在同一时间仅支持一个颁发者。

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转到“设备配置” > “派生凭据”   。

   ![在控制台中配置派生凭据](./media/derived-credentials/configure-provider.png)

2. 为派生凭据颁发者策略指定易记的显示名称  。  此名称不会向设备用户显示。

3. 对于“派生凭据颁发者”，选择已为租户选择的派生凭据颁发者  ：
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

4. 指定指向自定义说明所在位置的派生凭据帮助 URL，这些说明用于帮助用户获取组织的派生凭据  。 这些说明应特定于组织以及获取所选颁发者的凭据所必需的工作流。 该链接在公司门户应用中显示，且应能够通过设备进行访问。

   如果你不指定自己的 URL，Intune 将提供链接，指向无法涵盖所有场景的通用详细信息。 此通用指南对你的环境而言可能并不准确。

5. 选择一个或多个“通知类型”  。 通知类型是用于通知用户以下情况的方法：

   - 为设备注册颁发者以获取新的派生凭据。
   - 当前凭据将到期时，获取新的派生凭据。
   - 将派生凭据用于 Wi-Fi、VPN、电子邮件或应用身份验证以及 S/MIME 签名和加密的策略。

6. 准备就绪后，选择“保存”以完成派生凭据颁发者配置  。

保存配置之后，可以更改除“派生凭据颁发者”以外的所有字段  。  若要更改颁发者，请参阅[更改派生凭据颁发者](#change-the-derived-credential-issuer)。

## <a name="deploy-the-disa-purebred-app"></a>部署 DISA Purebred 应用

本部分仅在使用 DISA Purebred 时适用  。

若要采用 DISA Purebred 作为 Intune 的派生凭据颁发者，必须获取 DISA Purebred 应用，然后使用 Intune 将该应用部署到设备  。 设备用户使用其设备上的应用请求来自 DISA Purebred 的派生凭据。

除使用 Intune 部署应用以外，还要为 DISA Purebred 应用程序配置 Intune 按用用 VPN。

**完成以下任务**：
  
1. 下载 [DISA Purebred 应用程序](https://cyber.mil/pki-pke/purebred/)。
2. 在 Intune 中部署 DISA Purebred 应用程序。  请参阅[将 iOS 业务线应用添加到 Microsoft Intune](../apps/lob-apps-ios.md)。
3. 为 DISA Purebred 应用程序[创建按应用 VPN](../configuration/vpn-settings-configure.md)。

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>使用派生凭据进行身份验证以及 S/MIME 签名和加密

可以针对以下配置文件类型和用途指定派生凭据  ：

- [应用程序](#use-derived-credentials-for-app-authentication)
- [Email](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME 签名和加密](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  对于 Wi-Fi 配置文件，身份验证方法仅在 EAP 类型设置为以下值之一时可用   ：
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>使用派生凭据进行应用身份验证

使用派生凭据在网站和应用程序中进行基于凭据的身份验证。 若要提供派生凭据以进行应用身份验证，请在 Intune 控制台中执行以下步骤：  

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，转到“设备配置” > “配置文件”，然后选择“创建配置文件”    。

2. 为“名称”下的配置文件输入易记名称  。

3. 对于“平台”  ，请选择“iOS”  。

4. 对于“配置文件类型”，选择“派生凭据”   。

5. 选择“确定”，然后单击“创建”   。

6. 选择“分配”以选择应收到策略的组  。
 
根据你在设置派生凭据颁发者时指定的设置，用户将收到应用或电子邮件通知。 该通知告知用户启动公司门户，以便能够处理派生凭据策略。

## <a name="renew-a-derived-credential"></a>续订派生凭据

派生凭据无法续订或延期。 用户必须使用凭据请求工作流为其设备请求新的派生凭据。

如果为“通知类型”配置一个或多个方法，Intune 会在当前派生凭据的有效期限已使用 80％ 时自动通知用户  。 通知将指导用户完成凭据请求流程，以获取新的派生凭据。

设备收到新的派生凭据之后，使用派生凭据的策略将重新部署到该设备。


## <a name="change-the-derived-credential-issuer"></a>更改派生凭据颁发者

可以在租户级别更改凭据颁发者，但每个租户在同一时间只支持一个颁发者。

更改颁发者之后，系统将提示用户获取新颁发者的新派生凭据。 用户必须这样做才能使用派生凭据进行身份验证。

### <a name="change-the-issuer-for-your-tenant"></a>更改租户的颁发者

> [!IMPORTANT]  
> 如果在删除颁发者后立即重新配置同一颁发者，仍必须更新配置文件和设备以使用该颁发者的派生凭据。 删除颁发者之前获取的派生凭据将失效。

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转到“设备配置” > “派生凭据”   。

2. 选择“删除”以删除当前的派生凭据颁发者  。

3. 配置新的颁发者。

### <a name="update-profiles-that-use-derived-credentials"></a>更新使用派生凭据的配置文件

删除颁发者并添加新的颁发者之后，编辑使用派生凭据的每个配置文件。 即使还原之前的颁发者，此规则也适用。 对配置文件的任何编辑都会触发更新，包括对配置文件“说明”的简单编辑  。

### <a name="update-derived-credentials-on-devices"></a>更新设备上的派生凭据

删除颁发者并添加新的颁发者之后，设备用户必须请求新的派生凭据。 即使添加已删除的颁发者，此规则也适用。 请求新派生凭据的流程与注册新设备或更新现有凭据的流程相同。

## <a name="next-steps"></a>后续步骤

[创建设备配置文件](../configuration/device-profile-create.md)
