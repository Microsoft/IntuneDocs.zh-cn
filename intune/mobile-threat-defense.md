---
title: Mobile Threat Defense 与 Microsoft Intune
titleSuffix: Microsoft Intune
description: 结合使用 Intune Mobile Threat Defense (MTD) 和 Mobile Threat Defense 合作伙伴，保护对基于设备风险的公司资源的访问权限。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73c8167c91129d79a98674a92e7ccc5487a6b283
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885083"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>什么是 Mobile Threat Defense 与 Intune 的集成？
Intune 可以集成来自移动威胁防御供应商的数据，作为合规性策略和条件访问规则的信息源。 使用此信息，可通过阻止存在风险的移动设备的访问，来帮助保护 Exchange 和 SharePoint 等公司资源。  

## <a name="what-problem-does-this-solve"></a>还可以解决那些问题？
集成来自移动威胁防御供应商的信息可帮助保护公司资源免受对移动平台造成影响的风险威胁。  

通常，公司会积极保护电脑免受漏洞影响和恶意攻击，但通常不会监视和保护移动设备。 移动平台内置有保护（如应用隔离和审查使用者应用商店），同时这些平台仍易受到复杂攻击。 越来越多的员工将设备用于工作并访问敏感信息，因此移动威胁防御供应商提供的信息可帮助保护设备和资源免受日益复杂的攻击。  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 连接器的工作原理是什么？

Intune 使用移动威胁防御连接器在 Intune 和所选的移动威胁防御供应商之间创建通信通道。 Intune 移动威胁防御合作伙伴为移动设备提供直观且易于部署的应用程序。 这些应用程序会主动扫描和分析与 Intune 共享的威胁信息。 Intune 可将此数据用于制作报表或强制实施策略。  

例如：连接的移动威胁防御应用会向移动威胁防御供应商报告，指示网络上的电话当前连接到易受中间人攻击的网络。 此信息会划分到合适的风险级别：低、中或高。 之后，此风险级别会与 Intune 中所设置的允许的风险级别进行比较。 根据比较结果，可以在设备受到威胁时撤销对所选资源的访问。

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune 收集哪些数据用于移动威胁防御？

启用后，Intune 将从个人和公司拥有的设备收集应用清单信息，这些信息可供移动威胁防御 (MTD) 提供程序提取，例如 Lookout for Work。 可通过 iOS 设备的用户收集应用清单。

此服务为选择性加入；默认情况下不会共享任何应用清单信息。 Intune 管理员必须在服务设置中为 iOS 设备启用“应用同步”，然后才能共享应用清单信息。

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

## <a name="sample-scenarios"></a>示例方案

移动威胁防御解决方案判定设备受到感染时：

![显示 Mobile Threat Defense 受感染设备的图像](./media/MTD-image-1.png)

修正设备时授予访问权限：

![显示授予 Mobile Threat Defense 访问权限的图像](./media/MTD-image-2.png)

> [!NOTE] 
> 不支持对 Intune 使用多个移动威胁防御供应商。 启用多个 MTD 工具将强制安装所有 MTD 应用并使其在多台设备中扫描威胁。

## <a name="mobile-threat-defense-partners"></a>移动威胁防御合作伙伴

了解如何根据设备、网络和应用程序风险，通过以下工具保护对公司资源的访问：

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile 威胁防御](wandera-mtd-connector.md)
