---
title: "使用 Intune 将设备恢复为出厂设置"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 将所管理的设备恢复为出厂设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44f69179f76c8d5eeca1594485ca3a9c1b036188
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>将 Intune-托管设备恢复为出厂设置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**恢复出厂设置** - 将设备恢复为其默认设置。 Intune 不再管理该设备，且公司和个人数据都被删除。 不能撤消此操作。

## <a name="supported-platforms"></a>受支持的平台

- Windows - Windows 8.1 及更高版本（非 EAS 托管设备）支持
- Windows Phone - 支持
- iOS - 支持
- macOS - 不支持
- Android - 支持（不支持 Android for Work）

## <a name="how-to-reset-a-device-to-factory-settings"></a>如何将设备恢复出厂设置

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理的设备列表中选择一台设备，然后选择“恢复出厂设置”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。

