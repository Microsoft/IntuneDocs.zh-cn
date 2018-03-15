---
title: "查看 Intune 设备清单"
titlesuffix: Azure portal
description: "了解如何查看使用 Intune 管理的设备，并了解其硬件和已安装的应用。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772e2b1380626384d618e653b90b31a1f421eb72
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-view-intune-device-inventory"></a>如果查看 Intune 设备清单


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“设备”工作负载可让你深入了解所管理的设备，包括其硬件功能以及安装的应用。 

要查看设备清单，请执行以下操作：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 边栏选项卡上，选择“设备”。

现在，选择下列选项之一：

- **概述** - 获得有关已注册设备的信息，以及每个设备运行的操作系统的相关信息。
- **管理** - 选择“所有设备”查看所管理的所有设备列表。
    选择列表中的某个设备，打开<设备名称> “概述”边栏选项卡，可在其中选择下列选项之一：
    - **概述** - 查看有关设备的常规信息，包括设备名称、所有者、是否是 BYOD 设备、登录时间等。
    - **硬件** - 请查看有关设备的详细信息，包括其可用存储空间、型号和制造商等。
    - **发现的应用** - 显示 Intune 发现的安装在设备上的所有应用列表。
    - **设备符合性** - 显示已分配给设备的所有符合性策略的符合性状态。
    - **设备配置** - 显示已分配给设备的所有设备配置策略的符合性状态。
- **监视** - 选择“设备操作”查看在所管理的设备上执行的设备操作列表，以及它们的当前状态。
- **安装程序** > **TeamViewer 连接器** - 用于在使用 TeamViewer 软件的设备上配置远程管理。 有关详情，请参阅[针对 Intune 托管 Android 设备提供远程协助](/intune/device-profile-android-teamviewer)。

Intune 仅收集公司拥有的设备上的应用清单。 个人设备上的应用不会列入清单。 对于 Windows 10 电脑，仅收集公司拥有的设备上的新型应用清单。 Intune 不会收集设备上的 Win32 应用的相关信息。 可能不会收集所有清单项，这取决于设备所用的运营商。
