---
title: "使用 Microsoft Intune 查看设备 - Azure | Microsoft Docs"
description: "查看设备的详细信息，包括操作系统、存储空间、制造商和型号等。 在 Azure 的 Microsoft Intune 中获取已安装应用的列表、检查符合性策略、设置 TeamViewer 等等。 类似于查看管理设备的清单。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 934ba0853f8bee851f7027580c276a9fff911b7f
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看设备详细信息

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“设备”功能可提供管理设备的其他详细信息，包括其硬件和已安装的应用。 

本文介绍如何在 Azure 门户中查看所有设备及其属性。

## <a name="view-your-device-details"></a>查看设备详细信息

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备”。 “设备”中有多个选项：

  - **概述** - 获得有关已注册设备的信息，以及每个设备运行的操作系统的相关信息。
  - **管理** - 若要查看管理的所有设备，请选择“所有设备”或“Azure AD 设备”。
    在列表中，选择一个设备。 此步骤将打开 <设备名称> 概述，你可以在其中选择以下项：
    - **概述** - 签入时，如果设备为自带设备 (BYOD)，请查看设备名称、所有者以及其他详细信息
    - **硬件** - 可查看设备可用存储空间、型号、制造商以及其他详细信息
    - **发现的应用** - 列出 Intune 发现的安装在设备上的所有应用
    - **设备符合性** - 显示已分配给设备的所有符合性策略的状态
    - **设备配置** - 显示已分配给设备的所有设备配置策略的符合性状态
- **监视** - 选择“设备操作”查看在所管理的设备上执行的操作列表，以及它们的当前状态。 **审核日志**显示不同任务的状态。
- **安装程序** > **TeamViewer 连接器** - 使用 TeamViewer 软件在设备上配置远程管理。 有关详情，请参阅[针对 Intune 托管 Android 设备提供远程协助](device-profile-android-teamviewer.md)。

Intune 仅收集公司拥有的设备上的应用列表。 不检查个人设备上的应用。 对于 Windows 10 电脑，仅列出公司拥有的设备上的新型应用。 Intune 不会收集设备上的 Win32 应用的相关信息。 根据设备运营商使用情况，可能并不会收集所有应用。

## <a name="next-steps"></a>后续步骤
了解使用 Intune [管理设备](device-management.md)还可以执行哪些操作。
