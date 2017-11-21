---
title: "使用 Intune 的条件访问"
titlesuffix: Azure portal
description: "了解如何定义用户和设备在 Microsoft Intune 中访问公司资源必须满足的条件。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1cd12a105142d5e537da487e3bd9297ef83ddcb3
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="whats-conditional-access"></a>什么是条件性访问？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题将介绍条件性访问，因为它适用于企业移动性 + 安全性 (EMS)，然后介绍使用 Intune 时的条件性访问常见场景。

企业移动性 + 安全性 (EMS) 条件性访问不是一款独立的产品，它是作为 EMS 一部分的涉及全部服务和产品的解决方案。 它提供了精细的访问控制用以保护公司数据安全的同时，又考虑到了用户的体验，允许他们从任何设备、任何位置以最方便的方式完成工作。

你可以根据位置、设备、用户状态和应用程序敏感度来定义获取公司数据访问权限的条件。

> [!NOTE] 
> 条件性访问还会将其功能扩展到 [Office 365 服务](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/)。

![条件性访问体系结构图表](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>使用 Intune 的条件访问

Intune 添加了移动设备符合性和应用管理策略，以支持 EMS 条件访问解决方案。

![使用 EMS 时的 Intune 和条件性访问](./media/intune-with-ca-1.png)

通过 Intune 使用条件性访问的方式：

-   **基于设备的条件性访问**

    -   Exchange 内部部署的条件性访问

    -   基于网络访问控制的条件性访问

    -   基于设备风险的条件性访问

    -   Windows 电脑的条件访问

        -   公司拥有的设备

        -   自带设备办公 (BYOD)

-   **基于应用的条件性访问**

## <a name="next-steps"></a>后续步骤

[通过 Intune 使用条件性访问的常见方式](conditional-access-intune-common-ways-use.md)
