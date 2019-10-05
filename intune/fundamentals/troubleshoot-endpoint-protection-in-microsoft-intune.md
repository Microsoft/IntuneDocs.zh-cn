---
title: Microsoft Intune 中的常见 Endpoint Protection 信息 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用 Endpoint Protection 和 Windows Defender 以及对其进行故障排除时，请参阅常见消息和可能的解决方案。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2b4e57ba348fcc6e6907159e395e50dbdf35d1f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735579"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Microsoft Intune 中的 Endpoint Protection 问题和可能的解决方案

本文列出并描述了一些错误和警告的潜在原因和解决方案。 此信息有助于解决使用 Endpoint Protection 时出现的问题。

## <a name="windows-defender-error-codes"></a>Windows Defender 错误代码

查看事件日志和错误代码以[排除使用 Windows Defender AV 遇到的问题](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)。

## <a name="common-intune-errors-and-possible-resolutions"></a>Intune 的常见错误和可能的解决方法

### <a name="endpoint-protection-engine-unavailable"></a>Endpoint Protection 引擎不可用

**可能的原因**：Intune Endpoint Protection 引擎已损坏或删除。

**可能的解决方案**：

- 如果 Endpoint Protection 损坏或无法更新，则更新或重新安装程序。
- 强制执行即时更新。 在 Endpoint Protection 客户端程序（可能在任务栏中）中，选择“更新”  。
- 在“控制面板”>“程序”中，选择“Microsoft Intune Endpoint Protection 代理”  。 卸载应用程序。
- 在下次更新同步期间，Microsoft Online Management 更新管理器将会检测缺少的程序，并在计划安装时间重新安装它。

### <a name="features-are-disabled"></a>禁用功能

可能会收到一些功能被禁用的消息。 如果管理员使用配置文件禁用了 Intune Endpoint Protection 或 Windows Defender，则可能出现这些消息。 或者，最终用户在设备上禁用了它。 可能的消息：

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**可能的解决方案**：启用这些功能。 如需指导，请参阅：

- [添加 Endpoint Protection 设置](../protect/endpoint-protection-configure.md)
- [Windows Defender 防病毒](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [最终用户：打开访问公司资源的实时保护](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>恶意软件定义过期

如果设备上的恶意软件定义过期 14 天或更长时间，就会显示这种状态。 例如，该消息可能显示设备是否与 Internet 断开连接，或者恶意软件定义是否过时。

**可能的解决方案**：如果恶意软件定义过期，可使用 [Windows Defender 防病毒](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)更新定义。

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>完全扫描逾期或快速扫描逾期

14 天内尚未完成完全扫描或快速扫描。 如果设备在完全扫描期间重新启动，就会发生这种情况。

**可能的原因**：如果扫描逾期，可运行一次扫描或计划定期扫描。 请参阅 [Windows Defender 防病毒](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。

### <a name="another-endpoint-protection-application-running"></a>正在运行的另一个端点防护应用程序

另一个 Endpoint Protection 应用程序正在运行，并且设备处于正常状态。

**可能的解决方案**：如果安装了另一个 Endpoint Protection 应用程序，且 Intune 检测到该应用程序，则设备会变得不稳定。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
