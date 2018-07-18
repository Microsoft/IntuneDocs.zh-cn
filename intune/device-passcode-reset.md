---
title: 使用 Microsoft Intune 重置设备密码 - Azure | Microsoft Docs
description: 在使用 Intune 进行管理或监视的设备上，使用“删除密码”操作删除或重置密码。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a233c62b76901d9bad00aa6d8b2a8a4dd45dea96
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039295"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>在 Intune 中重置或删除设备密码

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

若要为设备创建新的密码，请使用“删除密码”操作。 此操作提示仅为工作配置文件重置 PIN。 Android 工作配置文件不支持设备 PIN 重置。

## <a name="work-profile-pin-reset-supported-platforms"></a>支持工作配置文件 PIN 重置的平台

- 使用工作配置文件注册的版本 8.0 及以上版本的 Android 设备 
- 版本在 6.0 及以下的 Android 设备
- Android 企业展台设备
- iOS 
     
## <a name="unsupported-platforms"></a>不受支持的平台

- 使用 Work 配置文件注册且版本在 7.0 及以下的 Android 设备
- 版本在 7.0 及以上的 Android 设备
- macOS
- Windows

## <a name="reset-a-passcode"></a>重置密码

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备”和“所有设备”。
4. 从你管理的设备列表中，选择一个设备，然后选择“...更多”。 然后选择“删除密码”设备远程操作。

## <a name="resetting-android-work-profile-passcodes"></a>重置 Android 工作配置文件密码

受支持的 Android 工作配置文件设备为最终用户接收新的托管配置文件解锁密码或托管配置文件质询。 

对于 Android 8.0 工作配置文件设备，最终用户会在注册完成后立即收到激活其重置密码的通知。 需提供和设置 Work 配置文件密码时会显示该通知。 输入其密码后，该通知将消除。

## <a name="resetting-ios-passcodes"></a>重置 iOS 密码

系统会从 iOS 设备中删除密码。 如果设置了密码符合性策略，则设备会提示用户在“设置”中设置新密码。 

## <a name="next-steps"></a>后续步骤

要查看刚执行的操作的状态，请在“设备”中选择“设备操作”。
