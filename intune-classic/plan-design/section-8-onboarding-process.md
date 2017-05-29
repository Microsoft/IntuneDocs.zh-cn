---
title: "Intune 载入流程 | Microsoft Docs"
description: "本文提供将 Intune 仅限云解决方案载入到环境中时需考虑的所有详细信息。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 562e24af8058df56f1b952c82fefe62d38388ec3
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="intune-implementation"></a>Intune 实现

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

在载入阶段，将 Intune 实现到生产环境中。 根据本指南前几节中了解到的[用例要求](section-3-determine-use-case-requirements.md)，实现过程包括设置和配置 Intune 及外部依赖关系（如果需要）。

以下部分概述了 Intune 实现过程，其中包括要求和高级别任务。

>[!TIP]
> 查看[其他资源](additional-resources.md)了解有关 Intune 实现过程的详细信息。

## <a name="intune-requirements"></a>Intune 要求

下面提供了独立 Intune 的主要要求：

-   EMS/Intune 订阅

-   Office 365 订阅（用于 Office 应用和 MAM 策略托管应用）

-   Apple APNs 证书（用于启用 iOS 设备平台管理）

-   Azure AD Connect（用于目录同步）

-   Intune On-premises Connector for Exchange（如果需要，用于 Exchange 内部部署 CA）

-   Intune 证书连接器（如果需要，用于 SCEP 证书部署）

>[!TIP]
> 可在[此处](/intune-classic/get-started/what-to-know-before-you-start-microsoft-intune)找到有关独立 Intune 要求的详细信息。

## <a name="intune-implementation-process"></a>Intune 实现过程

### <a name="overview-of-implementation-tasks"></a>实现任务的概述

下面是实现 Intune 时每个任务的概述。

#### <a name="task-1-add-intune-subscription"></a>任务 1：添加 Intune 订阅

如之前的要求部分所确定的一样，EMS 或 Intune 订阅是必需的。 如果组织没有 EMS 或 Intune 订阅，请联系 Microsoft 或 Microsoft 帐户团队表明想要购买企业移动性 + 安全 (EMS) 或 Intune 的意愿。

-   了解有关[如何购买 Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) 的详细信息。

#### <a name="task-2-add-office-365-subscription"></a>任务 2：添加 Office 365 订阅

此步骤是可选的。 如之前的要求部分所确定的一样，如果打算使用 Exchange Online 并通过 MAM 策略管理 Office 移动应用，Office 365 订阅是必需的。 如果组织没有 Office 365 订阅，请联系 Microsoft 或 Microsoft 帐户团队表明想要购买 Office 365 的意愿。

