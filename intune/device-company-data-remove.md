---
title: "使用 Intune 从设备中删除公司数据"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 从设备中仅删除公司数据。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>从 Intune-托管设备中删除公司数据


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**删除公司数据** - 从设备中仅删除由 Intune 管理的公司数据。 不会删除设备中的个人数据。 该设备将不再由 Intune 管理，并且将不再能够访问公司资源（不受加入 Azure Active Directory 的 Windows 设备的支持）。

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理的设备列表中选择一台设备，然后选择“删除公司数据”设备远程操作。

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
