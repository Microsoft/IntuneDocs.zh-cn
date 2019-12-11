---
title: Microsoft Intune 条件访问
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中定义用户、设备和应用访问公司资源必须满足的条件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188282"
---
# <a name="learn-about-conditional-access-and-intune"></a>了解条件访问和 Intune

使用条件访问，可以控制可连接到电子邮件和公司资源的设备和应用。 

企业移动性 + 安全性 (EMS) 不是一个独立的产品。 它是一个解决方案，涉及作为 EMS 的一部分的所有服务和产品。 条件访问提供了精细的访问控制用以保护公司数据安全的同时，又考虑到了用户的体验，允许他们从任何设备、任何位置以最方便的方式完成工作。

你可以根据位置、设备、用户状态和应用程序敏感度来定义获取公司数据访问权限的条件。

> [!NOTE]
> 条件性访问还会将其功能扩展到 [Office 365 服务](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access)。

![条件访问图](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>使用 Intune 的条件访问

条件访问是 Azure Active Directory Premium 许可证附带的 Azure Active Directory 功能。 Intune 通过向解决方案添加移动设备符合性和移动应用管理来增强此功能。 

![使用 EMS 时的 Intune 和条件访问](./media/conditional-access/intune-with-ca-1.png)

使用 Intune 条件访问的方式：

- **基于设备的条件访问**

  - 本地 Exchange 的条件访问

  - 基于网络访问控制的条件访问

  - 基于设备风险的条件访问

  - Windows 电脑的条件访问

    - 公司拥有的设备

    - 自带设备办公 (BYOD)

- **基于应用的条件访问**

## <a name="next-steps"></a>后续步骤

[使用 Intune 条件访问的常见方式](conditional-access-intune-common-ways-use.md)
