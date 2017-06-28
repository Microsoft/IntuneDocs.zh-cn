---
title: "条件访问疑难解答"
description: "用户无法通过 Intune 条件访问对资源进行访问时可执行的操作。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 04b1785c0b75d4668879488e5221d8b8c2794834
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="troubleshoot-conditional-access"></a>条件访问疑难解答

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

通常情况下，用户在尝试访问电子邮件或 SharePoint 时会收到注册提示。 该提示会使用户转到公司门户。

本主题介绍用户无法通过 Intune 条件访问对资源进行访问时可执行的操作。


## <a name="the-basics-for-success-in-conditional-access"></a>条件访问成功的基础知识

为使条件访问起作用，需满足以下条件：

-   必须由 Intune 管理设备。
-   设备必须注册 Azure Active Directory (AAD)。 正常情况下，此注册在 Intune 注册时自动进行
-   设备必须符合设备或设备用户的 Intune 合规性策略。  如果不存在合规性策略，则 Intune 注册可充分进行。
-   如果用户通过设备的本机邮件客户端而不是通过 Outlook 检索邮件，则必须在设备上激活 Exchange ActiveSync。     此操作在 iOS、Windows Phone 和 Android/KNOX 标准设备上自动进行。
-   Intune Exchange Connector 应正确配置。 有关详细信息，请参阅 [Microsoft Intune 中的 Exchange Connector 疑难解答](troubleshoot-exchange-connector.md)。

可在 Azure 管理门户和设备清单报告中针对各个设备查看这些条件。

## <a name="enrollment-issues"></a>注册问题

 -  设备未注册，因此注册即可解决问题。
 -  用户已注册设备，但工作区加入失败。 用户应从公司门户更新注册。

