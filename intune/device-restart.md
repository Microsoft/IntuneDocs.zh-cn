---
title: 使用 Microsoft Intune 重启设备 - Azure | Microsoft Docs
description: 通过“重启”远程操作，在 Azure 门户中使用 Microsoft Intune 重启 Windows 和 iOS 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7e9ec9d309efb89badfc7b61f50d1b0e8a2c041
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842739"
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 远程重启设备


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**重新启动**设备操作将重启你选择的设备。 设备所有者不会获得重新启动的自动通知，而且他们的工作内容可能丢失。

## <a name="supported-platforms"></a>受支持的平台

- Windows - Windows 8.1 及更高版本支持
- Windows Phone - Windows Phone 8.1 及更高版本支持
- Android 展台设备 - Android 7.0 及更高版本支持
- iOS - 支持

    > [!Note]  
    > 此命令需要受监督的设备和“设备锁定”访问权限。 设备会立即重启。 密码锁定的 iOS 设备重启后不会重新加入 Wi-Fi 网络。 重启后，设备可能无法与服务器进行通信。
- macOS - 不支持
- Android 和 Android 工作配置文件设备 - 不支持

## <a name="restart-a-device"></a>重启设备

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备” > “所有设备”。
4. 在所管理的设备列表中，选择一个设备，选择“更多”，然后选择“重新启动”设备远程操作。

## <a name="next-steps"></a>后续步骤

- 若要查看“重新启动”设备操作的状态，请选择“设备” > “设备操作”。
