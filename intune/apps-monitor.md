---
title: "如何监视应用信息和分配"
titlesuffix: Azure portal
description: "将应用分配给用户或设备后，请使用此信息来帮助你监视其状态。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>如何使用 Microsoft Intune 监视应用信息和分配

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 提供了许多可以用于监视所托管应用的属性及其分配状态的方法。

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 在“移动应用”工作负荷中，在“管理”组中选择“应用”。
     
    ![“应用安装状态”边栏选项卡。](./media/monitor-apps.png)
5. 在应用边栏选项卡列表中选择应用。 然后将看到<应用名称> “设备安装状态”边栏选项卡。

设备安装状态报表包含以下列：

1.  **设备名称** 设备类型的名称。
2.  **用户名** 用户的名称。
3.   **平台** 安装在设备上的操作系统。
4.  **版本** 应用程序的版本号。
5.   **状态** 应用的可能状态包括：“已安装”、“未安装”、“安装挂起”和“错误”。
6. **状态详细信息** 设备上应用状态的可读说明。
7. **上次签入时间** 设备上次签入到 Intune 的时间。

然后，执行以下操作之一来详细了解应用及其分配。

## <a name="general"></a>常规

- **概述** - 提供应用的基本概述和关于该应用的任意分配状态的信息。 可以选择一个图表来打开“设备安装状态”或“用户安装状态”边栏选项卡，以获取更为详细的信息。

## <a name="manage"></a>管理计算机上的

- **属性** - 可以通过它查看和更改所选应用的相关信息。 有关应用属性的详细信息，请参阅[如何将应用添加到 Microsoft Intune](apps-add.md)。
- **分配** - 提供该应用分配情况的相关信息。 有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

## <a name="monitor"></a>监视

- **设备安装状态** - 提供已将所选应用分配到的各个设备的详细信息，包括设备名称、操作系统、设备上次签入 Intune 的时间及应用安装状态。
- **用户安装状态** - 提供已向其分配所选应用的用户的详细信息，包括用户在其所有设备上安装的应用数以及任意安装失败的相关信息。