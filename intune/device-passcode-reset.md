---
title: "使用 Intune 重置设备密码"
titleSuffix: Intune on Azure
description: "了解如何重置使用 Intune 管理的设备密码。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30fac990d8b4a0a088180598e7787e23b1f708b7
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>重置受 Intune 管理的设备密码


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“重置密码”操作为设备生成一个新密码，新密码显示在“<设备名称> 概述”边栏选项卡上。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - Windows Phone 8.1 到 Windows 10 创意者更新（未加入 Azure AD）、Windows 10 创意者更新及更高版本支持
- iOS - 支持
- macOS - 不支持
- Android - 早于 Android 7 的 Android 版本支持。 不支持 Android for Work。

## <a name="how-to-reset-a-passcode"></a>如何重置密码

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中选择一台设备，然后选择“重置密码”设备远程操作。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。
