---
title: "利用 Intune 来管理设备"
titleSuffix: Intune on Azure
description: "了解如何查看使用 Intune 管理的设备，并在设备上执行各种操作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>什么是 Microsoft Intune 设备管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**设备**工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。 若要访问工作负荷，请执行以下操作：

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 现可执行列出的远程设备操作。 可用的操作取决于设备平台和设备的配置：

## <a name="available-device-actions"></a>可用的设备操作

- [查看设备清单](device-inventory.md)
- 执行远程设备操作：
    - [删除公司数据](device-company-data-remove.md) 
    - [恢复出厂设置](device-factory-reset.md)
    - [远程锁定](device-remote-lock.md)
    - [重置密码](device-passcode-reset.md)
    - [绕过激活锁](device-activation-lock-bypass.md)
    - [重新开始](device-fresh-start.md)
    - [丢失模式](device-lost-mode.md)
    - [查找设备](device-locate.md)
    - [重新启动](device-restart.md)
    - [Windows 10 PIN 重置](device-windows-pin-reset.md)
    - [适用于 Android 的远程控制](device-profile-android-teamviewer.md)
    - [同步设备](device-sync.md)


## <a name="next-steps"></a>后续步骤

- 选择“设备操作”以查看对所管理设备执行的操作的状态。 
![监视设备操作](./media/monitor-device-actions.png)
