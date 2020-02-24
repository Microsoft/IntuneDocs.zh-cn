---
title: 使用 Microsoft Intune 重启设备 - Azure | Microsoft Docs
description: 通过“重启”远程操作，在 Azure 门户中使用 Microsoft Intune 重启 Windows 和 iOS/iPadOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54fa0f796e96a2487793197cbbbe548fd8490856
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415618"
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 远程重启设备


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“重新启动”  设备操作将重启你选择的设备（在 5 分钟内）。 设备所有者不会获得重新启动的自动通知，而且他们的工作内容可能丢失。

## <a name="supported-platforms"></a>受支持的平台

- Windows - Windows 8.1 及更高版本支持
- Windows Phone - Windows Phone 8.1 及更高版本支持
- Android 展台设备 - Android 7.0 及更高版本支持
- iOS/iPadOS - 支持

    > [!Note]  
    > 此命令需要受监督的设备和“设备锁定”访问权限  。 设备会立即重启。 密码锁定的 iOS/iPadOS 设备重启后不会重新加入 Wi-Fi 网络。 重启后，设备可能无法与服务器进行通信。
- macOS - 不支持
- Android 和 Android 工作配置文件设备 - 不支持

## <a name="restart-a-device"></a>重启设备

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“设备” > “所有设备”   。
4. 在所管理设备的列表中，选择一个设备，然后选择“重启” > “是”   。

## <a name="next-steps"></a>后续步骤

- 若要查看“重新启动”设备操作的状态，请选择“设备” > “设备操作”    。
