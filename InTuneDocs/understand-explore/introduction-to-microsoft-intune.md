---
title: "什么是 Microsoft Intune | Microsoft Docs"
description: "了解 Intune 作为企业移动性 + 安全性解决方案的移动设备管理组件的工作原理，以及它帮助保护公司数据的方式。"
keywords: "什么是 Intune"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 03/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6673c8de8d5deb74005b40a58274efcb10783fcc
ms.openlocfilehash: ee1f41384df083d6479804ba05c0252d9ba12e1b
ms.lasthandoff: 03/08/2017


---

# <a name="what-is-intune"></a>什么是 Intune？

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 是一种基于云的企业移动管理 (EMM) 服务，可帮助员工提高工作效率，同时保护企业数据。 通过 Intune，还可以：
* 管理员工用于访问公司数据的移动设备。
* 管理员工使用的移动应用。
* 通过帮助控制员工访问和共享公司信息的方式来保护公司信息。
* 确保设备和应用符合公司安全要求。

Intune 与 Azure Active Directory (Azure AD) 紧密集成以实现标识和访问控制，并与 Azure 信息保护集成以实现数据保护。 它负责 Microsoft 企业移动性 +安全性 (EMS) 的管理，而 Office 365 则负责 Microsoft 移动解决方案的高效工作。  

结合 Office 365 和 EMS，使员工可以在其所有设备上高效工作，同时保护组织的信息。 Office 365 搭配 EMS 是针对企业移动性的完整集成套件，包括工作效率、标识、访问控制、管理和数据保护。 它为你提供了在组织中部署和运行移动性解决方案的有效方式。

## <a name="how-does-intune-work"></a>Intune 如何工作？
Intune 提供移动设备管理 (MDM) 和移动应用管理 (MAM)。 Intune 的 MDM 和 MAM 功能促成数据保护和相容性方案的 EMS 套件。  

