---
title: "Mobile Threat Defense 与 Microsoft Intune"
titleSuffix: 
description: "结合使用 Intune Mobile Threat Defense (MTD) 和 Mobile Threat Defense 合作伙伴，保护对基于设备风险的公司资源的访问权限。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2eaba4f04d6a1daedf40b7b37d2b44ed5aff4533
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>什么是 Mobile Threat Defense 与 Intune 的集成？


通过Intune 移动威胁防御连接器，可利用所选的移动威胁防御供应商作为符合性策略和条件性访问规则的信息源。 由此，IT 管理员可增强公司资源（如 Exchange 和 Sharepoint）的安全性，特别是易受攻击的移动设备的安全性。

## <a name="what-problem-does-this-solve"></a>还可以解决那些问题？

公司需要针对出现的威胁保护敏感数据，包括物理的、基于应用的和基于网络的威胁以及操作系统漏洞。

过去，公司在保护电脑免受攻击方面一直比较主动，但并未监视和保护移动设备。 尽管移动平台内置有保护（如应用隔离和审查使用者应用商店），但这些平台仍易受到复杂攻击。 如今，更多员工使用设备完成工作，并需要访问敏感信息。 因此，必须保护设备免受日益复杂的攻击。

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 连接器的工作原理是什么？

连接器会在 Intune 和所选的移动威胁防御供应商之间创建信道，进而保护公司资源。 Intune 移动威胁防御合作伙伴为移动设备提供了直观且易于部署的应用程序，可出于报告或强制目的主动扫描和分析威胁信息与 Intune 共享。 

例如，如果连接的移动威胁防御应用向移动威胁防御供应商报告，称网络上的某电话当前连接到易受中间人攻击的网络，则此信息将进行共享并分类为相应的风险级别（中/低/高），然后可将该级别与 Intune 中配置的允许风险级别限额进行比较，确定设备受到威胁时是否应取消对某些所选资源的访问。

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune 收集哪些数据用于移动威胁防御？

Intune 从个人和公司所有的设备收集应用清单信息，这些信息可供移动威胁防御 (MTD) 提取，例如 Lookout for Work。 可通过 iOS 11+ 设备的用户收集应用清单。

**应用清单**  
清单（来自公司所有的 iOS 11+ 和个人所有的设备）将发送给 MTD 服务提供程序。 应用清单中的数据包括：

 - 应用 ID
 - 应用版本
 - 应用内部版本号
 - 应用程序名称
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
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
