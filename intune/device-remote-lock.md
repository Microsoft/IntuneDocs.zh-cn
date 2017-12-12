---
title: "使用 Intune 远程锁定受管理设备"
titlesuffix: Azure portal
description: "了解如何使用 Intune 远程锁定你管理的设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8905b97a5912010a2516788a8da66441fc6f89ae
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>使用 Intune 远程锁定受管理设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**远程锁定**设备将锁定所选的设备。 设备所有者必须使用其密码才能解锁设备。 只能远程锁定设置了 PIN 或密码的设备。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - Windows Phone 8.1 及更高版本支持
- iOS - 支持
- macOS - 支持

    > [!Note]  
    > 设置 6 位数的恢复 PIN。 锁定时，“设备概述”边栏选项卡会显示 PIN，直到发送另一个设备操作。
- Android - 支持

## <a name="how-to-remote-lock-a-device"></a>如何远程锁定设备

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从你管理的设备列表中，选择设备，然后选择“远程锁定”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