使用 Intune 和 EMS 数据保护的 MDM / MAM 功能的方式取决于[尝试解决的业务问题](#common-business-problems-that-intune-helps-solve)。 例如：
* 如果要创建一次性设备池供零售商店中的轮班员工共享，那么会充分利用 MDM。
* 如果允许员工使用其个人设备访问公司数据 (BYOD)，则会依赖于 MAM 和数据保护。  
* 如果向信息工作者发放公司电话，那么将十分依赖所有这些技术。

## <a name="intune-mobile-device-management-mdm-explained"></a>Intune 移动设备管理 (MDM) 解释
MDM 通过使用移动操作系统中的可用协议或 API 来工作。 它包括类似以下的任务：
* 向管理系统注册设备，以便 IT 部门具有访问公司服务的设备清单
* 配置设备，确保其满足公司安全和健康标准
* 提供证书和 Wi-Fi / VPN 配置文件以访问公司服务
* 报告和衡量设备是否符合公司标准
* 从托管设备中删除公司数据  

有时，人们认为**对公司数据的访问控制**是一种 MDM 功能。 我们不这样认为，因为它不是由移动操作系统提供。 确切地说，它是由标识提供程序提供。 在本例中，标识提供程序是 Azure Active Directory (Azure AD)、Microsoft 的标识和访问管理系统。  

通过与 Azure AD 集成，Intune 实现了一系列广泛的访问控制方案。 例如，可以要求移动设备符合 Intune 中定义的公司标准，然后才允许设备访问 Exchange 之类的公司服务。 同样，可以将公司服务锁定到特定的一组移动应用。 例如，可以锁定 Exchange Online，只允许由 Outlook 或 Outlook Mobile 进行访问。

## <a name="intune-mobile-app-management-mam-explained"></a>Intune 移动应用管理 (MAM) 解释
谈及 MAM 时，我们指的是我们的解决方案使 IT 专业人员能够通过移动应用进行的一系列操作，例如：
* 将移动应用发布给员工
* 配置应用
* 控制在移动应用中使用和共享公司数据的方式
* 从移动应用中删除公司数据   
* 更新移动应用
* 报告移动应用清单
* 跟踪移动应用使用情况

我们已见过用于单独表示这些操作中的任何一个或者表示特定组合的术语 MAM。 特别是，人们常常会将应用配置的概念（即使用[iOS 上的托管应用配置](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)之类的技术）与在移动应用中保护公司数据的概念相混淆。 这是因为某些移动应用具有允许配置数据安全功能的设置。

结合用于保护数据的操作系统功能（例如，Windows 10 上的 Windows 信息保护等 MDM 功能），这能够对移动设备上的数据提供诸多保护。

当在 EMS 中结合其他服务使用 Intune 时，可以通过应用配置提供高于移动操作系统和移动应用本身提供的组织移动应用安全。 使用 EMS 管理的应用可以访问更多的移动应用和数据保护，包括：

* [单一登录](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*    [多重身份验证](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [应用条件性访问（如果移动应用中包含公司数据，则允许访问）](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [在同一个应用内将个人数据与公司数据隔离](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [应用保护策略（PIN、加密、另存为、剪贴板等等）](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [从移动应用擦除公司数据](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [权限管理支持](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![显示应用管理数据安全级别的图片](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Intune 移动应用安全
提供应用安全性是 MAM 的一部分，在 Intune 中，谈及移动应用安全性时，我们指的是：
* 将个人信息与企业 IT 识别保持隔离
* 限制用户可以对公司信息执行的操作，如复制、剪切/粘贴、保存和查看
* 从移动应用中删除公司数据，也称为选择性擦除或公司擦除

Intune 提供移动应用安全的一种方法是通过其**应用保护策略**功能。 应用保护策略使用 Azure AD 标识来隔离公司数据与个人数据。 将为使用公司凭据访问的数据提供额外的企业保护。

用户使用公司凭据登录到其设备时，公司标识允许她访问使用个人标识访问无法访问的数据。 使用该企业数据时，Intune 与其他 EMS 技术一起控制保存和共享该数据的方式。 这些相同的保护措施将不会应用于用户通过个人标识登录其设备访问的数据。 这样，IT 能够控制公司数据，而最终用户可以保持对个人数据的控制性和私密性。

## <a name="emm-with-and-without-device-enrollment"></a>需要和无需设备注册的 EMM
大多数企业移动性管理解决方案支持基本的移动设备和移动应用技术。 这些通常与注册到组织 MDM 解决方案中的设备相关联。 Intune 支持这些方案，此外还支持许多“无需注册”方案。  

组织采取“无需注册”方案的程度有所不同。 一些组织对其实现标准化。 一些组织允许它用于配套设备，如个人平板电脑。 其他组织则完全不支持。 即使在最后一种情况下（组织要求所有员工设备注册到 MDM），这些组织通常也会对承包商、供应商以及具有特定豁免权的其他设备支持“无需注册”方案。

甚至可以在已注册的设备上使用 Intune 的“无需注册”技术。 例如，在 MDM 中注册的设备可能会有移动操作系统提供的 open-in 保护。 （Open-in 保护是一种 iOS 功能，防止将一种应用（如 Outlook）中的文档在另一种应用（如 Word）中打开，除非这两种应用都由 MDM 提供程序托管。）此外，IT 可能会将应用保护策略应用于 EMS 托管的移动应用，以控制另存为或提供多重身份验证。

无论组织在已注册和未注册移动设备和应用方面的态度如何，作为 EMS 的一部分，Intune 包含一种能够在保护公司数据的同时提高员工工作效率的工具。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 可帮助解决的常见业务问题
以下列出的业务问题将链接到我们可提供的解决方案相关的详细信息。 只有最后一项要求 MDM 注册，作为解决方案的一部分：

* [保护本地电子邮件和数据以供移动设备访问](common-ways-to-use-intune.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [保护 Office 365 电子邮件和数据以供移动设备安全访问](common-ways-to-use-intune.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [向员工发放公司拥有的手机](common-ways-to-use-intune.md#issue-corporate-owned-phones-to-your-information-workers)
* [为所有员工提供一个“自带设备办公”(BYOD) 或个人设备计划](common-ways-to-use-intune.md#offer-a-bring-your-own-device-program-to-all-employees)
* [允许员工从不受管理的公用网亭安全访问 Office 365](common-ways-to-use-intune.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [向任务工作者发放使用受限的共享平板电脑](common-ways-to-use-intune.md#issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>后续步骤
* 了解一些 [Intune 的常见使用方式](common-ways-to-use-intune.md)。
* 通过 [Intune 的 30 天试用版](get-started-with-a-30-day-trial-of-microsoft-intune.md)熟悉该产品。
* 深入了解 Intune 的[技术要求和功能](/intune/get-started/what-to-know-before-you-start-microsoft-intune)。

