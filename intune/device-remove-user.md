---
title: "使用 Intune 从 iOS 设备中删除用户"
titlesuffix: Azure portal
description: "了解如何通过 Intune 从共享 iOS 设备中删除用户。”"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 979614aaa450493ea0b5cc2a1baaccc10a6dd028
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>通过 Intune 从共享 iOS 设备中删除用户


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“删除用户”操作会从使用 [iOS 教育配置文件](education-settings-configure-ios.md)配置的用于管理 iOS 课堂应用的共享 iPad 设备上的本地缓存中删除选择的用户。 

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS - iOS 9.3 及更高版本（仅共享 iPad 设备）支持
- macOS - 不支持
- Android - 不支持

## <a name="how-to-remove-a-user"></a>如何删除用户

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备”边栏选项卡上，选择“所有设备”。
5. 从所管理设备的列表中，选择一个 iOS 设备。
6. 在该设备的边栏选项卡上，选择“用户”。
7. 从列表中，右键单击想要删除的用户，然后选择“删除用户”。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
