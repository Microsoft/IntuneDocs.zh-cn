---
title: 创建 Microsoft Intune 设计
titleSuffix: Microsoft Intune
description: 本文可帮助为 Microsoft Intune 仅限云设计和实现创建设计。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c18f3e8fb14d8592789b39856ec420790fad286
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547547"
---
# <a name="create-a-design"></a>创建设计

Intune 设计基于收集的信息以及完成[本指南其他部分](../planning-guide.md)后制定的决策。 它有助于将以下内容整合在一起：

- 当前环境

- Intune 部署选项

- 确定外部依赖关系的要求

- 设备平台注意事项

- 进行传递的要求  

虽然存在本地基础结构最低要求，但设计计划仍可帮助确保拥有适当的移动设备管理解决方案，用于满足目标、宗旨和要求。

让我们更详细地研究一下各个方面。 

## <a name="record-your-current-environment"></a>记录当前环境
此外，在实现和测试阶段常常有设计更改。 发生更改时，使用设计计划来记录这些更改，以及更改背后的基本原理。

当前环境可能会影响设计决策，并且应在制定其他 Intune 设计决策时进行记录和引用。 以下是如何记录当前环境的几个示例：

- **云中的标识**

  - 是否使用 DirSync 或 Azure Active Directory (Azure AD) Connect？

  - 环境是否进行了联合？

  - 是否启用了多重身份验证 (MFA)？

- **电子邮件环境**

  - 是否使用 Exchange？ 是位于本地还是云中？

  - 是否正在进行将 Exchange 迁移到云这一项目？

- **当前移动设备管理 (MDM) 解决方案**

  - 当前是否在使用其他 MDM 解决方案？

  - 正在对公司和 BYOD 用例场景使用什么 MDM 解决方案？

  - 正在使用哪些功能（例如应用设备设置、Wi-Fi 配置）？

  - 支持哪些设备平台？

  - 哪些组以及有多少用户正在使用 MDM 解决方案？

- **证书解决方案**

  - 是否已实施证书解决方案？

  - 使用了哪种类型的证书？

- **系统管理**

  - 如何管理电脑和服务器环境？

  - 是否正在使用 Microsoft 终结点管理器？ 是否正在使用第三方系统管理平台？

- **VPN 解决方案**

  - 你的 VPN 解决方案是什么？

  - 是否将其同时用于公司和 BYOD 用例场景？

请务必将任何项目或任何其他计划记录到位，在记录当前 MDM 环境时它们会影响环境。 下面的示例演示了在创建 Intune 设计时记录当前环境的一种方法：

| **解决方案领域** | **当前环境** | **注释** |
|---|---|---|
| **标识** | Azure AD、Azure AD Connect、未联合、无 MFA | 项目就绪以在年底前启用 MFA |                 
| **电子邮件环境** | Exchange 内部部署、Exchange Online | 当前正在从 Exchange 内部部署迁移至 Exchange Online。 75% 的邮箱已迁移。 Intune 试点开始之前，将迁移最后的 25%。 |                
| **SharePoint** | 本地 SharePoint | 没有移动到 SharePoint Online 的计划 |  
| **当前 MDM** | Exchange ActiveSync |  |
| **证书解决方案** | Microsoft Server 2012 R2、AD 证书服务 | 仅对 Web 站点服务器使用 PKI |
| **系统管理** | Configuration Manager CB 1606 | 想要了解 Intune 混合解决方案 |
| **VPN 解决方案** | Cisco AnyConnect |  |


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来制定 Intune 设计计划。

## <a name="choose-an-intune-deployment-option"></a>选择 Intune 部署选项

