---
title: Intune 载入过程
titlesuffix: Microsoft Intune
description: 本文提供将 Microsoft Intune 仅限云解决方案载入到环境中时需考虑的所有详细信息。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 871e091af1f2046206dbc94fdc7d199435645190
ms.sourcegitcommit: e04e1652e121b4b9dbed05d0bbaa569e6d5d09bd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2018
---
# <a name="implement-your-microsoft-intune-plan"></a>实现 Microsoft Intune 计划

在载入阶段，将 Intune 部署到生产环境中。 根据[用例要求](planning-guide-requirements.md)，实现过程包括设置和配置 Intune 及外部依赖关系（如果需要）。

以下部分概述了 Intune 实现过程，其中包括要求和高级别任务。

## <a name="intune-requirements"></a>Intune 要求

独立 Intune 的主要要求如下：

-   企业移动性 + 安全性 (EMS)/Intune 订阅

-   Office 365 订阅（用于 Office 应用和应用保护策略托管应用）

-   Apple APNs 证书（用于启用 iOS 设备平台管理）

-   Azure AD Connect（用于目录同步）

-   Intune On-Premises Connector for Exchange（如果需要，用于 Exchange 内部部署的条件访问）

-   Intune 证书连接器（如果需要，用于 SCEP 证书部署）

>[!TIP]
> 请参阅[支持的设备](supported-devices-browsers.md)列表，获取可通过 Intune 管理的设备的完整列表。

## <a name="intune-implementation-process"></a>Intune 实现过程

我们已明确实现 Intune 部署的 13 个离散任务。 根据业务需求、现有基础结构和设备管理策略，其中一些任务可能已经完成。 其他任务可能不适用于你的计划。

### <a name="task-1-get-an-intune-subscription"></a>任务 1：获取 Intune 订阅

如上方 Intune 需求部分所述，需要一个 EMS 或 Intune 订阅。 如果组织没有相关订阅，请联系 Microsoft 或 Microsoft 帐户团队，表明想要购买企业移动性 + 安全性 (EMS) 或 Intune 的意愿。

-   了解有关[如何购买 Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) 的详细信息。

### <a name="task-2-add-office-365-subscription"></a>任务 2：添加 Office 365 订阅

此步骤是可选的。 若要使用 Exchange Online 并通过应用保护策略管理 Office 移动应用，则需要 Office 365 订阅。 如果组织没有 Office 365 订阅，请联系 Microsoft 或 Microsoft 帐户团队，表明想要购买 Office 365 的意愿。

-   了解有关[如何购买 Office 365](https://products.office.com/business/compare-office-365-for-business-plans) 的详细信息。

### <a name="task-3-add-users-groups-in-azure-ad"></a>任务 3：在 Azure AD 中添加用户组

可能需要基于 Intune 部署用例场景和要求，在 Active Directory 或 Azure Active Directory 中添加用户或安全组。 请在 Active Directory 或 Azure Active Directory 中查看当前用户和安全组，并确定其是否完全满足你的需求。 添加新用户和安全组时，建议在 Active Directory 中进行添加，并使用 Azure AD Connect 将其与 Azure Active Directory 同步。


-   了解有关[如何在 Intune 中添加用户/组](users-permissions-add.md)的详细信息。
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>任务 4：分配 Intune 和 Office 365 用户许可证

EMS/Intune 和 Office 365 推出的所有目标用户均需具备分配给他们的许可证。 可在 Office 365 管理中心门户分配 EMS/Intune 和 Office 365 许可证。

-   了解有关[如何分配 Intune 许可证](licenses-assign.md)的详细信息。

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>任务 5：将移动设备管理机构设置为 Intune

必须先将设备管理机构设置为 Intune，然后才可开始使用 Intune 设置、配置、管理和注册设备。

-   详细了解[如何设置设备管理机构](mdm-authority-set.md)。

### <a name="task-6-enable-device-platforms"></a>任务 6：启用设备平台

大多数设备平台均默认启用，Apple 设备（iOS 和 Mac）除外。 必须先启用设备平台，然后才可在 Intune 中注册和管理 iOS 设备。 为此，需创建 MDM Push Certificate，并将其添加到 Intune。

-   详细了解[如何启用 Apple 设备进行注册](apple-mdm-push-certificate-get.md)。

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>任务 7：添加和部署条款和条件策略

Intune 支持条款和条件策略。 根据 Intune 部署用例和要求，适当地添加条款和条件策略，并将其部署到目标组。

-   了解有关[如何添加和部署条款和条件策略](terms-and-conditions-create.md)的详细信息。

### <a name="task-8-add-and-deploy-configuration-policies"></a>任务 8：添加和部署配置策略

Intune 支持两种类型的配置策略 - 常规和自定义。 根据 Intune 部署用例和要求，适当地添加配置策略，并将其部署到目标组。

-   了解有关[如何添加和部署配置策略](device-profiles.md)的详细信息。

### <a name="task-9-add-and-deploy-resource-profiles"></a>任务 9：添加和部署资源配置文件

Intune 支持电子邮件、Wi-Fi 和 VPN 配置文件。 根据 Intune 部署用例和要求，适当地添加配置文件，并将其部署到目标组。

-   详细了解[如何使用 Intune 启用对公司资源的访问](device-profiles.md)。

### <a name="task-10-add-and-deploy-apps"></a>任务 10：添加和部署应用

Intune 支持部署 Web、业务线和公共应用商店应用。 还可管理通过与应用保护策略相关联集成 Intune SDK 的应用。 根据 Intune 部署用例和要求，适当地添加应用，并将其部署到目标组。

-   详细了解[添加和部署应用](app-management.md)。

### <a name="task-11-add-and-deploy-compliance-policies"></a>任务 11： 添加和部署合规性策略

Intune 支持符合性策略。 根据 Intune 部署用例和要求，适当地添加符合性策略，并将其部署到目标组。

-   了解有关[合规性策略](device-compliance.md)的详细信息。

### <a name="task-12-enable-conditional-access-policies"></a>任务 12：启用条件访问策略

Intune 支持对 Exchange Online、Exchange 內部部署、SharePoint Online、Skype for Business Online 和 Dynamics CRM Online 的条件访问。 根据 Intune 部署用例和要求，适当地启用并配置条件访问。

-   了解有关[条件性访问](conditional-access.md)的详细信息。

### <a name="task-13-enroll-devices"></a>任务 13：注册设备

Intune 支持 iOS、Mac OS、Android、Windows 桌面版和 Windows Mobile 设备平台。 根据 Intune 部署用例和要求，适当地注册移动设备平台。

-   了解有关[如何注册设备](device-enrollment.md)的详细信息。


## <a name="next-steps"></a>后续步骤

查看此 [Microsoft Virtual Academy Intune 会话模块](https://mva.microsoft.com/en-US/training-courses/deploying-microsoft-enterprise-mobility-suite-16408)，了解有关 Intune 实现过程的详细信息。


请参阅[测试和验证 Intune 部署](planning-guide-test-validation.md)的相关指南。