-   了解有关[如何购买 Office 365](https://products.office.com/business/compare-office-365-for-business-plans) 的详细信息。

#### <a name="task-3-add-users-groups-in-azure-ad"></a>任务 3：在 Azure AD 中添加用户组

可能需要基于 Intune 部署用例场景和要求，在 AD 或 AAD 中添加用户或安全组。 应在 Active Directory 或 Azure Active Directory 中查看当前用户和安全组，并确定它们是否完全满足你的需求。 新用户和安全组最常添加到 Active Directory 中，并通过 Azure AD Directory Connect 同步到 Azure Active Directory。

-   了解有关[如何在 Intune 中添加用户/组](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)的详细信息。

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>任务 4：分配 Intune 和 Office 365 用户许可证

EMS/Intune 和 Office 365 推出的所有目标用户都需要具有分配给他们的许可证。 EMS/Intune 和 Office 365 许可证分配可在 Office 365 管理中心门户完成。

-   了解有关[如何分配 Intune 许可证](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)的详细信息。

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>任务 5：将移动设备管理机构设置为 Intune

必须先将设备管理机构设置为 Intune，然后才可开始使用 Intune 设置、配置、管理和注册设备。 在 Intune 管理门户的“管理”工作区中完成设置设备管理机构任务。

-   了解有关[如何设置设备管理机构](/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)的详细信息。

#### <a name="task-6-enable-device-platforms"></a>任务 6：启用设备平台

在 Intune 管理控制台中，大多数设备平台均默认启用，Apple 设备（iOS 和 Mac）除外。 必须先启用设备平台，然后才可在 Intune 中注册和管理 iOS 设备。 启用 iOS 设备平台由一个三步的过程组成：创建和下载 APN 证书并将其上传到 Intune。

-   详细了解 [iOS 和 Mac 设备管理设置的工作方式]/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>任务 7：添加和部署条款和条件策略

Microsoft Intune 支持添加和部署条款和条件策略。 在 Intune 管理门户的“策略”工作区中完成添加和部署条款和条件策略。 根据 Intune 部署用例和要求，适当地添加条款和条件策略，并将其部署到目标组。

-   了解有关[如何添加和部署条款和条件策略](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)的详细信息。

#### <a name="task-8-add-and-deploy-configuration-policies"></a>任务 8：添加和部署配置策略

Microsoft Intune 支持添加和部署两种类型的配置策略 - 常规和自定义。 在 Intune 管理门户的“策略”工作区中完成添加和部署配置策略。 根据 Intune 部署用例和要求，适当地添加配置策略，并将其部署到目标组。

-   了解有关[如何添加和部署配置策略](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)的详细信息。

#### <a name="task-9-add-and-deploy-resource-profiles"></a>任务 9：添加和部署资源配置文件

Microsoft Intune 支持电子邮件、Wi-Fi 和 VPN 配置文件。 在 Intune 管理门户的“策略”工作区中完成添加和部署配置文件。 根据 Intune 部署用例和要求，适当地添加电子邮件/Wi-Fi/VPN 配置文件，并将其部署到目标组。

-   了解有关[使用 Intune 启用对公司资源的访问](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)的详细信息。

#### <a name="task-10-add-and-deploy-apps"></a>任务 10：添加和部署应用

Microsoft Intune 支持 Web、LOB 和公共应用商店应用的部署。 此外，支持管理通过与 MAM 策略相关联集成 Intune SDK 的应用。 在 Intune 管理门户的“应用”工作区中完成添加和部署应用。 在 Intune 管理门户的“策略”工作区中完成添加 MAM 策略。 根据 Intune 部署用例和要求，适当地添加应用，并将其部署到目标组。

-   了解有关[添加和部署应用程序](/intune-classic/deploy-use/deploy-apps)的详细信息。

#### <a name="task-11-add-and-deploy-compliance-policies"></a>任务 11： 添加和部署合规性策略

Microsoft Intune 支持合规性策略。 在 Intune 管理门户的“策略”工作区中完成添加和部署合规性策略。 根据 Intune 部署用例和要求，适当地添加合规性策略，并将其部署到目标组。

-   了解有关[合规性策略](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)的详细信息。

#### <a name="task-12-enable-conditional-access-policies"></a>任务 12：启用条件性访问策略

Microsoft Intune 支持对 Exchange Online 和内部部署、SharePoint Online、Skype for Business Online 和 Dynamics CRM Online 的条件性访问。 在 Intune 管理门户的“策略”工作区中启用条件性访问策略。 根据 [Intune 部署用例和要求](section-3-determine-use-case-requirements.md)，适当地启用并配置条件性访问。

-   了解有关[条件性访问](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)的详细信息。

#### <a name="task-13-enroll-devices"></a>任务 13：注册设备

Intune 支持 iOS、Mac OS、Android、Windows 桌面版和 Windows Mobile 设备平台。 根据 Intune 部署用例和要求，适当地注册移动设备平台。

-   了解有关[如何注册设备](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)的详细信息。

>[!TIP]
> 查看此 [Microsoft Virtual Academy Intune 会话模块](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676)，了解有关 Intune 实现过程的详细信息。

## <a name="next-section"></a>下一节

下一节提供[测试和验证 Intune 部署](section-9-test-and-validation.md)的相关指南。

