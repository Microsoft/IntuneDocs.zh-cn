---
title: Intune 移动设备管理迁移指南
titleSuffix: Microsoft Intune
description: 本指南全面介绍从第三方 MDM 提供程序迁移到 Microsoft Intune 所涉及的各种详细信息。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6a6410aa5eada1f1c4a0983d269d9e661b03831
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046378"
---
# <a name="intune-migration-guide"></a>Intune 迁移指南

![Microsoft Intune MDM 迁移指南图解](./media/MDM-migration-guide-art.PNG)

要成功迁移到 Microsoft Intune，首先需要制定一个坚实可行的计划，充分考虑当前移动设备管理 (MDM) 环境、业务目标和技术需求等因素。 此外，还需要包括关键的利益干系人，他们将支持并协同完成迁移计划。

本指南全面介绍从第三方 MDM 提供程序迁移到 Intune 所涉及的各种详细信息。

## <a name="whats-included-in-this-guide"></a>该指南包括什么？

本指南将迁移分成两个阶段，这两个阶段均包含任务、策略和战略指导，将帮助你逐步完成迁移到 Intune MDM 的完整过程。

-   [第 1 阶段：为移动设备管理准备 Intune](migration-guide-prepare.md)

    -   [评估 MDM 迁移要求](migration-guide-prepare.md#assess-mdm-requirements)

    -   [基本设置](migration-guide-setup.md)

    -   [配置设备和应用管理策略](migration-guide-configure-policies.md)

    -   [配置应用保护策略](migration-guide-app-protection-policies.md)

    -   [特殊迁移注意事项](migration-guide-considerations.md)

-   [第 2 阶段：迁移活动](migration-guide-campaign.md)

    -   [通信计划](migration-guide-communication-plan.md)

    -   [推动最终用户采用条件访问](migration-guide-drive-adoption.md)

    -   [典型迁移周期](migration-guide-cycle.md)
        -   [监视迁移](migration-guide-cycle.md#monitoring-migration)
        -   [迁移后](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>假设

-   你已经在概念验证 (PoC) 环境中评估了 Intune，并已决定将其用作组织中的 MDM 解决方案。

-   现在，你已对 Intune 及其功能有了一定的了解。

## <a name="before-you-begin"></a>在开始之前

请注意，你的新的 Intune 部署可能不同于旧的 MDM 部署。 与传统的 MDM 服务不同，Intune 重点关注标识驱动访问控制，因此不需要使用网络代理设备来控制组织网络外围之外的移动设备对公司数据的访问。 Microsoft 提供了解决方案，通过一系列紧密集成的云服务（统称为企业客户端 + 安全产品/服务）来确保云本身数据服务的安全。

-   查看 [Intune 的常见使用方式](common-scenarios.md)。

## <a name="next-steps"></a>后续步骤

[第 1 阶段：为移动设备管理准备 Intune](migration-guide-prepare.md)
