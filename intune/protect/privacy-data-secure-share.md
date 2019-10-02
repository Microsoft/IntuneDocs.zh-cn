---
title: Intune 中的数据安全性和数据共享
description: 了解 Intune 中如何保护和共享个人数据。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 631d76aca2c393be3c81cb8b6f532605664f4ce4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721950"
---
# <a name="data-security-and-sharing-in-intune"></a>Intune 中的数据安全性和数据共享


## <a name="data-security"></a>数据安全性

Microsoft Intune 是 Microsoft 企业移动性 + 安全性套件云服务产品的重要组成部分。 为了支持[数据管理策略](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx)，所有 Microsoft 云服务均采用 [Microsoft 隐私](https://www.microsoft.com/en-us/trustcenter/privacy)和 [Microsoft 安全性](https://www.microsoft.com/en-us/trustcenter/security/)方法进行开发。  

Microsoft Intune 与 Microsoft Azure 服务团队采用相同的技术和组织措施来抵御数据泄露进程。

有关详细信息，请参阅[服务信任门户](https://www.microsoft.com/en-us/TrustCenter/stp)。

Intune 使用数据最小化技术，如

- aggregation
- 某些功能的可选数据收集
- 降低数据的准确性或敏感性

Intune 还使用 RBAC 和 JiT 等技术保护支持事件，以确保在默认情况下实施数据保护。 

### <a name="data-breach-reporting"></a>数据泄露报告

发现可报告客户安全事件 (CRSI) 时，客户会收到通知。 此过程包括与 Microsoft O365 团队合作向使用 Intune 的任何 Microsoft O365 客户下达泄露通知。

## <a name="data-sharing"></a>数据共享

当租户管理员打开某些功能（如 Apple 设备注册计划）时，即表示管理员允许 Microsoft Intune 与相应的第三方共享数据。 在此情况下，Intune 可能与以下各方共享个人数据：

- 作为 Microsoft 代理的第三方。
- 非 Microsoft 代理的第三方（仅限租户管理员显式授予 Intune 执行此操作的权限时）。

作为 Microsoft 代理的所有第三方都包含在[联机服务分包商列表](https://aka.ms/Online_Serv_Subcontractor_List)中。

与此类实体共享数据是为了对客户和技术支持提供帮助，进行服务维护及其他操作。

租户与第三方签订的合同用于管理第三方服务中保留的 Intune 个人数据。 该合同还为 Intune 授予将数据传输到第三方服务的权限。  

有关与特定第三方共享的数据的信息，请参阅以下文章：
- [Intune 向 Apple 发送的数据](data-intune-sends-to-apple.md)
- [Intune 向 Google 发送的数据](data-intune-sends-to-google.md)
- [Apple 发送到 Intune 的数据](data-apple-sends-to-intune.md)
- [Google 发送到 Intune 的数据](data-google-sends-to-intune.md)
- [Jamf Pro 向 Intune 发送的数据](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>System Center Configuration Manager数据共享

Microsoft Intune 不与 System Center Configuration Manager 共享任何数据。 System Center Configuration Manager 是由客户直接部署、管理和运行的本地产品。 Configuration Manager 收集的诊断和使用情况数据仅用于改进将来版本的安装体验、质量和安全性。

有关详细信息，请参阅 [SCCM 的诊断和使用情况数据](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)。 


## <a name="next-steps"></a>后续步骤

了解如何在 Intune 中[查看和更正](privacy-data-view-correct.md)个人数据。
