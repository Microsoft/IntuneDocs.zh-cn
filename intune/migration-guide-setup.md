---
title: Microsoft Intune 基本设置
description: 本文提供设置 Microsoft Intune 所需的步骤。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76f5188a866e744c034fd592f9b1dfcbc9061ffa
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549386"
---
# <a name="basic-setup"></a>基本设置

评估环境后，即可设置 Microsoft Intune。

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune 部署的外部依赖关系

### <a name="identity"></a>标识

Intune 要求 Azure Active Directory (AAD) 作为标识和用户分组提供者。 了解详细信息：

- [身份要求](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [目录同步路线图](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [多重身份验证 (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [规划用户和设备组](users-add.md)

- [如何创建用户和设备组](groups-get-started.md)

如果组织已在使用 Office 365，则 Intune 必须使用相同的 Azure Active Directory 环境。

### <a name="pki-optional"></a>PKI（可选）

如果打算将针对 VPN、Wi-Fi 或电子邮件配置文件的基于证书的身份验证与 Intune 结合使用，需确保具有受支持的 [PKI 基础结构](certificates-configure.md)，并准备好创建和部署证书配置文件。 有关在 Intune 中配置证书的详细信息，请参阅：

- [如何配置 SCEP 证书基础结构](/intune/certificates-scep-configure)

- [如何配置 PFX 证书基础结构](/intune/certficates-pfx-configure)。


## <a name="task-list-for-an-intune-setup"></a>Intune 设置的任务列表

### <a name="task-1-intune-subscription"></a>任务 1：Intune 订阅

迁移到 Intune 之前，首先需要 Intune 订阅。

- 可以访问[本页](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)，它提供了执行以下操作的相关说明：

    - 创建链接到新的 AAD 租户的新的 Intune 订阅。

    - 通过登录到现有的 AAD 租户来关联 Intune 订阅。

### <a name="task-2-assign-intune-user-licenses"></a>任务 2：分配 Intune 用户许可证

- 了解[如何分配 Intune 用户许可证](licenses-assign.md)。

- 如果你已创建新的 Azure Active Directory 租户，可以了解[如何从本地 Active Directory (AD) 中创建新的用户或同步用户。](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>任务 3：将 MDM 机构设置为 Intune

可以通过 Azure 门户或 Configuration Manager 当前分支控制台管理 Intune。 除非需要将 Intune 与 Configuration Manager Current Branch 部署相集成，否则建议从 [Azure 门户](https://portal.azure.com)管理 Intune。

将 MDM 机构设置为 Intune，启用 Intune Azure 门户  。 使用不同的 MDM 机构以使 Intune 将 MDM 管理传输到备用 Microsoft 管理控制台。 这种情况并不常见。

> [!IMPORTANT]
> 如果你是第一次将移动设备管理传输到 Intune，则应将 MDM 机构设置为 Intune。

了解[如何设置移动管理机构](mdm-authority-set.md)。

## <a name="next-step"></a>下一步

配置[设备和应用管理策略](migration-guide-configure-policies.md)。
