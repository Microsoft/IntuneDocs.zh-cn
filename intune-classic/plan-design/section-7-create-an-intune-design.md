---
title: "创建 Intune 设计 | Microsoft Docs"
description: "本文可帮助为 Microsoft Intune 仅限云设计和实现创建设计。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b39076aad873b9e4d0a5e128a76b189ac0ec2008
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="create-an-intune-design"></a>创建 Intune 设计

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本指南的此节应与第 2 节中的其他主题并行使用。 此设计基于正在收集的信息以及为完成本指南之前的部分将制定的决策。 在此设计部分中，我们的重点是独立 Intune，它是一个基于 Microsoft 云的服务。

虽然存在最低的本地基础结构要求，但仍需进行设计规划以确保拥有满足目标、目的和要求的正确移动设备管理解决方案。

此外，在实现和测试阶段常常有设计更改，请务必记录这些更改以及进行更改背后的依据。 我们将讨论以下几个方面：

-   当前环境

-   Intune 部署选项

-   确定外部依赖关系的要求

-   设备平台注意事项

-   进行传递的要求  

让我们更详细地研究一下各个方面。 

## <a name="record-your-environment"></a>记录环境

第一步是记录当前环境，然后才可以创建设计。 当前环境可能会影响设计决策，并且应在制定其他 Intune 设计决策时进行记录和引用。 以下是如何记录当前环境的几个示例：

-   **云中的标识**

    -   是否使用 DirSync 或 Azure Active Directory (AAD) Connect？

    -   环境是否进行了联合？

    -   是否启用了多重身份验证？

-   **电子邮件环境**

    -   是否正在使用 Exchange，它是在本地还是在云中？

    -   是否正在进行将 Exchange 迁移到云这一项目？

-   **当前 MDM 解决方案**

    -   当前是否在使用其他 MDM 解决方案？

    -   正在对企业和 BYOD 用例场景使用什么 MDM 解决方案？

    -   正在使用哪些功能（例如应用设备设置、Wi-Fi 配置等）？

    -   支持哪些设备平台？

    -   哪些组以及有多少用户正在使用 MDM 解决方案？

-   **证书解决方案**

    -   是否已实施证书解决方案？

    -   使用了哪种类型的证书？

-   **系统管理**

    -   如何管理电脑和服务器环境？

    -   是否正在使用 System Center Configuration Manager？ 是否正在使用第三方系统管理平台？

-   **VPN 解决方案**

    -   你的 VPN 解决方案是什么？

    -   是否将其同时用于公司和 BYOD 用例场景？

请务必将任何项目或任何其他计划记录到位，以在记录当前 MDM 环境时可对环境进行更改。 下面是一种记录当前环境的方法示例，可在创建 Intune 设计时提供帮助：

| **解决方案领域** | **当前环境** | **注释** |
|:---:|:---:|:---:|
| **标识** | Azure AD、Azure AD Connect、未联合、无 MFA | 项目就绪以在年底前启用 MFA |                 
| **电子邮件环境** | Exchange 内部部署、Exchange Online | 当前正在从 Exchange 内部部署迁移至 Exchange Online。 75% 的邮箱已迁移。 Intune 试点开始之前，将迁移最后的 25%。 |                
| **SharePoint** | 本地 SharePoint | 没有移动到 SharePoint Online 的计划 |  
| **当前 MDM** | Exchange ActiveSync |  |
| **证书解决方案** | Microsoft Server 2012 R2、AD 证书服务 | 仅对 Web 站点服务器使用 PKI |
| **系统管理** | System Center Configuration Manager CB 1606 | 想要了解 Intune 混合解决方案 |
| **VPN 解决方案** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>选择 Intune 部署选项

Intune 提供两个部署选项：独立和混合。 需要决定哪一个适合你的业务需求。 “独立”是指在云中运行的 Intune 服务，“混合”是指 Intune 与 System Center Configuration Manager 的集成。

