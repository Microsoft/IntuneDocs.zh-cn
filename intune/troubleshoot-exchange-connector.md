---
title: Exchange Connector 疑难解答
titleSuffix: Microsoft Intune
description: 解决与 Intune On-premises Exchange Connector 相关的问题。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea3ae66a32353b4aa6c782b13e6a587ee1f4464e
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68491818"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Intune On-Premises Exchange Connector 疑难解答

本文介绍如何解决与 Intune On-premises Exchange Connector 相关的问题。

## <a name="steps-for-checking-the-connector-configuration"></a>检查 Connector 配置的步骤 

选中 [Intune On-premises Exchange Connector 设置](exchange-connector-install.md)，确保已正确配置 Connector。 以下是一些常见问题。 执行任何更正后，请查看问题是否已解决。

- 在“Microsoft Intune Exchange Connector”对话框中，请确保已指定具有执行[必需 Windows PowerShell Exchange cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements) 的相应权限的用户帐户。
- 启用通知并指定通知帐户。
- 配置 Exchange Connector 时，指定尽可能接近托管 Exchange Connector 的服务器的客户端访问服务器 (CAS)。 CAS 和 Exchange Connector 间的通信延迟可能导致设备发现延迟，尤其是在使用 Exchange Online Dedicated 时。
- 使用新注册设备的用户可能会在获取访问权限时遇到延迟，直到 Exchange Connector 与 Exchange CAS 同步。 完全同步一天进行一次，而增量（快速）同步每天进行多次。  可以[手动强制执行快速同步或完全同步](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)以尽量减少延迟。
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange 中未发现的 Exchange ActiveSync 设备
[监视 Exchange Connector 活动](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)，以检查 Exchange Connector 是否正在与 Exchange 服务器同步。 如果已在设备加入后成功完成完全同步或快速同步，则可检查是否存在其他可能的问题，如下所示。 如果未进行任何同步，请收集同步日志并将其附加到支持请求。

- 确保用户具备 Intune 许可证，否则 Exchange Connector 无法发现其设备。
- 如果用户的主 SMTP 地址与其在 Azure Active Directory (Azure AD) 中的 UPN 不同，Exchange Connector 无法发现该用户的任何设备。 修复主 SMTP 地址以解决此问题。
- 如果环境中同时存在 Exchange 2010 和 Exchange 2013 邮箱服务器，建议将 Exchange Connector 指向 Exchange 2013 CAS。 反之，如果将 Exchange Connector 设置为与 Exchange 2010 CAS 进行通信，Exchange Connector 将无法发现任何 Exchange 2013 用户的设备。 
- 对于 Exchange Online Dedicated 环境，必须在初始化设置期间在专用环境中将 Exchange Connector 指向 Exchange 2013 CAS（而非 Exchange 2010 CAS），因为 Connector 在执行 Powershell cmdlet 时只与此 CAS 进行通信。


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>使用 Powershell 获取有关 Exchange Connector 问题的详细数据
- 若要获取邮箱的所有移动设备的列表, 请使用`Get-ActiveSyncDeviceStatistics -mailbox mbx`
- 若要获取邮箱的 SMTP 地址列表, 请使用`Get-Mailbox -Identity user | select emailaddresses | fl`
- 若要获取有关设备的访问状态的详细信息，请使用 `Get-CASMailbox <upn> | fl`

## <a name="next-steps"></a>后续步骤
如果此信息没有帮助，还可以[获取对 Microsoft Intune 的支持](get-support.md)。
