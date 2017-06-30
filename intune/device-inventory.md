---
title: "查看 Intune 设备清单"
titleSuffix: Intune on Azure
description: "了解如何查看使用 Intune 管理的设备，并了解其硬件和已安装的应用。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: c1e7356e27a8e146b9629c4c2f13f0b1f6861e84
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="how-to-view-intune-device-inventory"></a>如果查看 Intune 设备清单


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“设备”工作负载可让你深入了解所管理的设备，包括其硬件功能以及安装的应用。 

要查看设备清单，请执行以下操作：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。

现在，选择以下选项之一：

- **概述** - 获得有关已注册设备的信息，以及每个设备运行的操作系统的相关信息。
- **管理** - 选择“所有设备”查看所管理的所有设备列表。
    选择列表中的某个设备，打开<设备名称> “概述”边栏选项卡，可在其中选择下列选项之一：
    - **概述** - 查看有关设备的常规信息，包括设备名称、所有者、是否是 BYOD 设备、上次登录时间等。

    - **硬件** - 请查看有关设备的详细信息，包括其可用存储空间、型号和制造商等。
    ![托管设备硬件清单](./media/hardware-inventory.png)
    - **检测到的应用程序** - 显示 Intune 发现的安装在设备上的所有应用列表。
    ![检测到的应用程序节点](./media/detected-applications.png)
- **监视** 选择“设备操作”查看在所管理的设备上执行的设备操作列表，以及这些操作的当前状态。
![监视设备操作](./media/monitor-device-actions.png)




