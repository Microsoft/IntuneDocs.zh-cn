---
title: "使用 Microsoft Intune 重置 Windows 10 设备 - Azure | Microsoft Docs"
description: "通过 Microsoft Intune 使用“全新启动”删除或卸载 Windows 10 电脑的应用，包括来自 OEM 的预安装应用。 也可以使用“是否保留用户数据”设置，保留主文件夹内容。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>使用“全新启动”重置使用 Intune 的 Windows 10 设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“全新启动”设备操作将删除在运行 Windows 10 创意者更新的电脑上安装的所有应用。 然后，电脑将自动更新到 Windows 的最新版。

此操作有助于删除新电脑通常安装的预安装 (OEM) 应用。 若要保留用户的主文件夹的内容并仅删除应用和设置，请使用 `if user data is retained` 设置。

> [!IMPORTANT]
> “全新启动”将从 Intune 注销设备，但设备仍联接 Azure Active Directory。

## <a name="use-fresh-start"></a>使用“全新启动”

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备”和“所有设备”。
4. 从管理的设备列表中，选择一个 Windows 10 桌面设备，然后选择“全新启动”。

## <a name="next-steps"></a>后续步骤

若要查看此操作的状态，请选择“设备操作”（“Microsoft Intune” > “设备”）。