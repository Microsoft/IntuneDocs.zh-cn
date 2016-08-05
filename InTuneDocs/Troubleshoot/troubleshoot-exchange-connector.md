---
title: "Exchange Connector 疑难解答| Microsoft Intune"
description: "解决与 Intune Exchange connector 相关的问题。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: 04ac69a30f6c1d91fe755f9720fbc2adc51745f7


---

# Exchange Connector 疑难解答
本主题介绍如何解决可能与 Intune Exchange Connector 相关的问题。

## 检查 Connector 配置的步骤 

检查 Exchange Connector 的配置，然后查看问题是否已得到解决。

- 请务必在 Exchange Connector 的初始设置中指定通知帐户。
- Exchange Connector 服务帐户必须具有适当的权限才能执行 Exchange Connector 使用的 PowerShell cmdlet。
- 配置 Exchange Connector 时，指定尽可能接近托管 Exchange Connector 的服务器的客户端访问服务器 (CAS)。 CAS 和 Exchange Connector 间的通信延迟可能导致设备发现延迟，尤其是在使用 O365 专用时。
- 请注意，与 Exchange CAS 的 Exchange Connector 同步间存在时间滞后。 完全同步一天进行一次，而增量（快速）同步每两个小时进行一次。 持有新注册的设备的用户可能遇到访问延迟。
- 
## Exchange 中未发现的 Exchange ActiveSync 设备
请查看 Exchange Connector 是否正在与 Exchange 服务器同步。 若要进行此操作，请查找完全同步或增量同步的日志。 查看 Exchange Connector 日志。 如果自设备连接后完全同步或增量同步已成功完成，则你已将其作为问题的根源消除。 如果未进行任何同步，则收集相关的同步日志并将其添加到你的支持请求中。

- 如果用户不具备 Intune 许可证，则 Exchange connector 将无法发现其设备。
- 如果用户的主 SMTP 地址与其在 AAD 中的 UPN 不同，则 Exchange Connector 将无法发现该 Intune/AAD 用户的任何设备。 修复主 SMTP 地址。
- 如果 Exchange Connector 在发现周期期间进行通信的 CAS 是 Exchange 2010 CAS，而你同时拥有 Exchange 2010 和 2013 邮箱服务器，则 Exchange Connector 将无法发现任何 Exchange 2013 用户的设备。 若要解决此问题，请配置 Exchange Connector 指向 Exchange 2013 CAS。  尽管此问题主要涉及 O365 专用拓扑，我们仍建议将在其他拓扑中指向 Exchange 2013 CAS 作为最佳做法。
- 对于 Exchange 专用（O365 专用）环境，必须在初始化设置期间的专用环境中将 Exchange Connector 指向 Exchange 2013（而非 2010）CAS，因为其在执行 Powershell cmdlet 时将只与此 CAS 进行通信。


## 使用 Powershell 获取有关 Exchange Connector 问题的详细数据
- 若要获取某个邮箱的所有移动设备的列表，请使用 Get-ActiveSyncDeviceStatistics -mailbox mbx
- 若要获取某个邮箱的 SMTP 地址的列表，请使用 Get-Mailbox -Identity user | select emailaddresses | fl。
- 若要获取有关设备的访问状态的详细信息，请使用 Get-CASMailbox <upn> | fl

### 后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。



<!--HONumber=Aug16_HO1-->


