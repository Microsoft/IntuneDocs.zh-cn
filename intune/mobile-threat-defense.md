---
title: "使用 Intune 的移动威胁防御"
titleSuffix: Azure portal
description: "根据设备风险，保护对公司资源的访问"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f9c28bbd06fbee620466d4f269fbb08d98bbcde2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="mobile-threat-defense-integration-with-intune"></a>使用 Intune 的移动威胁防御集成


通过Intune 移动威胁防御连接器，可利用所选的移动威胁防御供应商作为符合性策略和条件性访问规则的信息源。 由此，IT 管理员可增强公司资源（如 Exchange 和 Sharepoint）的安全性，特别是防御来自安全已受威胁的移动设备的攻击。

## <a name="what-problem-does-this-solve"></a>还可以解决那些问题？

公司需要针对出现的威胁保护敏感数据，包括物理的、基于应用的和基于网络的威胁以及操作系统漏洞。
过去，公司在保护电脑免受攻击方面一直比较主动，但并未监视和保护移动设备。 尽管移动平台内置有保护（如应用隔离和审查使用者应用商店），但这些平台仍易受到复杂攻击。 如今，更多员工使用设备完成工作，并需要访问敏感信息。 因此，需要保护设备免受日益复杂的攻击。

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune 移动威胁防御连接器如何工作？

连接器会在 Intune 和所选的移动威胁防御供应商之间创建信道，进而保护公司资源。 Intune 移动威胁防御合作伙伴为移动设备提供了直观且易于部署的应用程序，可出于报告或强制目的主动扫描和分析威胁信息与 Intune 共享。 例如，如果连接的移动威胁防御应用向移动威胁防御供应商报告，称你网络上的某电话当前连接到易受中间人攻击的网络，则此信息将进行共享并分类为相应的风险级别（中/低/高），然后可将该级别与 Intune 中配置的允许风险级别限额进行比较，确定设备受到威胁时是否应取消你对某些所选资源的访问。

## <a name="sample-scenarios"></a>示例方案

移动威胁防御解决方案判定设备受到感染时：

![移动威胁防御感染的设备](./media/MTD-image-1.png)

修正设备时授予访问权限：

![授予移动威胁防御访问权限](./media/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>移动威胁防御合作伙伴

了解如何根据设备、网络和应用程序风险，通过以下工具保护对公司资源的访问：

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)