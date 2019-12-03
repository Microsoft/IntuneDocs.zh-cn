---
title: 排查 Intune Exchange connector 的常见问题
titleSuffix: Microsoft Intune
description: 排查和解决本地 Microsoft Intune Exchange connector 的常见问题。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547675"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>解决 Intune Exchange connector 的常见问题
 
本文可以帮助 Intune 管理员解决 Intune Exchange connector 操作的常见问题。

开始故障排除之前，请查看有关连接器的基本信息，请参阅[Intune 本地 Exchange connector 的故障排除](troubleshoot-exchange-connector.md)。 另请查看连接器配置的常见问题。

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>在 Exchange 中未发现 Exchange ActiveSync 设备

当 exchange ActiveSync 设备不是从 Exchange 中发现时，请[监视 exchange connector 活动](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support)，查看 exchange connector 是否正在与 exchange server 同步。 如果自设备加入后未发生同步，则收集同步日志并将它们附加到支持请求。 如果自设备加入后，完全同步或快速同步已成功完成，请检查是否存在以下问题：

- 请确保用户具有 Intune 许可证。 如果不是，Exchange connector 将无法发现其设备。

- 如果用户的主 SMTP 地址与其在 Azure Active Directory (Azure AD) 中的用户主体名称 (UPN) 不同，则 Exchange Connector 无法发现该用户的任何设备。 修复主 SMTP 地址以解决此问题。

- 如果环境中同时存在 Exchange 2010 和 Exchange 2013 邮箱服务器，建议将 Exchange Connector 指向 Exchange 2013 客户端访问服务器 (CAS)。 如果将 Exchange Connector 设置为与 Exchange 2010 CAS 进行通信，Exchange Connector 将无法发现 Exchange 2013 上的任何用户设备。

- 对于 Exchange Online 专用环境，必须在初始设置过程中将 Exchange connector 指向专用环境中的 Exchange 2013 CA （而不是 Exchange 2010 CA）。 连接器在执行 PowerShell cmdlet 时将仅与 Exchange 2013 CA 通信。

## <a name="problems-with-the-notification-email-message"></a>通知电子邮件的问题

若要在不运行 Android Knox 的设备上支持本地邮箱的条件性访问，请确保 Intune 注册从 Intune Exchange connector 发送的 "立即开始" 电子邮件消息开始。 从消息中开始注册可确保设备接收到跨所有平台（Exchange、Azure AD、Intune）的唯一 ActiveSyncID。

用户可能不会收到通知电子邮件，原因如下：

- 未正确设置通知帐户。
- 自动发现通知帐户失败。
- 用于发送电子邮件的 Exchange Web 服务（EWS）请求失败。

请查看以下各节以解决电子邮件通知问题。

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>检查用于检索自动发现设置的通知帐户

1. 确保在 Exchange 客户端访问服务上配置自动发现服务和 EWS。 有关详细信息，请参阅 Exchange Server 中的[客户端访问服务](https://docs.microsoft.com/Exchange/architecture/client-access/client-access)和[自动发现服务](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019)。

2. 验证你的通知帐户是否满足以下要求：

   - 此帐户具有由 Exchange 内部部署服务器托管的活动邮箱。

   - 帐户 UPN 匹配 SMTP 地址。

3. 自动发现需要具有指向 Exchange 客户端访问服务器的**Autodiscover.SMTPdomain.com** （例如 Autodiscover.contoso.com）的 dns 记录的 dns 服务器。 若要检查记录，请指定 FQDN 代替*Autodiscover.SMTPdomain.com* ，并执行以下步骤：

   1. 在命令提示符下，输入*NSLOOKUP*。

   2. 输入*Autodiscover.SMTPdomain.com*。 输出应如下图所示：![Nslookup 结果](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   你还可以在 https://testconnectivity.microsoft.com 从 internet 测试自动发现服务。 或使用 Microsoft Connectivity Analyzer 工具从本地域中测试。 有关详细信息，请参阅[Microsoft 连接分析器工具](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80))。


### <a name="check-autodiscovery"></a>检查自动发现

如果自动发现失败，请尝试以下步骤：

1. [配置有效的自动发现 DNS 记录](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150))。

2. 在 Intune Exchange connector 配置文件中对 EWS URL 进行硬编码：

   1. 确定 EWS URL。 Exchange 的默认 EWS URL 是 `https://<mailServerFQDN>/ews/exchange.asmx`的，但 URL 可能不同。 请与 Exchange 管理员联系，以验证您的环境的正确 URL。

   2. 编辑 *OnPremisesExchangeConnectorServiceConfiguration.xml* 文件。 默认情况下，该文件位于运行 Exchange Connector 的计算机上的 *%ProgramData%\Microsoft\Windows Intune Exchange Connector*中。 在文本编辑器中打开文件，然后更改以下行，以反映环境的 EWS URL： `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. 保存文件，然后重启计算机或 Microsoft Intune Exchange Connector 服务。

>[!NOTE]
> 在此配置中，Intune Exchange connector 停止使用自动发现，而直接连接到 EWS URL。

## <a name="next-steps"></a>后续步骤

有关特定错误的帮助，请尝试[解决 Intune Exchange connector 的常见错误](troubleshoot-exchange-connector-common-errors.md)。

若要获取支持，或从 Intune 社区获取帮助：

- 请参阅[获取支持](../fundamentals/get-support.md)以使用 Intune 控制台排查问题或与 Microsoft 建立支持案例。
- 在[Microsoft Intune 论坛](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod)中发布你的问题。