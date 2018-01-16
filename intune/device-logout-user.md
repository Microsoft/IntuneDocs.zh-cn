---
title: "使用 Intune 注销 iOS 设备用户"
titlesuffix: Azure portal
description: "了解如何使用 Intune 注销当前的 iOS 设备用户。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f02e4fb0da11a251c33c6ee1e44ba07848f69f9b
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>注销 Intune 管理的 iOS 设备上的当前用户


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


“注销当前用户”操作会注销共享 iPad 设备上的当前用户，该设备使用 [iOS 教育配置文件](education-settings-configure-ios.md)进行配置，用于管理 iOS 课堂应用。 

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS - iOS 9.3 及更高版本（仅共享 iPad 设备）支持
- macOS - 不支持
- Android - 不支持

## <a name="how-to-logout-the-current-user"></a>如何注销当前用户

1.  登录 Azure 门户。
2.  选择“更多服务” > “监视 + 管理” > “Intune”。
3.  在 Intune 边栏选项卡上，选择“设备”。
4.  在“设备和组”边栏选项卡上，选择“所有设备”。
5.  从管理的设备列表中，选择一台 iOS 设备，然后选择“注销当前用户”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
