---
title: 通过 Microsoft Intune 从 iOS/iPadOS 设备中删除用户
titleSuffix: ''
description: 了解如何通过 Intune 从共享 iOS/iPadOS 设备中删除用户。
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
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415567"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>从共享 iOS/iPadOS 设备中删除用户


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“删除用户”操作从共享的 iPad 设备上的本地缓存中删除所选用户  。 还必须使用 [iOS/iPadOS 教育版配置文件](../fundamentals/education-settings-configure-ios.md)设置 iPad 设备来管理 iOS/iPadOS Classroom 应用。 

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS/iPadOS - iOS/iPadOS 9.3 及更高版本（仅共享 iPad 设备）支持
- macOS - 不支持
- Android - 不支持

## <a name="remove-a-user"></a>删除用户

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备” > “所有设备”   。
3. 在所管理设备的列表中，选择一个 iOS/iPadOS 设备。
4. 在设备的窗格中，选择“用户”  。
5. 在列表中，右键单击想要删除的用户，然后选择“删除用户”  。

## <a name="next-steps"></a>后续步骤

- 若要查看“删除用户”操作的状态，请选择“设备” > “设备操作”    。
