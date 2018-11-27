---
title: Intune 中的 Endpoint Protection 疑难解答 - Azure | Microsoft Docs
description: 解决使用 Microsoft Intune Endpoint Protection 时出现的问题。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: f828394c48b5b7d55d9180da875d9cb3062f23c6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181677"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Intune 中的 Endpoint Protection 疑难解答

此信息有助于解决使用 Endpoint Protection 时出现的问题。 此外，还可以[查看事件日志和错误代码以排除使用 Windows Defender AV 遇到的问题](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)。

如果此信息没有帮助，还可以[获取对 Microsoft Intune 的支持](get-support.md)。

### <a name="error-messages"></a>错误消息
本章节描述了以下错误和警告的潜在原因和解决方案。

|状态项|可能的原因|可能的解决方案|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 引擎不可用**|Intune Endpoint Protection 引擎已损坏或删除。|如果 Intune Endpoint Protection 引擎已损坏，可以尝试更新或重新安装软件。<br /><br />若要强制执行立即更新，请在 Endpoint Protection 客户端软件中选择**更新**（参见托管计算机上的工具栏）。<br /><br />如果无法更新引擎，则必须重新安装 Endpoint Protection 引擎。<br /><br />在托管计算机“控制面板”的已安装程序列表中，找出“Microsoft Intune Endpoint Protection 代理”，然后卸载应用程序。<br /><br />在下次更新同步期间，Microsoft Online Management 更新管理器将会检测缺少的程序，并在计划安装时间重新安装它。|
|**已禁用 Endpoint Protection**|Intune Endpoint Protection 已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用 Endpoint Protection。 请参阅 Intune 中的[添加 Endpoint Protection 设置](endpoint-protection-configure.md)或[打开 Windows Defender 以访问公司资源](/intune-user-help/turn-on-defender-windows)。|
|**已禁用实时保护**|实时保护已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用 Endpoint Protection。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**已禁用下载扫描**|下载扫描被管理员（通过使用配置文件）或被托管计算机上的某位用户禁用。|启用扫描。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**已禁用文件和程序活动监视**|文件和程序活动监视已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用文件和程序活动。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**已禁用行为监视**|行为监视已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用行为监视。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**已禁用脚本扫描**|脚本扫描已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用脚本扫描。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**已禁用网络检查系统**|网络检查系统已遭到管理员（通过使用配置文件）或托管计算机上的某位用户禁用。|启用网络检查系统 (NIS)。 请参阅 Intune 中的 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)或[打开实时保护以访问公司资源](/intune-user-help/turn-on-defender-windows)。 |
|**恶意软件定义过期**|计算机可能已与 Internet 断开了很长一段时间，其恶意软件定义可能尚未更新。 如果计算机上的恶意软件定义过期 14 天或更长时间，就会出现这种状态。|如果恶意软件定义过期，可使用 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)更新定义。|
|**完全扫描逾期**|已经有 14 天未进行完全扫描。 可能的原因是完全扫描时计算机进行了重新启动。|如果完全扫描逾期，可运行一次完全扫描或计划定期完全扫描。 请参阅 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)。 |
|**快速扫描逾期**|已经有 14 天未进行快速扫描。 这可能是快速扫描过程中重启所导致。|如果快速扫描逾期，可运行一次快速扫描或计划定期快速扫描。 请参阅 [Windows Defender 防病毒](device-restrictions-windows-10.md#windows-defender-antivirus)。|
|**正在运行的另一个端点防护应用程序**|另一个 Endpoint Protection 应用程序正在运行，并且计算机处于正常状态。|默认情况下，如果安装了另一个 Endpoint Protection 应用程序，且 Intune 检测到该应用程序，则设备会变得不稳定。|

### <a name="next-steps"></a>后续步骤
如果此信息没有帮助，还可以[获取对 Microsoft Intune 的支持](get-support.md)。
