---
title: 使用 Microsoft Intune 锁定设备 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用“远程锁定”操作锁定受 PIN 或密码保护的设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bce5a89ecc49952f5c21536c429e9cd3309b13c3
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712268"
---
# <a name="remotely-lock-devices-with-intune"></a>使用 Intune 远程锁定设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

“远程锁定”设备操作将锁定该设备  。 设备所有者必须输入其密码才能解锁设备。 可远程锁定已设置 PIN 或密码的设备。 不能远程锁定没有 PIN 或密码的设备。

## <a name="supported-platforms"></a>受支持的平台

以下平台支持远程锁定  ：

- Android
- Android 企业展台设备
- Android 企业工作配置文件设备
- iOS
- macOS
- Windows 10 移动版
- Windows Phone 8.1 及更高版本

以下平台不支持远程锁定  ：
- Windows 10 桌面版

> [!NOTE]
> 对于 macOS 设备，请设置一个 6 位数的恢复 PIN。 设备锁定时，“设备概述”会显示 PIN，直到发送另一个设备操作  。

## <a name="remote-lock-a-device"></a>远程锁定设备

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“设备” > “所有设备”   。
4. 在设备列表中选择一个设备，然后选择“远程锁定”操作  。

## <a name="next-steps"></a>后续步骤

- 若要查看此操作的状态，请选择“Microsoft Intune” > “设备” > “设备操作”    。 
- 有关有助于管理设备的其他操作，请参阅[可用操作](device-management.md)。
