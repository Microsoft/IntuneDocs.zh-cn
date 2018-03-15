---
title: "使用 Intune 来重置和删除设备密码"
titlesuffix: Azure portal
description: "了解如何重置和删除使用 Intune 管理的设备密码。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e1496d24fd9d3bb636a4eab00c254b753210f63
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>重置和删除受 Intune 管理的设备密码


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

术语“删除”和“重置”在本文中可交换使用。

“删除密码”操作为设备生成一个新密码，新密码显示在<设备名称> “概述”边栏选项卡上。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - Windows Phone 8.1 到 Windows 10 创意者更新（未加入 Azure AD）、Windows 10 创意者更新及更高版本支持
- iOS - 支持
- macOS - 不支持
- Android - 早于 Android 7 的 Android 版本支持。 不支持 Android for Work。

## <a name="how-to-reset-a-passcode"></a>如何重置密码

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备”边栏选项卡上，选择“所有设备”。
5. 从所管理设备的列表中，选择一台设备，选择“...更多”，然后选择“删除密码”设备远程操作。

## <a name="next-steps"></a>后续步骤

要查看刚执行的操作的状态，请在“设备”边栏选项卡上选择“设备操作”。
