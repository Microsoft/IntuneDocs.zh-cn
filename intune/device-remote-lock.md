---
title: "使用 Microsoft Intune 锁定设备 - Azure | Microsoft Docs"
description: "在 Microsoft Intune 中使用“远程锁定”操作锁定受 PIN 或密码保护的设备。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>使用 Intune 远程锁定设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“远程锁定”设备将锁定该设备。 设备所有者必须输入其密码才能解锁设备。 可远程锁定已设置 PIN 或密码的设备。 不能远程锁定没有 PIN 或密码的设备。

## <a name="supported-platforms"></a>受支持的平台

以下平台支持远程锁定：

- Android
- iOS
- macOS
- Windows 10 移动版
- Windows Phone 8.1 及更高版本

以下设备不支持：
- Windows 10 桌面版

> [!NOTE]
> 对于 macOS 设备，请设置一个 6 位数的恢复 PIN。 锁定时，“设备概述”会显示 PIN，直到发送另一个设备操作。

## <a name="remote-lock-a-device"></a>远程锁定设备

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备”和“所有设备”。
4. 从设备列表中选择一个设备，然后选择“远程锁定”操作。

## <a name="next-steps"></a>后续步骤

若要查看此操作的状态，请打开“设备操作”（“Microsoft Intune”>“设备”）。 有关帮助管理设备的其他操作，请参阅[可用操作](device-management.md)。