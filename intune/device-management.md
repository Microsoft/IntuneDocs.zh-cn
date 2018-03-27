---
title: 使用 Microsoft Intune 管理设备
titleSuffix: ''
description: 查看使用 Intune 管理的设备，并在设备上执行各种操作。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436eeb306bf4ba343ae4d88a824aeed2077a3426
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>什么是 Microsoft Intune 设备管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 IT 管理员，必须确保受管理设备提供最终用户工作时所需的资源，同时保护数据免遭风险。

**设备**工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。 若要访问工作负荷，请执行以下操作：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”中选择“设备”。
4. 可查看设备相关信息并执行远程设备操作，如下所示：
    - 概述 - 可以管理的已注册设备的快照。
    - 所有设备 - 所管理的已注册设备的列表。 选择“筛选器”或“列”，优化显示的信息。 选择一个设备，[查看设备清单](device-inventory.md)。
    - Azure AD 设备 - 注册或加入 Azure Active Directory 的设备列表。 了解有关 [Azure AD 设备管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)的详细信息。
    - 设备操作 - 在设备上执行的远程操作的历史记录，包括操作、操作状态、操作启动者和时间。

        ![监视设备操作的屏幕截图](./media/monitor-device-actions.png)

    - **审核日志** - 审核日志记录了导致 Microsoft Intune 发生更改的活动。 了解更多有关[审核日志](monitor-audit-logs.md)的信息。
    - **TeamViewer 连接器** - TeamViewer 服务允许由 Intune 托管的 Android 设备用户从 IT 管理员处获取远程协助。 详细了解 [TeamViewer](device-profile-android-teamviewer.md)。
    - **帮助和支持** - 排查问题、请求获取支持或查看 Intune 状态。  
    
## <a name="available-device-actions"></a>可用的设备操作
可用的操作取决于设备平台和设备的配置。

- [查看设备清单](device-inventory.md)
- 执行远程设备操作：
    - [删除公司数据](devices-wipe.md#remove-company-data)
    - [恢复出厂设置](devices-wipe.md#factory-reset)
    - [远程锁定](device-remote-lock.md)
    - [重置密码](device-passcode-reset.md)
    - [绕过激活锁](device-activation-lock-bypass.md)（仅限 iOS）
    - [重新开始](device-fresh-start.md)（仅限 Windows）
    - [丢失模式](device-lost-mode.md)（仅限 iOS）
    - [查找设备](device-locate.md)（仅限 iOS）
    - [重启](device-restart.md)（仅限 Windows）
    - [Windows 10 PIN 重置](device-windows-pin-reset.md)
    - [适用于 Android 的远程控制](device-profile-android-teamviewer.md)
    - [同步设备](device-sync.md)


## <a name="next-steps"></a>后续步骤

- 选择“设备操作”以查看对所管理设备执行的操作的状态。
