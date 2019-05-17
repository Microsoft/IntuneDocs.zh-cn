---
title: Microsoft 365 中的设备管理
description: Microsoft 365 企业版包含 Microsoft Intune。 了解 Intune 如何为你的组织提供移动设备管理和移动应用程序管理。 阅读常见方案，并使用 Intune 在环境中部署 Microsoft 365。
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15f908a34f0a9315552acfad56cbf560a23fa26d
ms.sourcegitcommit: e63e3debb5f4d9a757f767913e72e39742137b17
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58788439"
---
# <a name="what-is-device-management"></a>什么是设备管理？ 

所有管理员的关键任务是保护组织的资源和数据。 此任务是设备管理。 用户可以通过多个设备打开和共享个人文件、访问网站以及安装应用和游戏。 这些用户也是员工和学生。 他们希望使用他们的设备访问工作和学校资源，例如电子邮件和 OneNote。 设备管理使组织能够保护其资源和数据。 

使用设备管理提供程序，组织可以确保只有经过授权的人员和设备才能访问专有信息。 同时，设备用户可以放心地从其手机访问工作数据，因为他们知道他们的设备符合组织的安全要求。 作为组织，你可能会问 - 应该使用什么来保护我们的资源？

答案是 [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune)。 Intune 提供移动设备管理 (MDM) 和移动应用程序管理 (MAM)。 MDM 或 MAM 解决方案的一些关键任务是：

- 支持多种移动环境，并能安全地管理 iOS、Android、Windows 和 macOS 设备。
- 确保设备和应用符合组织的安全要求。
- 创建有助于确保公司所有和个人设备上组织数据的安全的策略。
- 使用单个、统一的移动解决方案来实施这些策略，并帮助管理设备、应用、用户和组。

Intune 包含在 Microsoft 365 中，并与 Azure Active Directory (Azure AD) 集成。 Azure AD 可帮助控制具有访问权限的用户以及他们有权访问的内容。

## <a name="hello-intune"></a>Hello Intune！
许多组织（如 Microsoft）都使用 Intune 来保护用户从其公司所有和个人移动设备访问的专有数据。 Intune 包括设备和应用配置策略、软件更新策略和安装状态（图表、表格和报告）等功能，可帮助保护和监视数据访问。

人们常常有多个使用不同平台的设备。 例如，员工可能会使用 Surface Pro 进行工作，并在个人生活中使用 Android 移动设备。 而且，人们常常从多个设备访问组织资源，例如 Microsoft Outlook 和 SharePoint。

使用 Intune，你可以管理每个人的多个设备，以及在每个设备上运行的不同平台，包括 iOS、macOS、Android 和 Windows。 Intune 按设备平台分隔策略和设置。 因此，可以轻松管理和查看特定平台的设备。

[常见方案](https://docs.microsoft.com/intune/common-scenarios)是了解 Intune 在使用移动设备时如何回答常见问题的绝佳资源。 你将发现以下方案：  
- 使用本地 Exchange 保护电子邮件
- 安全可靠地访问 Office 365
- 使用个人设备访问组织资源

## <a name="integration-with-secure-and-protect-services"></a>与安全和保护服务集成
所有设备管理解决方案的关键任务是提供安全性和保护。 Intune 能够很好的与其他服务集成，以完成此任务。 例如：

- Microsoft 365 是简化常见 IT 任务的关键组件。 在 Microsoft 365 管理中心内，可创建用户，并管理组。 还可以访问其他服务，如 Intune、Azure AD 等。 

  例如，在 Microsoft 365 中创建 iOS 设备组。 然后，使用 Intune 将策略推送到着重于 iOS 功能的 iOS 设备组，例如访问应用商店、使用 AirDrop、备份到 iCloud、使用 Apple 的 Web 筛选器等。

- Windows Defender 包含许多安全功能，可帮助保护 Windows 10 设备。 例如，结合使用 Intune 和 Windows Defender，可以： 

    - 启用 [Windows Defender SmartScreen ](https://docs.microsoft.com/intune/endpoint-protection-windows-10) 以查找移动设备上的文件和应用中的可疑活动。 
    - 使用 [Windows Defender 高级威胁防护 (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection)来帮助阻止移动设备上的安全漏洞。 并且，通过阻止用户访问公司资源来帮助限制安全漏洞的影响。

- 条件访问是 Azure Active Directory 的功能，可以与 Intune 完美集成。 使用[条件访问](https://docs.microsoft.com/intune/conditional-access)，确保只允许符合的设备访问电子邮件、SharePoint 和其他应用。 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>选择适合你的设备管理解决方案

有几种方法可以实现设备管理。 首先，可以使用 Intune 中内置的功能来管理设备的不同方面。 这种方法称为移动设备管理 (MDM)。 用户“登记”他们的设备，并使用证书与 Intune 通信。 作为 IT 管理员，你可以在设备上推送应用、将设备限制到特定的操作系统、阻止个人设备等。 如果设备丢失或被盗，还可以从设备中删除所有数据。 

在第二种方法中，可以在设备上管理应用。 这种方法称为移动应用程序管理 (MAM)。 用户可以使用其个人设备访问组织资源。 打开应用（如电子邮件或 SharePoint）时，系统会提示用户进行其他身份验证。 如果设备丢失或被盗，可以从设备中删除所有组织数据。 

此外，还可以结合使用 [MDM 和 MAM](https://docs.microsoft.com/intune/byod-technology-decisions)。

设置 Intune 时，还可以选择仅在 Azure 门户中管理设备，或结合使用 Intune 和 Microsoft 365 来管理设备。 [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal)（在 Azure 门户中将移动设备管理迁移到 Intune）是一个 Microsoft IT 案例研究。 在本案例研究中，了解 Microsoft IT 如何选择新式设备管理方法以及相关经验。

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>使用“设备管理”仪表板简化 IT 任务

[设备管理仪表板](https://devicemanagement.portal.azure.com/)是一站式服务，可管理和完成移动设备的任务。 此仪表板包括用于设备管理（包括 Intune 和 Azure Active Directory）和客户端应用管理的服务。 

在“设备管理”仪表板中，你可以：

- [注册设备](https://docs.microsoft.com/intune/device-enrollment)
- [设置设备合规性](https://docs.microsoft.com/intune/device-compliance-get-started)
- [管理设备](https://docs.microsoft.com/intune/device-management)
- [管理应用](https://docs.microsoft.com/intune/app-management)  
- [iOS 电子书](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [安装 Exchange 内部部署连接器](https://docs.microsoft.com/intune/exchange-connector-install)  
- [管理角色](https://docs.microsoft.com/intune/role-based-access-control)  
- 管理软件更新
  - [管理 Windows 10 更新](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [管理 iOS 更新](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [管理用户](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [管理组和成员](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [故障排除](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>下一步
当准备好开始使用 MDM 或 MAM 解决方案时，请按不同步骤设置 Intune、登记设备并开始创建策略。 [适用于 Microsoft 365 的移动设备管理](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)也是出色的资源。