- 详细了解[在 Microsoft Intune 独立移动设备管理和结合 System Center Configuration Manager 使用的混合移动设备管理之间进行选择](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Intune 租户位置

如果组织拥有全球布局，请确保订阅服务时规划租户所在的位置。 首次注册 Intune 订阅并映射到下面所列的全球各地区域时，将定义国家/地区：

-   北美

-   欧洲、中东和非洲

-   亚太地区

>[!IMPORTANT]
> 之后不能更改国家（地区）/租户位置。

## <a name="external-dependencies"></a>外部依赖关系

外部依赖关系指独立于 Intune 的服务和产品，但要么是 Intune 的要求，要么可能与 Intune 集成。 请务必确定任何外部依赖关系的要求及其配置方式。 下面列出了一些常见的外部依赖关系示例。

-   标识

-   用户和设备组

-   PKI

接下来我们详细探讨一下这些常见的外部依赖关系

### <a name="identity"></a>标识

我们使用标识来确定属于你的组织并注册了设备的用户。 Intune 要求 Azure Active Directory (Azure AD) 作为用户标识提供者。 如果已使用此服务，将能够利用云中已有的标识。 此外，推荐使用 Azure AD Connect 工具将本地用户标识与 Microsoft 云服务同步。 如果组织已在使用 Office 365，则 Intune 务必使用相同的 Azure Active Directory 环境。

可在下方找到有关 Intune 的标识要求的详细信息。

-   了解有关[标识要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)的详细信息。

-   了解有关[目录同步要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)的详细信息。

-   了解有关[多重身份验证要求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)的详细信息。

### <a name="user-and-device-groups"></a>用户和设备组

用户和设备组确定部署的目标。 这可能包括面向策略、应用程序和配置文件的部署。 Intune 仅限云支持用户和设备组 - 需确定将需要哪些用户和设备组。 建议在本地 Active Directory 中创建所有组，然后将组同步到 Azure Active Directory。 可在下方找到有关用户和设备组规划和创建的详细信息。

-   了解有关[规划用户和设备组](/intune-classic/deploy-use/plan-your-user-and-device-groups)的详细信息。

-   了解[如何创建用户和设备组](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。

### <a name="public-key-infrastructure-pki"></a>公钥基础结构 (PKI)

公钥基础结构向设备或用户提供证书，以安全地对服务进行身份验证。 Intune 支持 Microsoft PKI 基础结构。 设备和用户证书可颁发给移动设备，以满足基于证书的身份验证要求。 实现证书前，需确定是否需要证书、网络基础结构是否可支持基于证书的身份验证，以及当前是否正在现有环境中使用证书。

如果打算通过 Intune 将证书与 VPN、Wi-Fi 或电子邮件配置文件结合使用，需确保具有支持的 [PKI 基础结构](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)，且准备好创建和部署证书配置文件。

此外，如果要颁发 SCEP 证书，则需确定将托管网络设备注册服务 (NDES) 功能的服务器，以及通信的发生方式。

有关在 Intune 中配置证书的详细信息，请参阅：

-   [如何配置 SCEP 证书基础结构](/intune-classic/deploy-use/configure-certificate-infrastructure-for-scep)。

-   [如何配置 PFX 证书基础结构](/intune-classic/deploy-use/configure-certificate-infrastructure-for-pfx)。

-   [如何配置 Intune 证书配置文件](/intune-classic/deploy-use/configure-intune-certificate-profiles)。

-   [如何配置资源访问策略](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。

## <a name="device-platform-considerations"></a>设备平台注意事项

要了解设备如何正常运行，需要深入了解设备。

-   确定支持的设备平台

-   设备

-   设备所有权

-   批量注册

让我们更详细地研究一下这些方面。

### <a name="determine-supported-device-platforms"></a>确定支持的设备平台

需要知道哪些设备将存在于环境中，以及创建设计时验证它们是否受 Intune 支持。 Intune 支持 iOS、Android 和 Windows 平台。

-   了解有关 [Intune 支持的设备](/intune-classic/get-started/supported-mobile-devices-and-computers)的详细信息。

### <a name="devices"></a>设备

Intune 管理移动设备以保护公司数据的安全，并允许最终用户从多个位置工作。 Intune 支持多个设备平台，因此我们建议记录组织设计中支持的那些设备和 OS 平台。 这其中就包括“用例要求”一节中创建的设备和平台。

还建议按 OS 平台和版本检查设备功能时，知晓要引用列表的版本。 下面提供了一个示例：

| **设备平台** | **OS 版本** |
|:---:|:---:|
| iOS - iPhone | 9.0+ |                
| iOS - iPad | 8.0+ |               
| Android - Samsung KNOX 标准版 | 4.0+ |
| Windows 10 平板电脑 | 10+ |

### <a name="device-ownership"></a>设备所有权

Intune 支持公司拥有和 BYOD 所有权。 如果设备由设备注册管理器或设备注册计划注册，则该设备被视为公司拥有。 例如，设备可通过 Apple DEP 进行注册，被标记为“公司”并置于接收目标企业策略和应用的设备组中。

请参阅[第 3 部分：确定用例场景要求](section-3-determine-use-case-requirements.md)，了解有关公司和 BYOD 用例的详细信息。

### <a name="bulk-enrollment"></a>批量注册

在 Intune 中注册设备有多个注册选项可用，以作为通过公司门户进行自助式注册的补充。 批量注册可通过多种不同方式完成，具体取决于平台。 如果需要批量注册，首先需确定批量注册方法，并将该方法纳入设计中。 在下方查找有关不同的批量注册方法的详细信息。

-   了解有关[批量注册](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)的详细信息。

## <a name="feature-requirements"></a>功能要求

在这些部分中，我们将了解以下符合用例场景要求的特性和功能：

-   条款和条件策略

-   配置策略

-   资源配置文件

-   应用

-   合规性策略

-   条件性访问

让我们更详细地研究一下各个方面。

### <a name="terms-and-conditions-policies"></a>条款和条件策略

条款和条件可用于解释最终用户在注册前必须接受的策略或条件。 Intune 支持向用户组添加和部署多个条款和条件策略的功能。 需确定是否需要条款和条件策略。 如果需要，谁将负责在组织中提供此信息。

-   了解在 Intune 上[如何创建条款和条件策略](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)。 下面是一个如何记录条款和条件策略的示例。

| **条款和条件名称** | **用例** | **目标组** |
|:---:|:---:|:---:|
| 公司条款和条件 | 企业 | 公司用户 |                 
| BYOD 条款和条件 | BYOD | BYOD 用户 |                

### <a name="configuration-policies"></a>配置策略

配置策略用于管理设备上的安全设置和功能。 设计配置策略时，请参阅用例要求部分，确定 Intune 设备所需的配置。 记录哪些设置以及应如何配置它们，同时记录它们将面向哪些用户或设备组。

每个平台应至少创建一个配置策略。 如果需要，每个平台可创建多个配置策略。 下面是一个针对不同平台和用例场景设计 4 个不同配置策略的示例。

| **策略名称** | **设备平台** | **设置** | **目标组** |   
|:---:|:---:|:---:|:---:|
| 公司 - iOS | iOS | PIN 必需，长度为 6，限制云备份 | 公司设备 |                                                           
| 公司 - Android | Android | PIN 必需，长度为 6，限制云备份 | 公司设备 |                                                           
| BYOD - iOS  | iOS | PIN 必需，长度为 4 | BYOD 设备 |
| BYOD - Android  | Android | PIN 必需，长度为 4 | BYOD 设备 |

### <a name="profiles"></a>Profiles

配置文件用于帮助最终用户连接到公司数据。 Intune 支持许多类型的配置文件。 请参阅用例和要求，确定何时配置[配置文件](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。 所有设备配置文件按平台类型进行分类，且应包含在设计文档中。

-   证书配置文件

-   Wi-Fi 配置文件

-   VPN 配置文件

-   电子邮件配置文件

让我们更详细地研究一下每种类型的配置文件。

##### <a name="certificate-profiles"></a>证书配置文件

证书配置文件允许 Intune 向用户或设备颁发证书。 Intune 支持以下项：

-   简单证书注册协议 (SCEP)

-   受信任的根证书

-   PFX 证书。

建议记录哪些用户组需要证书、需要多少证书配置文件，以及将它们部署到哪些用户组。

>[!NOTE]
> 请记住，SCEP 证书需要受信任的根证书，因此请确保 SCEP 证书的所有目标用户同时接收受信任的根证书。 如果需要 SCEP 证书，设计并记录需要什么 SCEP 证书模板。

下面是一个如何在设计过程中记录证书的示例：

| **类型** | **配置文件名称** | **设备平台** | **用例** |   
|:---:|:---:|:---:|:---:|
| 根 CA | 企业根 CA | Android、iOS、Windows Mobile | 公司、BYOD  |                                                           
| SCEP | 用户证书 | Android、iOS、Windows Mobile | 公司、BYOD |                                                           

##### <a name="wi-fi-profile"></a>Wi-Fi 配置文件

Wi-Fi 配置文件用于自动将移动设备连接到无线网络。 Intune 支持将 Wi-Fi 配置文件部署到所有支持的平台。

-   详细了解 [Intune 如何支持 Wi-fi 配置文件]/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)。

下面是一个 Wi-Fi 配置文件设计的示例：

| **类型** | **配置文件名称** | **设备平台** | **用例** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | 亚洲 Wi-Fi 配置文件 | Android | 公司、BYOD（亚洲地区）|                                                           
| Wi-Fi | 北美 Wi-Fi 配置文件 | Android、iOS、Windows 10 移动版 | 公司、BYOD（北美地区） |                                                           

##### <a name="vpn-profile"></a>VPN 配置文件

VPN 配置文件让用户可以安全地从远程位置访问网络。 Intune 支持来自本机移动 VPN 连接和第三方供应商的 VPN 配置文件。

-   了解有关 [Intune 支持的 VPN 配置文件和供应商](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)的详细信息。

下面是一个记录 VPN 配置文件设计的示例。

| **类型** | **配置文件名称** | **设备平台** | **用例** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco AnyConnect 配置文件 | Android、iOS、Windows 10 移动版 | 公司、BYOD（北美和德国）|                                                           
| VPN | 脉冲安全 | Android | 公司、BYOD（亚洲地区） |                                                           

##### <a name="email-profile"></a>电子邮件配置文件

电子邮件配置文件允许电子邮件客户端自动通过连接信息进行安装，并设置电子邮件配置。 Intune 在某些设备上支持电子邮件配置文件。

-   了解有关[电子邮件配置文件](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)以及支持哪些平台的详细信息。

下面是一个记录电子邮件配置文件设计的示例：

| **类型** | **配置文件名称** | **设备平台** | **用例** |   
|:---:|:---:|:---:|:---:|
| 电子邮件配置文件 | iOS 电子邮件配置文件 | iOS | 公司 - 信息工作者 BYOD |                                                           
| 电子邮件配置文件 | Android Knox 电子邮件配置文件 | Android Knox | BYOD |

### <a name="apps"></a>应用

Intune 支持以多种方式向用户或设备传递应用。 传递的应用程序类型可能是软件安装程序应用、来自公共应用商店的应用、来自外部链接的应用或托管 iOS 应用。 除了单个应用部署，还可通过适用于 iOS 和 Windows 的批量采购计划管理和部署批量采购的应用。 下面是有关 Intune 如何支持应用和批量采购计划的详细信息。

-   了解有关[应用的类型](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)的详细信息

-   详细了解 [适用于企业的 iOS 批量采购计划 /intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune))。

-   了解有关[适用于企业的 Windows 应用商店](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)的详细信息。

#### <a name="app-type-requirements"></a>应用类型要求

由于可将应用部署到用户和设备，因此建议确定哪些应用程序将由 Intune 管理。 收集列表的同时，请尝试回答以下问题：

-   这些应用是否需要与云服务集成？

-   是否向 BYOD 用户提供所有应用？

-   这些应用的可用部署选项有哪些？

-   贵公司是否需要为合作伙伴提供对服务型软件 (SaaS) 应用数据的访问权限？

-   这些应用是否需要从用户设备访问 Internet？

-   这些应用是否在应用商店中公开提供？或者它们是否为自定义业务线应用？


>[!TIP]
> 查看 [Intune 支持的不同应用程序类型](/intune-classic/deploy-use/add-apps)。

#### <a name="app-protection-policies"></a>应用保护策略

应用程序保护策略通过定义应用程序管理公司数据的方式最大限度地减少数据丢失。 Intune 对任何为与移动应用管理搭配使用而构建的应用程序支持应用保护策略。 设计应用保护策略时，需确定将对给定应用中的公司数据设置什么限制。 建议查看[应用保护策略](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)如何运作。 下面是一个如何记录现有应用程序以及需要何种保护的示例。

| **应用程序** | **目的** | **平台** | **用例** | **应用保护策略** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 可用 | iOS | 公司 - 高级管理人员 | 不能越狱，加密文件 |                                                         
| Word | 可用 | iOS、Android - Samsung Knox、非 Knox、Windows 10 移动版 | 公司、BYOD | 不能越狱，加密文件 |                                                         

#### <a name="compliance-policies"></a>相容性策略

合规性策略确定设备是否满足某些要求。 Intune 使用合规性策略确定设备是否被为合规。 然后，合规性状态可用于限制对公司资源的访问。 如果需要条件性访问，建议设计[设备合规性策略](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)。 请参阅要求和用例，确定需要多少设备合规性策略，以及哪些用户组是目标用户组。 此外，还需要确定设备被视为不合规前，在未签入的状态下它可处于脱机状态的时长。

下面是如何设计合规性策略的示例：

| **策略名称** | **设备平台** | **设置** | **目标组** |   
|:---:|:---:|:---:|:---:|
| 合规性策略 | iOS、Android - Samsung Knox、非 Knox、Windows 10 移动版 | PIN - 必需，不能越狱 | 公司、BYOD |

#### <a name="conditional-access-policies"></a>条件性访问策略

条件性访问用于仅允许合规设备访问公司资源。 Intune 配合整个企业移动性 + 安全 (EMS) 工作，控制对公司资源的访问。 需确定条件性访问是否必需以及必须保护的内容。

-   了解有关[条件性访问](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)的详细信息。

对于联机访问，需确定条件性访问策略的目标平台和用户组。

此外，还需确定是否需要为 Exchange Online 或 Exchange 内部部署安装/配置 Intune 服务间连接器。

了解如何安装和配置 Intune 服务间连接器：

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange 内部部署](/intune-classic/deploy-use/intune-on-premises-exchange-connector)

下面是一个如何记录条件性访问策略的示例：

| **服务** | **新式验证平台** | **基本身份验证** | **用例** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | 在受 Intune 支持的平台上阻止不合规设备 | 公司、BYOD |
| SharePoint Online | iOS、Android |  | 公司、BYOD |

## <a name="next-section"></a>下一节

下一节提供 [Intune 实现过程](section-8-onboarding-process.md)的相关指南。

