---
title: 排查 Microsoft Intune 中的软件更新问题 - Azure | Microsoft Docs
description: 解决 Microsoft Intune 中的软件更新问题。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ad8d904f72df169eea136c625a2f44d645cafbc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509754"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>排查 Microsoft Intune 中的软件更新问题

帮助解决 Microsoft Intune 中的软件更新问题。 若要查看错误代码和说明列表，请转到 [Microsoft Intune 中的软件更新代理错误代码](../protect/software-update-agent-error-codes.md)。

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>有许多被取代更新的 Windows 7 设备停止向 Intune 报告

Microsoft Intune 客户端可能出现以下一种或多种表现的情况：

- 设备突然停止向 Intune 报告。  
- 设备出现高 CPU 使用率。
- 当应用程序通过 Intune 安装时，安装速度缓慢。
- Microsoft Intune Center 显示以下错误：`An error occurred while updating your computer. Error found: Code 0x800705b4`。
- “Intune 管理控制台”>“组”>“所有设备”>“状态”显示：`One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

如果被取代的更新（已被其他更新所取代的更新）已较长时间未遭到拒绝，则可能出现此问题。 在某些进程期间（例如安装应用程序），Windows 将按顺序检查所有被取代的更新，以便可正确映射更新及其后续任务。 如果被取代的更新的列表过大，此检查任务可能导致 CPU 使用率过高，因为需要处理负载和时间。 此问题主要影响 Windows 7 设备，因为大量被取代的更新对 Windows 7 可用。 较新的操作系统可能不具备如此多可用的被取代更新，并且可能不易发生此问题。

**解决方法**

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“软件更新”  。
3. 若被取代的更新可应用到 Windows 7 或在受影响的客户端上安装的应用程序（如 Microsoft Office），则拒绝所有此类更新。
4. 重启受影响的客户端。

如果你正在运行 Windows 7，请确保已安装以下更新：[3050265 Windows 更新客户端（用于 Windows 7）：2015 年 6 月](https://support.microsoft.com/kb/3050265)。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。