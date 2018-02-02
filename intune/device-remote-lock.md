---
title: "使用 Intune 远程锁定受管理设备"
titlesuffix: Azure portal
description: "了解如何使用 Intune 远程锁定你管理的设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecd7fa03b35e91b5a77906858fb251348796704d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>使用 Intune 远程锁定受管理设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**远程锁定**设备将锁定所选的设备。 设备所有者必须使用其密码才能解锁设备。 只能远程锁定设置了 PIN 或密码的设备。

## <a name="supported-platforms"></a>受支持的平台

以下平台支持远程锁定：

|平台|支持状态|
|---|---|
|Android|是|
|iOS|是|
|macOS|是|
|Windows 10|是|
|Windows 10 移动版|是|
|Windows Phone|是，适用于 Windows Phone 8.1 和更高版本|

> [!NOTE]  
> 对于 macOS 设备，请设置一个 6 位数的恢复 PIN。 锁定时，“设备概述”边栏选项卡会显示 PIN，直到发送另一个设备操作。

## <a name="how-to-remote-lock-a-device"></a>如何远程锁定设备

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从你管理的设备列表中，选择设备，然后选择“远程锁定”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
