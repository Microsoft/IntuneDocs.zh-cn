---
title: 如何监视应用信息和分配
titlesuffix: Microsoft Intune
description: 将应用分配给用户或设备后，请使用此信息来帮助你监视其状态。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01b7972a6a4dbb641f4c656190324d8572f9010c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>如何使用 Microsoft Intune 监视应用信息和分配

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 提供了许多可以用于监视所托管应用的属性及其分配状态的方法。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”组。
3. 在“管理”组中选择“移动应用”，然后选择“应用”。
5. 在应用列表中，选择要监视的应用。 随后将看到“应用”边栏选项卡，其中概述了设备状态和用户状态。

## <a name="app-overview-blade"></a>应用概述边栏选项卡

可使用特定应用边栏选项卡查看环境中应用状态的相关详细信息。

### <a name="essentials"></a>Essentials
“软件包”部分包含有关该应用的以下信息：

 | **应用详细信息**            | **描述**                                                      |
|------------------------|------------------------------------------------------------------|
| **发布者**          | 应用发布者。                                            |
| **操作系统**   | 应用的操作系统（Windows、iOS、Android 等） |
| **创建时间**             | 创建此修订版本的日期和时间。                         |
| **已分配**           | “是”或“否”表示是否已分配了应用。                  |

### <a name="device-and-user-status-graphs"></a>设备和用户状态关系图
此关系图显示以下状态的数目：

| **设备状态**       | **描述**                                       |
|-----------------------|-------------------------------------------------------|
| **已安装**         | 已安装的应用数。                         |
| **未安装**     | 未安装的应用数。                     |
| **已失败**            | 失败的安装次数。                   |
| **安装挂起**   | 正在安装的应用数。 |
| **不适用**           | 其状态不适用的应用数。            |

### <a name="device-install-status"></a>设备安装状态

在“监视器”部分选择“设备安装状态”时，显示设备状态列表。 详细信息表包括以下列：

| **设备列**      | **描述**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **设备名**      | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。                                                                       |
| **用户名**        | 用户的名称。                                                                                                                                                                                                                                      |
| **平台**         | 设备的操作系统（Windows、iOS、Android 等）                                                                                                                                                                                           |
| **版本**          | 应用的版本号。 对于业务线应用，显示该应用的完整版本号。 完整版本号标识应用的特定版本。 该号码显示为“版本号(内部版本号)”。 例如：2.2(2.2.17560800) |
| **状态**           | 应用的状态。                                                                                                                                                                                                                                     |
| **状态详细信息**   | 状态的详细信息。                                                                                                                                                                                                                                     |
| **上次签入**    | 上次与 Intune 同步的设备日期。                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>用户安装状态

在“监视器”部分选择“用户安装状态”时，显示用户状态列表。 详细信息表包括以下列：

| **用户列**     | **描述**                           |
|---------------------|-------------------------------------------|
| **名称**            | Azure AD 中的用户名称。         |
| **用户名**       | 用户的唯一名称。              |
| **安装**   | 用户使用的应用安装数。 |
| **失败**        | 用户安装失败的次数。     |
| **未安装**   | 用户未安装的应用数。 |


## <a name="next-steps"></a>后续步骤

- 要了解有关使用 Intune 数据的详细信息，请参阅[使用 Intune 数据仓库](reports-nav-create-intune-reports.md)。
- 若要了解应用配置策略，请参阅 [Intune 的应用配置策略](app-configuration-policies-overview.md)。