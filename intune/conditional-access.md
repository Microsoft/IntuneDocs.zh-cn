---
title: "使用 Microsoft Intune 进行条件访问"
titlesuffix: 
description: "了解如何在 Microsoft Intune 中定义用户、设备和应用访问公司资源必须满足的条件。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/06/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08589f3d9186699ce5241579cc1879be2d442e3d
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="whats-conditional-access"></a>什么是条件性访问？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

条件访问是指控制允许连接到电子邮件和公司资源的设备和应用的方式。 在本主题中，了解基于设备和基于应用的条件访问，并查找通过 Intune 使用条件访问的常见方案。

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
