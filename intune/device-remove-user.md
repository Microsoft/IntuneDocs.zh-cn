---
title: 通过 Microsoft Intune 从 iOS 设备中删除用户
titlesuffix: ''
description: 了解如何通过 Intune 从共享 iOS 设备中删除用户。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 00733600555118533ef2754d0b2b37184f93b309
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189208"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>从共享 iOS 设备中删除用户


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

“删除用户”操作从共享的 iPad 设备上的本地缓存中删除所选用户。 还必须使用 [iOS 教育版配置文件](education-settings-configure-ios.md) 设置 IPad 设备来管理 iOS Classroom 应用。 

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS - iOS 9.3 及更高版本（仅共享 iPad 设备）支持
- macOS - 不支持
- Android - 不支持

## <a name="remove-a-user"></a>删除用户

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“设备”。
4. 在“设备”窗格中，选择“所有设备”。
5. 在所管理设备的列表中，选择一个 iOS 设备。
6. 在设备的窗格中，选择“用户”。
7. 在列表中，右键单击想要删除的用户，然后选择“删除用户”。

## <a name="next-steps"></a>后续步骤

- 若要查看“删除用户”操作的状态，请选择“设备” > “设备操作”。
