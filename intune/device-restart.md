---
title: "使用 Intune 远程重启设备"
titlesuffix: Azure portal
description: "了解如何使用重启设备操作远程重启设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9afe804d2f9e48e27ced4bd92959cd065f6ec89a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 远程重启设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重新启动**设备操作将重启你选择的设备。 设备所有者不会获得重新启动的自动通知，因此工作可能丢失。

## <a name="supported-platforms"></a>受支持的平台

- Windows - Windows 8.1 及更高版本支持
- Windows Phone - Windows Phone 8.1 及更高版本支持
- iOS - 支持

    > [!Note]  
    > 此命令需要受监督的设备和“设备锁定”访问权限。 设备会立即重启。 密码锁定的 iOS 设备重启后不会重新加入 Wi-Fi 网络；重启后，它们可能无法与服务器进行通信。
- macOS - 不支持
- Android - 不支持

## <a name="how-to-restart-a-device"></a>如何重启设备

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中，选择一台设备，然后选择“重新启动”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
