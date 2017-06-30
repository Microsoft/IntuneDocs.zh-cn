---
title: "重置使用 Intune 的 Windows 10 设备"
titleSuffix: Intune on Azure
description: "了解如何使用“全新启动”重置运行 Intune 的 Windows 10 电脑。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 590472c0ab9f0103d72730b8ab01dc324c852a7a
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>使用“全新启动”重置使用 Intune 的 Windows 10 设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“全新启动”设备操作可删除在运行创意者更新的 Windows 10 电脑上安装的所有应用，然后将电脑自动更新到 Windows 的最新版本。
这可用于删除新电脑通常附带的预先安装的 (OEM) 应用。 发出此设备操作时可以配置是否保留用户数据。 在这种情况下，应用和设置已删除，但会保留用户主页文件夹的内容。

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中，选择一项 Windows 10 桌面设备，然后选择“全新启动”设备远程操作。

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。