Intune 提供两个部署选项：独立和混合。 “独立”是指在云中运行的 Intune 服务，“混合”是指 Intune 与 Configuration Manager 的集成。 本指南主要用于使用独立选项。 [决定哪个选项适合你的业务需求](https://docs.microsoft.com/configmgr/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)。

> [!Important]
>已弃用载入新的混合 MDM 客户这一功能。 有关详细信息，请参阅博客文章[从混合移动设备管理移动到 Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)。


## <a name="intune-tenant-location"></a>Intune 租户位置

如果组织拥有全球布局，请确保在订阅服务时规划租户所在的位置。 国家/地区在你首次注册 Intune 订阅并映射到下面所列的全球各国家/地区时定义：

- 北美

- 欧洲、中东和非洲

- 亚太地区

>[!IMPORTANT]
> 之后便无法更改国家/地区和租户位置。

## <a name="external-dependencies"></a>外部依赖关系

外部依赖关系是指独立于 Intune 的服务和产品，但要么是 Intune 的要求，要么可能与 Intune 集成。 请务必确定任何外部依赖关系的要求及其配置方式。 下面是一些常见的外部依赖关系示例：

- 标识

- 用户和设备组

- 公钥基础结构 (PKI)

接下来，让我们详细探讨一下这些常见的外部依赖关系。

### <a name="identity"></a>标识

我们使用标识来确定属于你的组织并注册了设备的用户。 Intune 要求 Azure Active Directory (Azure AD) 作为用户标识提供者。 如果已使用此服务，则可使用云中已存在的标识。 此外，推荐使用 Azure AD Connect 工具将本地用户标识与 Microsoft 云服务同步。 如果组织已在使用 Office 365，请 Intune 务必使用相同的 Azure AD 环境。

详细了解以下 Intune 标识要求：

- [身份要求](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions)。

- [目录同步要求](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

- [多重身份验证要求](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)。

### <a name="user-and-device-groups"></a>用户和设备组

用户和设备组确定部署的目标，包括策略、应用程序和配置文件。 需要确定所需的用户和设备组。

建议在本地 Active Directory 中创建所有组，然后同步到 Azure AD。 详细了解用户和设备组的规划和创建：

- [规划用户和设备组](users-add.md)。

- [创建用户和设备组](groups-add.md)。

### <a name="public-key-infrastructure-pki"></a>公钥基础结构 (PKI)
公钥基础结构向设备或用户提供证书，以安全地对服务进行身份验证。 Intune 支持 Microsoft PKI 基础结构。 设备和用户证书可颁发给移动设备，以满足基于证书的身份验证要求。 使用证书前，需确定是否需要证书、网络基础结构是否可支持基于证书的身份验证，以及当前是否正在现有环境中使用证书。

如果打算通过 Intune 将证书与 VPN、Wi-Fi 或电子邮件配置文件结合使用，请确保已有支持的 [PKI 基础结构](../protect/certificates-configure.md)，且准备好创建和部署证书配置文件。

此外，如果要使用 SCEP 证书，则需确定将托管网络设备注册服务 (NDES) 功能的服务器，以及通信的发生方式。

了解详细信息：

- [如何配置 Intune 证书配置文件](../protect/certificates-configure.md)

- [如何配置 SCEP 证书基础结构](../protect/certificates-scep-configure.md)

- [如何配置 PFX 证书基础结构](../protect/certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>设备平台注意事项

深入研究设备的以下方面，了解如何正确管理设备。

- 受支持的设备平台

- 设备

- 设备所有权

- 批量注册

让我们更详细地研究一下这些方面。

### <a name="determine-supported-device-platforms"></a>确定支持的设备平台

需要知道哪些设备将存在于环境中，以及创建设计时验证它们是否受 Intune 支持。 Intune 支持 iOS、Android 和 Windows 平台。

[支持 Intune 的设备的完整列表](supported-devices-browsers.md)。

### <a name="devices"></a>设备

Intune 管理移动设备以保护公司数据的安全，并允许最终用户从多个位置工作。 Intune 支持许多设备平台，因此建议记录组织设计中将支持的设备、OS 平台和版本。 例如：

| **设备平台** | **OS 版本** |
|:---:|:---:|
| iOS - iPhone | 10.0+ |                
| iOS - iPad | 10.0+ |               
| Android - Samsung KNOX 标准版 | 4.0+ |
| Windows 10 平板电脑 | 10+ |


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来制定设备列表。
### <a name="device-ownership"></a>设备所有权

Intune 支持公司拥有的设备和个人设备。 如果设备由设备注册管理器或设备注册计划注册，则该设备被视为公司拥有。 例如，设备可通过 Apple 设备注册计划 (DEP) 注册，被标记为“公司”并置于接收目标公司策略和应用的设备组中。

请参阅[第 3 部分：确定用例方案要求](planning-guide-requirements.md)，详细了解公司和 BYOD 用例。

### <a name="bulk-enrollment"></a>批量注册

 可根据平台通过多种不同的方式批量注册设备。 如果需要批量注册，请首先[确定批量注册方法](../enrollment/device-enrollment.md)，并将该方法纳入设计中。

## <a name="feature-requirements"></a>功能要求

以下部分介绍了符合用例场景要求的一些特性和功能：

- 条款和条件策略

- 配置策略

- 资源配置文件

- 应用

- 合规性策略

- 条件性访问

让我们更详细地研究一下各个方面。

### <a name="terms-and-conditions-policies"></a>条款和条件策略

可使用[条款和条件](../enrollment/terms-and-conditions-create.md)来解释最终用户在注册其设备前必须接受的策略或条件。 Intune 支持向用户组添加和部署多个条款和条件策略的功能。

需确定是否需要条款和条件策略。 如果需要，谁将负责在组织中提供此信息。 下面是一个如何记录条款和条件策略的示例。

| **条款和条件名称** | **用例** | **目标组** |
|:---:|:---:|:---:|
| 公司条款和条件 | 企业 | 公司用户 |                 
| BYOD 条款和条件 | BYOD | BYOD 用户 |                


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)将条款和条件映射到用户组。

### <a name="configuration-policies"></a>配置策略

使用配置策略管理设备上的安全设置和功能。 设计配置策略时，请参阅用例要求部分，确定 Intune 设备所需的配置。 记录相关设置及其配置方式。 同时记录它们将面向哪些用户或设备组。

至少应为每个平台创建一个配置策略。 如果需要，可为每个平台创建多个配置策略。 下面的示例针对不同平台和用例场景设计 4 个不同的配置策略。

| **策略名称** | **设备平台** | **设置** | **目标组** |   
|:---:|:---:|:---:|:---:|
| 公司 - iOS | iOS | PIN 是必需的，长度为：6，限制云备份 | 公司设备 |                                                           
| 公司 - Android | Android | PIN 是必需的，长度为：6，限制云备份 | 公司设备 |                                                           
| BYOD - iOS  | iOS | PIN 是必需的，长度为：4 | BYOD 设备 |
| BYOD - Android  | Android | PIN 是必需的，长度为：4 | BYOD 设备 |


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定配置策略需求。

### <a name="profiles"></a>Profiles

使用配置文件来帮助最终用户连接到公司数据。 Intune 支持许多类型的配置文件。 请参阅用例和要求，确定何时配置配置文件。 所有设备配置文件按平台类型分类，且应包含在设计文档中。

- 证书配置文件

- Wi-Fi 配置文件

- VPN 配置文件

- 电子邮件配置文件

让我们更详细地研究一下每种类型的配置文件。

#### <a name="certificate-profiles"></a>证书配置文件

证书配置文件允许 Intune 向用户或设备颁发证书。 Intune 支持以下项：

- 简单证书注册协议 (SCEP)

- 受信任的根证书

- PFX 证书。

建议记录哪些用户组需要证书、需要多少证书配置文件，以及将它们部署到哪些用户组。

>[!NOTE]
> 请记住，SCEP 证书配置文件需要受信任的根证书，因此请确保 SCEP 证书配置文件的所有目标用户同时也接收受信任的根证书。 如果需要 SCEP 证书，请设计并记录需要什么 SCEP 证书模板。

下面是一个如何在设计过程中记录证书的示例：

| **类型** | **配置文件名称** | **设备平台** | **用例** |   
|:---:|:---:|:---:|:---:|
| 根 CA | 企业根 CA | Android、iOS、Windows Mobile | 公司、BYOD  |                                                           
| SCEP | 用户证书 | Android、iOS、Windows Mobile | 公司、BYOD |                                                           


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定证书配置文件需求。

#### <a name="wi-fi-profile"></a>Wi-Fi 配置文件

使用 Wi-Fi 配置文件自动将移动设备连接到无线网络。 Intune 支持将 Wi-Fi 配置文件部署到所有支持的平台。 了解有关 [Intune 如何支持 Wi-Fi 配置文件](../configuration/wi-fi-settings-configure.md)的详细信息。

下面是一个 Wi-Fi 配置文件设计的示例：

| 类型 | 配置文件名称 | 设备平台 | 用例 | | Wi-Fi | 亚洲 Wi-Fi 配置文件 | Android | 公司、BYOD 亚洲地区| | Wi-Fi | 北美 Wi-Fi 配置文件 | Android、iOS、Windows 10 移动版 | 公司、BYOD 北美地区 |    

可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定 Wi-Fi 配置文件需求。

#### <a name="vpn-profile"></a>VPN 配置文件

VPN 配置文件让用户可以安全地从远程位置访问网络。 Intune 支持来自本机移动 VPN 连接和第三方供应商的 VPN 配置文件。 了解有关 [Intune 支持的 VPN 配置文件和供应商](../configuration/vpn-settings-configure.md)的详细信息。

下面是一个记录 VPN 配置文件设计的示例。

| **类型** | **配置文件名称** | **设备平台** | **用例** |
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco AnyConnect 配置文件 | Android、iOS、Windows 10 移动版 | 公司、BYOD（北美和德国）|
| VPN | 脉冲安全 | Android | 公司、BYOD（亚洲地区） |

可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定 VPN 配置文件需求。

#### <a name="email-profile"></a>电子邮件配置文件

电子邮件配置文件允许电子邮件客户端自动通过连接信息和电子邮件配置进行安装。 Intune 在某些设备上支持电子邮件配置文件。 详细了解[电子邮件配置文件以及支持的平台](../configuration/email-settings-configure.md)。

下面是一个记录电子邮件配置文件设计的示例：

| **类型** | **配置文件名称** | **设备平台** | **用例** |
|:---:|:---:|:---:|:---:|
| 电子邮件配置文件 | iOS 电子邮件配置文件 | iOS | 公司 - 信息工作者 BYOD |
| 电子邮件配置文件 | Android Knox 电子邮件配置文件 | Android Knox | BYOD |

可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定电子邮件配置文件需求。
### <a name="apps"></a>应用

可使用 Intune 通过多种方式将应用提供给用户或设备。 应用程序的类型包括软件安装程序应用、来自公共应用商店的应用、来自外部链接的应用或托管 iOS 应用。 除单个应用部署外，还可通过适用于 iOS 和 Windows 的批量采购计划来管理和部署批量采购的应用。 了解详细信息：

- [可提供的应用类型](../apps/app-management.md)

- [适用于企业的 iOS 批量采购计划 (VPP)](../apps/vpp-apps-ios.md)

- [适用于企业的 Microsoft Store 应用](../apps/windows-store-for-business.md)

#### <a name="app-type-requirements"></a>应用类型要求

由于可向用户和设备部署应用，因此建议确定哪些应用程序将由 Intune 管理。 收集列表的同时，请尝试回答以下问题：

- 这些应用是否需要与云服务集成？

- 是否向 BYOD 用户提供所有应用？

- 这些应用的可用部署选项有哪些？

- 贵公司是否需要为合作伙伴提供对服务型软件 (SaaS) 应用数据的访问权限？

- 这些应用是否需要从用户设备访问 Internet？

- 这些应用是否在应用商店中公开提供？或者它们是否为自定义业务线 (LOB) 应用？


#### <a name="app-protection-policies"></a>应用保护策略

应用程序保护策略通过定义应用程序管理公司数据的方式最大限度地减少数据丢失。 Intune 对任何为与移动应用管理搭配使用而构建的应用程序支持应用保护策略。 设计应用保护策略时，需确定将对给定应用中的公司数据设置什么限制。 建议查看[应用保护策略](../apps/app-protection-policy.md)如何运作。 下面是一个如何记录现有应用程序以及需要何种保护的示例。

| **应用程序** | **目的** | **平台** | **用例** | **应用保护策略** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 可用 | iOS | 公司 - 高级管理人员 | 不能越狱，加密文件 |                                                         
| Word | 可用 | iOS、Android - Samsung Knox、非 Knox、Windows 10 移动版 | 公司、BYOD | 不能越狱，加密文件 |                                                         


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定应用配置策略需求。
#### <a name="compliance-policies"></a>相容性策略

合规性策略确定设备是否满足某些要求。 Intune 使用符合性策略确定设备是否被视为符合。 然后，可使用符合性状态限制或允许对公司资源的访问。 如果需要条件访问，建议设计[设备符合性策略](../protect/device-compliance-get-started.md)。

请参阅要求和用例，确定需要多少设备符合性策略，以及哪些用户组是目标用户组。 此外，还需要确定设备在未签入的状态下处于脱机状态多长时间后，会被视为不符合。

下面是如何设计合规性策略的示例：

| **策略名称** | **设备平台** | **设置** | **目标组** |
|:---:|:---:|:---:|:---:|
| 合规性策略 | iOS、Android - Samsung Knox、非 Knox、Windows 10 移动版 | PIN - 必需，不能越狱 | 公司、BYOD |


可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定符合性策略需求。
#### <a name="conditional-access-policies"></a>条件访问策略

使用条件访问仅允许符合要求的设备访问电子邮件和其他公司资源。 Intune 配合企业移动性 + 安全 (EMS) 工作，控制对公司资源的访问。 请确定是否需要条件访问，以及必须保护的内容。 了解有关[条件性访问](../protect/conditional-access.md)的详细信息。

对于联机访问，请确定条件访问策略的目标平台和用户组。 此外，还需确定是否需要为 Exchange 本地安装或配置 Intune 连接器： 

- [Exchange 内部部署](../protect/exchange-connector-install.md)

下面是一个如何记录条件访问策略的示例：

| **服务** | **新式验证平台** | **基本身份验证** | **用例** |
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | 在受 Intune 支持的平台上阻止不符合设备 | 公司、BYOD |
| SharePoint Online | iOS、Android |  | 公司、BYOD |

可[下载以上表格的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来确定条件访问策略需求。

## <a name="next-steps"></a>后续步骤

下一节提供 [Intune 实现过程](planning-guide-onboarding.md)的相关指南。
