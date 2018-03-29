---
title: 使用 Microsoft Intune 重置设备密码 - Azure | Microsoft Docs
description: 在使用 Intune 进行管理或监视的设备上，使用“删除密码”操作删除或重置密码。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>在 Intune 中重置或删除设备密码

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

若要为设备创建新的密码，请使用“删除密码”操作。

## <a name="supported-platforms"></a>受支持的平台

- Windows Phone 8.1（未加入到 Azure Active Directory），其中包括 Windows 10 创意者更新以下的版本
- Windows 10 创意者更新及更高版本
- iOS
- 早于 Android 7 的 Android 版本

以下系统不支持此功能：

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>重置密码

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备”和“所有设备”。
4. 从你管理的设备列表中，选择一个设备，然后选择“...更多”。 然后选择“删除密码”设备远程操作。

## <a name="next-steps"></a>后续步骤

要查看刚执行的操作的状态，请在“设备”中选择“设备操作”。
