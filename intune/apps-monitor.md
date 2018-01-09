---
title: "如何监视应用信息和分配"
titlesuffix: Azure portal
description: "将应用分配给用户或设备后，请使用此信息来帮助你监视其状态。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cb95319d2574116d480de9bdf74ef36129d0970f
ms.sourcegitcommit: 9fabf1a8db53842f7b00762374de5b137158ee25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>如何使用 Microsoft Intune 监视应用信息和分配

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 提供了许多可以用于监视所托管应用的属性及其分配状态的方法。

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 在“移动应用”工作负荷中，在“管理”组中选择“应用”。
5. 在应用边栏选项卡列表中选择应用。 然后将看到<应用名称> “设备安装状态”边栏选项卡。

## <a name="app-overview-blade"></a>应用概述边栏选项卡

可使用 <应用名称> “设备安装状态”边栏选项卡查看环境中应用状态的相关详细信息。

### <a name="essentials"></a>Essentials

“软件包”部分包含有关该应用的以下信息：

 - **发布者**  
应用发布者。
 - **操作系统**  
应用的操作系统（Windows、iOS、Android 等）
 - **创建**  
创建此修订版本的时间。
 - **已分配**  
“是”或“否”表示是否已分配了应用。

### <a name="status"></a>状态
每个图表显示以下状态的计数：

 - **已安装**  
已安装的应用数。
 - **未安装**  
未安装的应用数。
 - **安装挂起**  
正在安装的应用数。
 - **已失败**  
失败的安装次数。
 - **未知**  
状态未知的应用数。

### <a name="device-status"></a>设备状态

设备状态。 显示设备上应用的安装状态的环形图。 单击图表打开关于设备状态的详细信息列表。 详细信息表包括以下列：

 - **设备名**  
允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。
 - **用户名**  
用户的名称。
 - **平台**  
设备的操作系统（Windows、iOS、Android 等）
 - **版本**  
应用的版本号。 对于业务线应用，显示该应用的完整版本号。 完整版本号标识应用的特定版本。 该号码显示为“版本号(内部版本号)”。 例如：2.2(2.2.17560800)
 - **状态**  
应用的状态。
 - **状态详细信息**  
状态的详细信息。
 - **上次签入**  
上次与 Intune 同步的设备日期。


### <a name="user-status"></a>用户状态

用户状态。 显示用户的应用安装状态的环形图。 单击图表打开关于设备状态的详细信息列表。 详细信息表包括以下列：
 - **名称**  
Azure AD 中的用户名称。
 - **用户名**  
用户的唯一名称。
 - **安装**  
用户使用的应用安装数。
 - **失败**  
用户安装失败的次数。
 - **未安装**  
用户未安装的应用数。


## <a name="next-steps"></a>后续步骤

要了解有关使用 Intune 数据的详细信息，请参阅[使用 Intune 数据仓库](reports-nav-create-intune-reports.md)。