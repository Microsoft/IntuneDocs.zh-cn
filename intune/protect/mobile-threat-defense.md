---
title: Mobile Threat Defense 与 Microsoft Intune
titleSuffix: Microsoft Intune
description: 结合使用 Intune Mobile Threat Defense (MTD) 和 Mobile Threat Defense 合作伙伴，保护对基于设备风险的公司资源的访问权限。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73057588"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>使用 Intune 的移动威胁防御集成

Intune 可以集成来自移动威胁防御 (MTD) 供应商的数据，作为设备符合性策略和设备条件访问规则的信息源。 使用此信息，可通过阻止存在风险的移动设备的访问，来帮助保护 Exchange 和 SharePoint 等公司资源。

Intune 可以使用 Intune 应用保护策略将此相同的数据用作未注册设备的源。 因此，管理员可以使用此信息帮助保护[受 Microsoft Intune 保护的应用](~/apps/apps-supported-intune-apps.md)中的公司数据，并发出阻止或选择性擦除。

## <a name="protect-corporate-resources"></a>保护公司资源

集成来自 MTD 供应商的信息可帮助保护公司资源免受对移动平台造成影响的风险威胁。  

通常，公司会积极保护电脑免受漏洞影响和恶意攻击，但通常不会监视和保护移动设备。 移动平台内置有保护（如应用隔离和审查使用者应用商店），同时这些平台仍易受到复杂攻击。 越来越多的员工将设备用于工作并访问敏感信息，因此 MTD 供应商提供的信息可帮助保护设备和资源免受日益复杂的攻击。

## <a name="intune-mobile-threat-defense-connectors"></a>Intune 移动威胁防御连接器

Intune 使用移动威胁防御连接器在 Intune 和所选的 MTD 供应商之间创建通信通道。 Intune MTD 合作伙伴为移动设备提供直观且易于部署的应用程序。 这些应用程序会主动扫描和分析与 Intune 共享的威胁信息。 Intune 可将此数据用于制作报表或强制实施策略。

例如：连接的 MTD 应用会向 MTD 供应商报告，指示网络上的电话当前连接到易受中间人攻击的网络。 此信息会划分到合适的风险级别：低、中或高。 之后，此风险级别会与 Intune 中所设置的允许的风险级别进行比较。 根据比较结果，可以在设备受到威胁时撤销对所选资源的访问。

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Intune 收集用于移动威胁防御的数据

启用后，Intune 将从个人和公司拥有的设备收集应用清单信息，这些信息可供 MTD 提供程序提取，例如 Lookout for Work。 可通过 iOS 设备的用户收集应用清单。

此服务为选择性加入；默认情况下不会共享任何应用清单信息。 Intune 管理员必须在移动威胁防御连接器设置中启用”适用于 iOS 设备的应用同步”，然后才能共享应用清单信息  。

**应用清单**  
如果为 iOS 设备启用“应用同步”，来自公司和个人拥有的 iOS 设备的清单将发送给 MTD 服务提供程序。 应用清单中的数据包括：

- 应用 ID
- 应用版本
- 应用内部版本号
- 应用名称
- 应用程序包大小
- 应用动态大小
- 应用是否经过验证
- 应用是否受管理

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>使用设备符合性策略的已注册设备的示例方案

移动威胁防御解决方案判定设备受到感染时：

![显示 Mobile Threat Defense 受感染设备的图像](./media/mobile-threat-defense/MTD-image-1.png)

修正设备时授予访问权限：

![显示授予 Mobile Threat Defense 访问权限的图像](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>使用 Intune 应用保护策略的未注册设备的示例方案

移动威胁防御解决方案判定设备受到感染时：<br>
![显示 Mobile Threat Defense 受感染设备的图像](./media/mobile-threat-defense/MTD-image-3.png)

修正设备时授予访问权限：<br>
![显示授予 Mobile Threat Defense 访问权限的图像](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> 可以将多个移动防御供应商用于单个 Intune 租户。 但是，当两个或多个供应商配置为用于同一平台时，运行该平台的所有设备都必须安装每个 MTD 应用并扫描威胁。 从任何已配置的应用提交扫描失败都会导致设备被标记为不符合。 

## <a name="mobile-threat-defense-partners"></a>移动威胁防御合作伙伴

了解如何根据设备、网络和应用程序风险，通过以下工具保护对公司资源的访问：

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile 威胁防御](wandera-mtd-connector.md)
