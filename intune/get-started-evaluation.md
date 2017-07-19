---
title: "Intune 入门"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>什么是 Microsoft Intune？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Azure 门户中的 Microsoft Intune](./media/generic-intune-azure.png)

Microsoft Intune 是 Azure 的最新服务之一。 它提供用于管理组织的移动设备、电脑和[定期更新](whats-new.md)的应用的工具。 除了新式 Azure 控制台外，Intune 还允许使用经典控制台。 经典控制台是 Intune 的第一个版本，你仍然可以其中转到[使用 Intune 软件客户端管理 Windows 电脑](/intune-classic/deploy-use/pc-management-comparison.md)。 使用 Silverlight 构建的经典门户用于少量任务。 所有其他任务（包括移动设备和应用管理）需在 Azure 门户中完成。 入门指南将指导成功在 Azure 门户中使用 Intune 所需完成的基本任务。

![“帮助和支持”边栏选项卡位于 Intune 左侧边栏的操作列表底部。](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>Azure 门户中的 Intune 提供什么？

Azure 门户中的 Intune 为你提供：

* 用于所有[企业移动性 + 安全性 (EMS) 组件](https://docs.microsoft.com/enterprise-mobility-security)的集成控制台
* 支持[新式 Web 浏览器](supported-devices-browsers.md)的通过 Web 标准构建的基于 HTML 的控制台
* 提供跨所有 Azure 应用程序的兼容性的 [Azure Active Directory 组](groups-get-started.md)
* 通过 [Microsoft Graph API](intune-graph-apis.md) 实现自动化

## <a name="prerequisites"></a>先决条件

在开始之前，必须激活 Intune 管理员和租户帐户。 可以在[此处](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)注册这些账户。 当前订阅者还可以在实时租户中完成这些活动。 请确保仅在测试设备上进行操作！

为了完成指南中的所有任务，还需要确保你是组织的全局管理员。