## <a name="compliance-issues"></a>合规性问题

 -  设备不符合 Intune 策略。 常见的问题是加密和密码要求。 用户将被重定向到公司门户中，他们可在其中配置设备以符合要求。
 -  为设备注册合规性信息需要一点时间。 请稍等几分钟，然后重试。
 -  对于 iOS 设备：
     -   用户创建的现有电子邮件配置文件将阻止由 Intune 管理员创建的配置文件的部署。 这是一个常见问题，因为 iOS 用户通常将创建电子邮件配置文件，然后注册。 公司门户将通知用户由于其手动配置的电子邮件配置文件而导致他们不符合要求，并提示用户删除该配置文件。用户应删除其电子邮件配置文件，以便可以部署 Intune 配置文件。 为防止此问题，请告知用户注册时不要安装电子邮件配置文件，并允许 Intune 部署配置文件。
     -   iOS 设备可能在检查合规性状态过程中受阻，进而阻止用户初始化其他签入。 重启公司门户可能可以修复此问题，且合规性状态将反映 Intune 中的设备状态。 通过设备同步收集所有的数据后，合规性检查将快速进行，平均速度不超过半秒。

        通常，设备保持此状态的原因是其在连接到服务时出现问题或同步花费的时间较长。  如果设备重启且已验证 SSP 在设备上为最新后，此问题继续存在于不同网络配置（移动电话网络、Wi-Fi、VPN）中，请按照[如何获取 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中的说明，与Microsoft 支持人员取得联系。

 - 对于 Android 设备：
    - 某些 Android 设备看似已加密，但公司门户应用还是会将这些设备识别为未加密。 
    
        -   遇到这种情况的设备需要用户设置一个安全启动密码。 用户会在公司门户应用中看到一条设备通知，通知中要求为设备设置一个启动密码。 点击设备通知并确认现有 PIN 或密码后，在“安全启动”屏幕上选择“需要 PIN 才能启动设备”选项。 然后在公司门户应用中点击设备的“检查符合性”按钮。 现在设备应该被标识为已加密。
    
        -   某些设备制造商使用默认 PIN，而不是用户设置的机密 PIN 来加密其设备。 Intune 会将使用默认 PIN 的加密识别为不安全，因为这种加密方式会让设备上的数据受到威胁，使数据可能泄露给对设备具有物理访问权限的恶意用户。 如果存在此问题，建议使用[应用保护策略](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies)。

## <a name="policy-issues"></a>策略问题

创建合规性策略并将其链接到电子邮件策略时，必须将这两个策略部署到同一用户，因此在规划将哪些策略部署到哪些组时需谨慎。 只应用了一个策略的用户很可能发现他们的设备不合规。


## <a name="exchange-activesync-issues"></a>Exchange ActiveSync 问题

### <a name="compliant-android-device-gets-quarantine-notice"></a>合规的 Android 设备收到隔离通知
- 在尝试访问公司资源时，已注册且合规的 Android 设备仍可能会收到隔离通知。 选择显示**开始**的链接之前，用户应确保在尝试访问资源时未打开公司门户。 用户应关闭公司门户，重试访问资源，然后选择**开始**链接。

### <a name="retired-device-continues-to-have-access"></a>已停用的设备继续拥有访问权限。
- 使用 Exchange Online 时，已停用的设备可能会在停用后的几个小时内仍拥有访问权限。 这是因为 Exchange 将缓存访问权限 6 个小时。 在这种情况下，请考虑保护已停用设备上数据的其他方法。

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>设备合规且已注册 AAD 但仍受阻
- 有时 Exchange ActiveSync ID (EASID) 到 AAD 的预配被延迟。 正在限制引发此问题的常见原因，请稍等几分钟，然后重试。

### <a name="device-blocked"></a>设备受阻

设备可能由于未获取激活电子邮件而在条件访问中被阻止。

- 是否存在默认的 Exchange 规则隔离或阻止设备？ 如果默认的规则阻止或隔离设备，设备将无法从 Exchange Connector 中收到激活电子邮件。 这是由于设计而导致的。
- 通知帐户是否按照“基本配置”中的说明正确配置？
- 设备是否作为 Exchange ActiveSync 设备显示在 Intune 管理控制台中？ 如果没有，则设备发现可能会失败，可能是由于 Exchange Connector 同步出现问题。 请在 Exchange 中查看未发现的 Exchange ActiveSync 设备。
- 查看 Exchange Connector 的 sendemail 活动的日志并检查错误。 要搜索的命令示例为从通知帐户到用户邮箱的 SendEmail。
- Exchange Connector 阻止设备前，将发送激活电子邮件。 如果设备未在线，则可能不会收到此激活电子邮件。 查看设备电子邮件客户端是否使用“推送”而非“轮询”进行电子邮件检索，因为这也可能导致用户错过该电子邮件。 切换至“轮询”，然后查看设备是否收到该电子邮件。

## <a name="non-compliant-device-not-blocked"></a>未阻止不合规设备

如果发现不合规但继续拥有访问权限的设备，请按照以下步骤操作。

- 复查目标组和排除组。 如果用户未处于正确的目标组或处于排除组中，则不会将其阻止。 只对目标组中的用户的设备进行合规性检查。
- 请确保设备处于被发现的状态。 Exchange Connector 是否在用户位于 Exchange 2013 服务器上时指向 Exchange 2010 CAS？ 该情况下，如果默认的 Exchange 规则为“允许”，则即使用户处于目标组中，Intune 仍无法发现设备已连接到 Exchange。
- 检查 Exchange 中的设备存在/访问状态：
    - 使用此 PowerShell cmdlet 获取某个邮箱的所有移动设备的列表："Get-ActiveSyncDeviceStatistics -mailbox mbx”。 如果未列出相应设备，则其未在访问 Exchange。
    - 如果列出了相应设备，使用 Get-CASmailbox -identity:’upn’ | fl cmdlet 获取其访问状态的详细信息，然后将此信息提供给 Microsoft 支持。

## <a name="before-you-open-a-support-ticket"></a>在开具支持票证前
如果上述疑难解答步骤未解决你的问题，可能要求你向 Microsoft 支持提供相关信息，如 OWA 邮箱日志或 Exchange Connector 日志。

### <a name="collecting-owa-mailbox-logs"></a>收集 OWA 邮箱日志

1. 通过 OWA 登录，并在右上角你的姓名旁选中设置（齿轮）符号。
2. 选择“选项”
3. 在左侧栏中选择“电话”（可能会显示“移动设备”）。
4. 从顶部菜单中，选择“移动设备”。
5. 从列表中选择你的设备，然后选择“开始记录”。
6. 出现提示时，在弹出的对话框中选择“是”。
7. 执行导致该问题的操作，以便你可以再现它。
8. 请等待 1-2 分钟，然后返回至 OWA 中的电话列表。 请确保你的电话在列表中处于选中状态，然后从顶部菜单中选择“**检索日志**”。
9. 此时，你应会收到一封来自自己的含附件的电子邮件。 当你打开支持票证时，请将电子邮件中的内容提供给 Microsoft 支持。

### <a name="exchange-connector-logs"></a>Exchange Connector 日志

#### <a name="general-log-information"></a>常规日志信息
若要查看 Exchange Connector 日志，请使用 [Server Trace Viewer Tool]（服务跟踪查看器工具 (https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx'）。 此工具需要下载 Windows Server SDK。

>[!NOTE]
>该日志位于 C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs。 该日志包含在 30 个日志文件的系列中，其中以 *Connector0.log* 开始并以 *Connector29.log* 结束。 一个日志中的数据累积 10 MB 后，将滚动更新到另一个日志。 日志到达 Connector29 后，将重新从 Connector0 开始，覆盖先前的日志文件。

#### <a name="locating-sync-logs"></a>定位同步日志

-    通过搜索“**full sync**”定位日志中的完全同步。 完全同步的开始部分将通过以下文本标记：

    'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users`

    完全同步的日志结尾部分显示如下：

    Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. Details: Inventory command result - Devices synced: 0 Commmand ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected','

-   通过搜索“**quick sync**”定位日志中的快速（增量）同步。

##### <a name="exceptions-in-get-next-command"></a>获取下一条命令中的异常
查看针对“**获取下一条命令**”中的异常的 Exchange Connector 日志，并将其提供给 Microsoft 支持。

#### <a name="verbose-logging"></a>详细日志记录

若要启用详细日志记录：

1.  打开 Exchange Connector 跟踪配置文件。 该文件位于：%ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml。
2.  通过以下密钥查找 TraceSourceLine：OnPremisesExchangeConnectorService
3.  如下所示，将“**SourceLevel**”节点值从 **Warning ActivityTracing**（默认值）更改为 **Verbose ActivityTracing**。

    <TraceSourceLine>
          <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key>
          <Value xsi:type="TraceSource">
            <SourceLevel>All</SourceLevel>
            <Listeners>
              <Listener>
                <ListenerType>CircularTraceListener</ListenerType>
                <SourceLevel>Verbose ActivityTracing</SourceLevel>
                <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes>
                <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName>
                <FileQuota>30</FileQuota>
              </Listener>
            </Listeners>
          </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。

