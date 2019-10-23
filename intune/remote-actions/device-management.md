---
title: 使用 Microsoft Intune 管理设备 - Azure | Microsoft Docs
description: 通过 Microsoft Intune 查看管理的设备（包括将设备列表导出为 csv 格式）、查看已加入 Azure Active Directory 的设备、查看对设备进行的操作的更改日志、使用 TeamViewer 连接器允许 IT 管理员远程对 Android 进行故障排除，以及查看可以在设备上运行的所有操作。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/19/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3ee6240d9efb0d09c41a6a9b1260cd4189927a8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509427"
---
# <a name="what-is-microsoft-intune-device-management"></a>什么是 Microsoft Intune 设备管理？

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

作为 IT 管理员，必须确保受管理设备提供用户工作时所需的资源，同时保护数据免遭风险。

**设备**工作负荷可以让你了解所管理的设备，并能在这些设备上执行远程任务。

## <a name="get-to-your-devices"></a>找到你的设备

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择“设备”  。 此视图显示有关各设备的详细信息，以及可以使用该设备进行的操作，包括：

   - “概述”显示已注册设备的可视化快照，并显示正在使用不同平台（Android、iOS 等）的设备数量  。
   - “所有设备”显示你管理的已注册设备的列表  。

     使用“导出”功能，以 10,000 (Internet Explorer) 或 30,000（Microsoft Edge、Chrome）为增量创建一个包含所有设备的 .csv 列表  。

     选择任意设备以[查看有关该设备的详细信息](device-inventory.md)，包括硬件详细信息、已安装应用以及其符合性策略的状态等。

   - “Azure AD 设备”显示注册或加入 Azure Active Directory (Azure AD) 的设备列表  。 了解有关 [Azure AD 设备管理](https://docs.microsoft.com/azure/active-directory/device-management-introduction)的详细信息。
   - “设备操作”含有在不同设备上执行的远程操作的历史记录，包括操作、操作状态、操作启动者和时间  。

     ![监视设备操作的屏幕截图](./media/device-management/monitor-device-actions.png)

   - “审核日志”记录了导致 Intune 出现变化的活动  。 [审核日志](../fundamentals/monitor-audit-logs.md)可以提供更多信息。
   - “TeamViewer 连接器”服务允许由 Intune 托管的 Android 设备用户从 IT 管理员处获取远程协助  。 详细了解 [TeamViewer](teamviewer-support.md)。
   - “帮助和支持”提供有关疑难解答提示、请求支持或检查 Intune 状态的快捷方式  。

## <a name="available-device-actions"></a>可用的设备操作
可用的操作取决于设备平台和设备的配置。

- [查看设备清单](device-inventory.md)
- 运行远程设备操作：
  - [停用](devices-wipe.md#retire)
  - [擦除](devices-wipe.md#wipe)
  - [远程锁定](device-remote-lock.md)
  - [重置密码](device-passcode-reset.md)
  - [绕过激活锁](device-activation-lock-bypass.md)（仅限 iOS）
  - [重新开始](device-fresh-start.md)（仅限 Windows）
  - [丢失模式](device-lost-mode.md)（仅限 iOS）
  - [查找设备](device-locate.md)（仅限 iOS）
  - [重启](device-restart.md)（仅限 Windows）
  - [Windows 10 PIN 重置](device-windows-pin-reset.md)
  - [适用于 Android 的远程控制](teamviewer-support.md)
  - [同步设备](device-sync.md)
  - [发送自定义通知](custom-notifications.md#send-a-custom-notification-to-a-single-device)（Android、iOS）

## <a name="next-steps"></a>后续步骤

- 在“所有设备”中选择某个设备，以查看有关该设备的详细信息  。
- 选择“设备操作”以查看对所管理设备执行的操作的状态  。
