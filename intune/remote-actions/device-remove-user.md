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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f418149d8640f7fd663f0bbf4b3151ffb428a75e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728476"
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

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“设备”   。
4. 在“设备”窗格中，选择“所有设备”   。
5. 在所管理设备的列表中，选择一个 iOS 设备。
6. 在设备的窗格中，选择“用户”  。
7. 在列表中，右键单击想要删除的用户，然后选择“删除用户”  。

## <a name="next-steps"></a>后续步骤

- 若要查看“删除用户”操作的状态，请选择“设备” > “设备操作”    。
