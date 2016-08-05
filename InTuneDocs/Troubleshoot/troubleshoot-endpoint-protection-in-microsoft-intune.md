---
title: "Endpoint Protection 疑难解答 | Microsoft Intune"
description: "解决使用 Microsoft Intune Endpoint Protection 时出现的问题。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: 71f976fba252950fd9a8818fb27fbbb294369894


---

# Troubleshoot Endpoint Protection in Microsoft Intune

此章节的信息有助于解决使用 Microsoft Intune Endpoint Protection 时出现的问题。

如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。


### Endpoint Protection 错误消息
本章节描述了在 [Intune 管理员控制台](https://manage.microsoft.com)的**Endpoint Protection 状态**窗格中显示的以下错误和警告的潜在原因和解决方案。

|状态项|可能的原因|可能的解决方案|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 引擎不可用**|Intune Endpoint Protection 引擎已损坏或删除。|如果 Intune Endpoint Protection 引擎已损坏，可以尝试更新或重新安装软件。<br /><br />若要强制执行立即更新，请在 Endpoint Protection 客户端软件中选择**更新**（参见托管计算机上的工具栏）。<br /><br />如果无法更新引擎，则必须重新安装 Endpoint Protection 引擎。<br /><br />在托管计算机“控制面板”的已安装程序列表中，找出“Microsoft Intune Endpoint Protection 代理”，然后卸载应用程序。<br /><br />在下次更新同步期间，Microsoft Online Management 更新管理器将会检测缺少的程序，并在计划安装时间重新安装它。|
|**已禁用 Endpoint Protection**|Intune Endpoint Protection 已遭到管理员（通过使用策略）或托管计算机上的某位用户禁用。|如果禁用了 Endpoint Protection，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或从托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用 Endpoint Protection，请打开**策略**工作区，然后在应用于此计算机的策略中更改**启用 Endpoint Protection**设置。<br /><br />或者，<br /><br />若要从托管计算机中启用 Endpoint Protection，请从通知区域中启动 Intune Endpoint Protection 客户端，且系统将提示你启用 Endpoint Protection。|
|**已禁用实时保护**|实时保护已遭到管理员（通过使用策略）或托管计算机上的某位用户禁用。|如果禁用了实时保护，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或从托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用实时保护，请打开“策略”工作区，然后在应用于此计算机的策略中将“启用实时保护”设置更改为“是”。<br /><br />或者，<br /><br />若要从托管计算机中启用实时保护，请从通知区域中启动 Endpoint Protection 客户端软件。 此时，将会提示你启用实时保护。|
|**已禁用下载扫描**|下载扫描被管理员使用策略禁用，或被管理的计算机上的用户禁用。|如果禁用了下载扫描，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或从托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用下载扫描，请打开**策略**工作区，然后在应用于此计算机的策略中将**扫描所有下载**设置更改为**是**。<br /><br />或者，<br /><br />若要从托管计算机中启用下载扫描，请从通知区域中启动 Endpoint Protection 客户端软件。 依次选择**设置**选项卡、**实时保护**和**扫描所有下载**复选框，然后选择**保存更改**。|
|**已禁用文件和程序活动监视**|文件和程序活动监视已被使用策略的管理员或用户在被管理的计算机上禁用。|如果禁用了文件和程序活动监视，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用文件和程序活动监视，请打开“策略”工作区，然后在应用于此计算机的策略中将“监视计算机上的文件和程序活动”设置更改为“是”。<br /><br />或者，<br /><br />若要从托管计算机中启用文件和程序活动监视，请从通知区域中启动 Endpoint Protection 客户端软件。 依次选择**设置**选项卡、**实时保护**和**监视计算机上的文件和程序活动**复选框，然后选择**保存更改**。|
|**已禁用行为监视**|行为监视已遭到管理员（通过使用策略）或托管计算机上的某位用户禁用。|如果禁用了行为监视，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用行为监视，请打开**策略**工作区，在应用于此计算机的策略中将**启用行为监视**设置更改为**是**，然后重启托管计算机。<br /><br />或者，<br /><br />若要从托管计算机中启用行为监视，请从通知区域中启动 Endpoint Protection 客户端软件。 依次选择**设置**选项卡、**实时保护**和**启用行为监视**复选框，然后选择**保存更改**。 然后重启计算机。|
|**已禁用脚本扫描**|脚本扫描已遭到管理员（通过使用策略）或托管计算机上的某位用户禁用。|如果禁用了脚本扫描，则可以从 [Intune 管理员控制台](https://manage.microsoft.com)或从托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用脚本扫描，请打开**策略**工作区，然后在应用于此计算机的策略中将**启用脚本扫描**设置更改为**是**。<br /><br />或者，<br /><br />若要从托管计算机中启用脚本扫描，请从通知区域中启动 Endpoint Protection 客户端软件。 依次选择**设置**选项卡、**实时保护**和**启用脚本扫描**复选框，然后选择**保存更改**。|
|**已禁用网络检查系统**|网络检查系统被管理员使用策略禁用，或被管理的计算机上的用户禁用。|如果禁用了网络检查系统，则可以从 [Intune 管理员控制台](https://manage.microsoft.com) 或从托管计算机中启用它。 执行以下操作之一：<br /><br />若要从 [Intune 管理员控制台](https://manage.microsoft.com)中启用网络检查系统，请打开**策略**工作区，在应用于此计算机的策略中将**启用网络检查系统**设置更改为**是**，然后重启托管计算机。<br /><br />或者，<br /><br />若要从托管计算机中启用网络检查系统，请从通知区域中启动 Endpoint Protection 客户端软件。 依次选择**设置**选项卡、**实时保护**和**启用网络检查系统**复选框，然后选择**保存更改**。 重新启动计算机。|
|**恶意软件定义过期**|计算机可能已与 Internet 断开了很长一段时间，其恶意软件定义可能尚未更新。 如果计算机上的恶意软件定义过期 14 天或更长时间，就会出现这种状态。|如果恶意软件定义过期，则可以从[Intune 管理员控制台](https://manage.microsoft.com)或从托管计算机中更新定义。<br /><br />有关详细信息，请参阅[使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)主题。|
|**完全扫描逾期**|已经有 14 天未进行完全扫描。 可能的原因是完全扫描时计算机进行了重新启动。|如果完全扫描过期，你可以从 [Intune 管理员控制台](https://manage.microsoft.com)运行一次完全扫描或定期重复进行完全扫描，方法是使用主题[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)中的信息。|
|**快速扫描逾期**|已经有 14 天未进行快速扫描。 这可能是快速扫描过程中重启所导致。|如果快速扫描过期，你可以从 [Intune 管理员控制台](https://manage.microsoft.com)运行一次快速扫描或定期重复进行快速扫描，方法是使用主题[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)中的信息。|
|**正在运行的另一个端点防护应用程序**|另一个 Endpoint Protection 应用程序正在运行，并且计算机处于正常状态。|默认情况下，如果安装了其他 Endpoint Protection 应用程序并且 Intune 检测到该应用程序，则 Endpoint Protection 会自动禁用其自身。 如果 Intune 未检测到其他终结点应用程序，则 Endpoint Protection 将保持启用状态。 有关详细信息，请参阅[使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。|

### 后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。



<!--HONumber=Aug16_HO1-->


