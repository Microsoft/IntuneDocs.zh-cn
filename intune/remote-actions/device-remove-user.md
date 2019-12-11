---
title: 通过 Microsoft Intune 从 iOS 设备中删除用户
titleSuffix: ''
description: 了解如何通过 Intune 从共享 iOS 设备中删除用户。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713162"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>从共享 iOS 设备中删除用户


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“删除用户”操作从共享的 iPad 设备上的本地缓存中删除所选用户  。 还必须使用 [iOS 教育版配置文件](../fundamentals/education-settings-configure-ios.md) 设置 IPad 设备来管理 iOS Classroom 应用。 

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS - iOS 9.3 及更高版本（仅共享 iPad 设备）支持
- macOS - 不支持
- Android - 不支持

## <a name="remove-a-user"></a>删除用户

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备” > “所有设备”   。
3. 在所管理设备的列表中，选择一个 iOS 设备。
4. 在设备的窗格中，选择“用户”  。
5. 在列表中，右键单击想要删除的用户，然后选择“删除用户”  。

## <a name="next-steps"></a>后续步骤

- 若要查看“删除用户”操作的状态，请选择“设备” > “设备操作”    。
