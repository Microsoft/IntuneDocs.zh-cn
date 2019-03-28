---
title: 什么是 Microsoft Intune
description: 了解 Microsoft Intune 如何成为企业移动性 + 安全性解决方案的移动设备管理 (MDM) 和移动应用管理 (MAM) 组件，以及它如何帮助保护公司数据。
keywords: 什么是 Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 511e672193ec609f817c10572c99ac73831c54ae
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460574"
---
# <a name="what-is-microsoft-intune"></a>什么是 Microsoft Intune？

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Microsoft Intune 是企业移动管理 (EMM) 领域中基于云的服务，可帮助员工提高工作效率，同时保护企业数据。 与其他 Azure 服务一样，Microsoft Intune 也可在 Azure 门户中使用。 通过 Intune，还可以：
* 管理工作人员用来访问公司数据的移动设备和 PC。
* 管理员工使用的移动应用。
* 通过帮助控制员工访问和共享公司信息的方式来保护公司信息。
* 确保设备和应用符合公司安全要求。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 可帮助解决的常见业务问题

* [保护本地电子邮件和数据以供移动设备访问](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [保护 Office 365 电子邮件和数据以供移动设备安全访问](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [向员工发放公司拥有的手机](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [为所有员工提供一个“自带设备办公”(BYOD) 或个人设备计划](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [允许员工从不受管理的公用网亭安全访问 Office 365](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [向任务工作者发放使用受限的共享平板电脑](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Intune 如何工作？
Intune 是 Microsoft 企业移动性 + 安全性 (EMS) 套件的组件，可用于管理移动设备和应用。 它与 Azure Active Directory (Azure AD) 等其他 EMS 组件紧密集成以实现标识和访问控制，并与 Azure 信息保护集成以实现数据保护。 将它与 Office 365 结合使用时，员工可以在其设备上高效工作，同时保护组织的信息。

![Intune 体系结构示意图](./media/intunearch_sm.png)

查看 Intune 体系结构示意图的[大图](./media/intunearchitecture.svg)。

Intune 设备和应用管理功能和 EMS 数据保护功能的使用方式取决于[尝试解决的业务问题](#common-business-problems-that-intune-helps-solve)。 例如：
* 如果要创建一系列一次性设备供零售商店中的轮班员工共享，那么应该充分利用设备管理。
* 如果允许员工使用其个人设备访问公司数据 (BYOD)，则会依赖于应用管理和数据保护。  
* 如果要向信息工作者发放公司电话，那么将依赖所有这些技术。

## <a name="intune-device-management-explained"></a>Intune 设备管理介绍
Intune 设备管理通过使用移动操作系统中的可用协议或 API 来实现。 它包括类似以下的任务：
* 向管理系统注册设备，以便 IT 部门具有访问公司服务的设备清单
* 配置设备，确保其满足公司安全和健康标准
* 提供证书和 Wi-Fi / VPN 配置文件以访问公司服务
* 报告和衡量设备是否符合公司标准
* 从托管设备中删除公司数据  

有时，人们认为“对公司数据的访问控制”是一种设备管理功能。 我们不这样认为，因为它不是由移动操作系统提供。 确切地说，它是由标识提供程序提供。 在本例中，标识提供程序是 Azure Active Directory (Azure AD)、Microsoft 的标识和访问管理系统。  

通过与 Azure AD 集成，Intune 实现了一系列广泛的访问控制方案。 例如，可以要求移动设备符合 Intune 中定义的公司标准，然后才允许设备访问 Exchange 之类的公司服务。 同样，可以将公司服务锁定到特定的一组移动应用。 例如，可以锁定 Exchange Online，只允许由 Outlook 或 Outlook Mobile 进行访问。

## <a name="intune-app-management-explained"></a>Intune 应用管理介绍
我们所说的应用管理是指：
* 向员工分配移动应用
* 使用应用运行时的标准设置来配置应用
* 控制在移动应用中使用和共享公司数据的方式
* 从移动应用中删除公司数据   
* 更新应用
* 报告移动应用清单
* 跟踪移动应用使用情况

我们见到过将移动应用管理 (MAM) 这一术语用于单独表示这些操作中的任何一项或任意几项的组合。 特别是，人们常常会将应用配置的概念与在移动应用中保护公司数据的概念相结合。 这是因为某些移动应用具有允许配置数据安全功能的设置。

我们说到应用配置和 Intune 时，特指 [iOS 上的托管应用配置](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)等技术。

当在 EMS 中结合其他服务使用 Intune 时，可以通过应用配置提供高于移动操作系统和移动应用本身提供的组织移动应用安全。 使用 EMS 管理的应用可以访问更多的移动应用和数据保护功能，包括：

* [单一登录](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [多重身份验证](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [应用条件访问 - 如果移动应用中包含公司数据，则允许访问](app-based-conditional-access-intune.md)
* [在同一个应用内将个人数据与公司数据隔离](app-protection-policy.md)
* [应用保护策略（PIN、加密、另存为、剪贴板等等）](app-protection-policies.md)
* [从移动应用擦除公司数据](apps-selective-wipe.md)
* [权限管理支持](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![显示应用管理数据安全级别的图片](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Intune 应用安全性
提供应用安全性是应用管理的一部分，在 Intune 中，谈及移动应用安全性时，我们指的是：
* 将个人信息与企业 IT 识别保持隔离
* 限制用户可以对公司信息执行的操作，如复制、剪切/粘贴、保存和查看
* 从移动应用中删除公司数据，也称为选择性擦除或公司擦除

Intune 提供移动应用安全的一种方法是通过其应用保护策略功能。 应用保护策略使用 Azure AD 标识来隔离公司数据与个人数据。 使用公司凭据访问的数据还会另外受到公司保护。

例如，用户使用公司凭据登录到其设备时，其公司标识允许他们访问使用个人标识无法访问的数据。 用户使用该公司数据时，应用保护策略会控制数据的保存方式和共享方式。 这些相同的保护措施将不会应用于用户通过个人标识登录其设备访问的数据。 这样，IT 能够控制公司数据，而最终用户可以保持对其个人数据的控制性和私密性。

## <a name="emm-with-and-without-device-enrollment"></a>需要和无需设备注册的 EMM
大多数企业移动性管理解决方案支持基本的移动设备和移动应用技术。 这些通常与在组织的移动设备管理 (MDM) 解决方案中注册过的设备相关联。 Intune 支持这些方案，此外还支持许多“无需注册”方案。  

组织采取“无需注册”方案的程度有所不同。 一些组织对其实现标准化。 一些组织允许它用于配套设备，如个人平板电脑。 其他组织则完全不支持。 即使在最后一种情况下（组织要求所有员工设备注册到 MDM），这些组织通常也会对承包商、供应商以及具有特定豁免权的其他设备支持“无需注册”方案。

甚至可以在已注册的设备上使用 Intune 的“无需注册”技术。 例如，在 MDM 中注册的设备可能会有移动操作系统提供的 open-in 保护。 “Open-in”保护是 Apple iOS 的一种功能，用于防止将一种应用（如 Outlook）中的文档在另一种应用（如 Word）中打开，除非这两种应用都由同一 MDM 提供程序托管。 此外，IT 可能会将应用保护策略应用于 EMS 托管的移动应用，以控制另存为或提供多重身份验证。

无论组织在已注册和未注册移动设备和应用方面的态度如何，作为 EMS 的一部分，Intune 包含一种能够在保护公司数据的同时提高员工工作效率的工具。

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure 门户中的 Microsoft Intune

可在 [Azure 门户](https://portal.azure.com)中找到 Microsoft Intune 服务。

Azure 门户中 Microsoft Intune 的重要功能包括：

- 用于所有企业移动性 + 安全性 (EMS) 组件的集成控制台
- 基于 Web 标准构建的基于 HTML 的控制台
- 可自动执行多种操作的 Microsoft Graph API 支持
- Azure Active Directory (AD) 组提供跨所有 Azure 应用程序的兼容性
- 支持大多数新式 Web 浏览器

若要获取自定义门户体验的快速指南，请参阅[开始使用 Azure 门户中的 Intune](get-started-azure.md)。

> [!NOTE]
> 如果已使用以前版本的 Microsoft Intune，可参考以下信息：
> * [我的功能位于 Azure 的什么位置？](ui-changes.md)是一个参考，显示随着移动到 Azure 而更改的特定工作流程和 UI。
> * [Azure 门户中的 Intune 经典组](groups-get-started.md)解释了转移到 Azure Active Directory 安全组以进行组管理的含义。

### <a name="before-you-start"></a>开始之前

若要使用 Azure 门户中的 Intune，必须拥有 Intune 管理员和租户帐户。 如果尚没有帐户，请[注册帐户](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

### <a name="supported-web-browsers-for-the-azure-portal"></a>受 Azure 门户支持的 Web 浏览器

Azure 门户在大多数新式电脑、Mac 和平板电脑上都可以运行。 不支持移动电话。
目前，支持以下浏览器：

- Microsoft Edge（最新版本）
- Microsoft Internet Explorer 11
- Safari（最新版本，仅限 Mac）
- Chrome（最新版本）
- Firefox（最新版本）

请查看 [Azure 门户](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)，了解支持的浏览器的最新相关信息。

## <a name="next-steps"></a>后续步骤
* 了解一些 [Intune 的常见使用方式](common-scenarios.md)。
* 通过 [Intune 的 30 天试用版](free-trial-sign-up.md)熟悉该产品。
* 深入了解 Intune 的[技术要求和功能](supported-devices-browsers.md)。
