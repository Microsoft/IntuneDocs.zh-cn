---
title: Exchange Connector 疑难解答
titleSuffix: Microsoft Intune
description: 解决与 Intune On-premises Exchange Connector 相关的问题。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3d9473b68f0420670130203409abf477355d93f
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885533"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Intune Exchange Connector 疑难解答

本文介绍如何解决与 Intune Exchange Connector 相关的问题。

## <a name="before-you-start"></a>开始之前

在开始对 Intune 中的 Exchange Connector 问题进行故障排除之前，请收集一些基本信息，以确保使用坚实的基础。 此方法可帮助您更好地了解问题的性质，并更快地解决问题。

- 验证你的进程是否满足安装要求。 请参阅[设置本地 Intune Exchange 连接器](exchange-connector-install.md)。
- 验证你的帐户具有 Exchange 和 Intune 管理员权限。
- 请注意完整的错误消息文本、详细信息和显示消息的位置。
- 确定问题的开始时间： 
  - 首次设置连接器？ 
  - 连接器是否正常工作，并失败？
  - 如果正在运行，Intune 环境、Exchange 环境或运行连接器软件的计算机上发生了哪些更改？
- 什么是 MDM 机构？
- 使用哪种版本的 Exchange？

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>使用 PowerShell 获取有关 Exchange Connector 问题的更多数据

- 若要获取邮箱的所有移动设备的列表，请使用 `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- 若要获取邮箱的 SMTP 地址列表，请使用 `Get-Mailbox -Identity user | select emailaddresses | fl`
- 若要获取有关设备的访问状态的详细信息，请使用 `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>查看连接器配置

查看[本地 Exchange connector 要求](exchange-connector-install.md#intune-exchange-connector-requirements)，确保正确配置环境和连接器。 

### <a name="general-considerations-for-the-connector"></a>连接器的一般注意事项

- 确保你的防火墙和代理服务器允许在承载 Intune Exchange Connector 和 Intune 服务的服务器之间进行通信。

- 承载 Intune Exchange Connector 和 Exchange 客户端访问服务器（CAS）的计算机应已加入域且位于同一 LAN 上。 请确保为 Intune Exchange connector 使用的帐户添加所需的权限。

- 通知帐户用于检索*自动发现*设置。 有关 Exchange 中的 Autodisover 的详细信息，请参阅[Exchange Server 中的自动发现服务](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016)。

- Intune Exchange Connector 使用通知帐户凭据将通知电子邮件发送给 EWS URL，并使用 "*入门*" 链接（用于注册 Intune）发送通知电子邮件。 对于 Android 非 Knox 设备，使用 "*开始*使用注册链接" 是必需的。 否则，条件访问将阻止这些设备。

### <a name="common-issues-for-connector-configurations"></a>连接器配置的常见问题

- **帐户权限**：在“Microsoft Intune Exchange Connector”对话框中，请确保已指定具有执行[必需 Windows PowerShell Exchange cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements) 的相应权限的用户帐户。
- **通知电子邮件**：启用通知并指定通知帐户。
- **客户端访问服务器同步**：配置 Exchange connector 时，请指定具有最小网络延迟的 ca，以使其成为托管 Exchange Connector 的服务器。 CAS 和 Exchange Connector 间的通信延迟可能导致设备发现延迟，尤其是在使用 Exchange Online Dedicated 时。
- **同步计划**：使用新注册设备的用户可能会在获取访问权限时遇到延迟，直到 Exchange Connector 与 Exchange CAS 同步。 完全同步一天进行一次，而增量（快速）同步每天进行多次。 可以[手动强制执行快速同步或完全同步](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)以尽量减少延迟。

## <a name="next-steps"></a>后续步骤
以下文章可帮助解决常见问题和特定错误：

- [解决 Intune Exchange Connector 的常见问题](troubleshoot-exchange-connector-common-problems.md)。
- [解决 Intune Exchange Connector 的常见错误](troubleshoot-exchange-connector-common-errors.md)。

寻求支持或 Intune 社区的帮助：

- 请参阅[获取支持](../fundamentals/get-support.md)以使用 Intune 控制台帮助解决问题，或与 Microsoft 建立支持案例。 
- 在[Microsoft Intune 论坛](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)中发布你的问题。  
