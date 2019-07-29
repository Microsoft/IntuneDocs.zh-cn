---
title: 条件访问疑难解答
titleSuffix: Microsoft Intune
description: 在你的用户无法通过 Intune 条件访问来访问资源时应采取的措施。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14a1e0a4d0df3e5c278028b314a34553f7943f8d
ms.sourcegitcommit: 97a46f0f6a27eda0592ff6518fac46bc2447b622
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68411641"
---
# <a name="troubleshoot-conditional-access"></a>条件访问疑难解答
本文介绍了在你的用户无法访问受条件访问保护的资源时应采取的措施，以及在用户可访问受保护资源但应遭阻止时应采取的措施。

使用 Intune 和条件访问, 你可以保护对以下服务的访问:
- Office 365 服务, 例如 Exchange Online、SharePoint Online 和 Skype for Business Online
- Exchange 内部部署
- 各种其他服务

此功能可确保只有已注册 Intune 且符合你在 Intune 管理控制台或 Azure Active Directory 中设置的条件访问规则的设备，才能访问公司资源。 

## <a name="requirements-for-conditional-access"></a>条件访问要求

必须满足以下要求，条件访问才能正常运行：

- 设备必须注册到 MDM 并由 Intune 管理。

- 用户和设备都必须符合分配的 Intune 符合性策略。

- 默认情况下，必须为用户分配设备符合性策略。 这可能取决于“标记未分配符合性策略的设备”设置的配置，该设置可在 Intune 管理门户中的“设备符合性” > “符合性策略设置”下进行配置    。

- 如果用户使用的是设备的本机邮件客户端而不是 Outlook，则必须在设备上激活 Exchange ActiveSync。 此操作在 iOS、Windows Phone 和 Android Knox 设备上自动进行。

- 对于本地 Exchange, 必须正确配置 Intune Exchange Connector。 有关详细信息，请参阅 [Microsoft Intune 中的 Exchange Connector 疑难解答](troubleshoot-exchange-connector.md)。

- 对于本地 Skype, 必须配置混合新式身份验证。 请参阅[混合新式身份验证概述](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview)。

可在 Azure 门户和设备清单报告中针对各个设备查看这些条件。

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>设备看似符合但用户仍被阻止

- 确保为用户分配了 Intune 许可证, 以便进行适当的符合性评估。

- 只有在用户单击所接收隔离电子邮件中的“立即开始使用”链接后，才会授予非 Knox Android 设备访问权限  。 即使用户已注册 Intune，情况也是如此。 如果用户手机上未收到带有链接的电子邮件，则可以使用电脑访问其电子邮件并将其转发到其设备上的电子邮件帐户。

- 首次注册设备时，为设备注册符合性信息可能需要一点时间。 请稍等几分钟，然后重试。

- 对于 iOS 设备，现有电子邮件配置文件可能会阻止对分配给该用户的电子邮件配置文件（由 Intune 管理员创建）进行部署，从而使设备不符合。 在本方案中，公司门户应用将通知用户由于他们的电子邮件配置文件是手动配置的，因此不符合，并提示用户删除该配置文件。 用户删除现有电子邮件配置文件后，便可成功部署 Intune 电子邮件配置文件。 若要避免此问题，请告知用户在注册前删除其设备上的所有现有电子邮件配置文件。

- 设备可能在检查符合性状态过程中受阻，进而阻止用户启动其他签入。 如果设备处于此状态:
  - 确保设备使用的是最新版本的公司门户应用。
  - 重启设备。
  - 查看问题在不同网络上（例如移动电话、Wi-Fi 等）上是否仍然存在。

  如果问题依然存在，请联系 Microsoft 支持部门，如[获取对 Microsoft Intune 的支持](get-support.md)中所述。

- 某些 Android 设备看似已加密，但公司门户应用还是会将这些设备识别为未加密，并将其标记为不符合。 在此方案中，用户会在公司门户应用中看到一条通知，通知中要求为设备设置一个启动密码。 点击通知并确认现有 PIN 或密码后，在“安全启动”屏幕上选择“需要 PIN 才能启动设备”选项，然后在公司门户应用中点击设备的“检查符合性”按钮    。 现在设备应该被标识为已加密。 

  > [!NOTE]
  > 某些设备制造商使用默认 PIN，而不是用户设置的 PIN 来加密其设备。 Intune 会将使用默认 PIN 的加密视为不安全，并将这些设备标记为不符合设备，直到用户创建新的非默认 PIN。

- 在首次尝试访问公司资源时，已注册且符合的 Android 设备仍可能受阻止并会收到隔离通知。 如果发生这种情况，请确保公司门户应用未运行，然后选择隔离电子邮件中的“立即开始”链接以触发评估  。 仅在首次启用条件访问时才需要执行此操作。

- 已注册的 Android 设备可能会提示用户 "找不到任何证书", 并且不会获得访问 O365 资源的权限。 用户必须在已注册的设备上启用“启用浏览器访问”  选项，如下所示：
  1. 打开公司门户应用。
  2. 通过三个点 (…) 或硬件菜单按钮转到“设置”页面。
  3. 选择“启用浏览器访问”  按钮。
  4. 在 Chrome 浏览器中，从 Office 365 中注销并重启 Chrome。  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>设备受阻止且未收到隔离电子邮件

- 验证设备是否作为 Exchange ActiveSync 设备显示在 Intune 管理控制台中。 如果没有，则设备发现可能会失败，可能是由 Exchange Connector 问题导致。 有关详细信息，请参阅 [Intune On-Premises Exchange 连接器疑难解答](troubleshoot-exchange-connector.md)。

- Exchange 连接器阻止设备之前，将发送激活（隔离）电子邮件。 如果设备已脱机，则可能不会收到此激活电子邮件。 

- 检查设备上的电子邮件客户端是否配置为使用“推送”而不是“轮询”来检索电子邮件   。 如果是这样，则可能会导致用户漏失电子邮件。 切换到“轮询”并查看设备是否收到电子邮件  。

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>设备不符合，但用户未受阻止

- 对于 Windows 电脑，条件访问仅阻止本机电子邮件应用，即启用新式身份验证的 Office 2013 或 Office 2016。 若要在 Windows 电脑上阻止旧版 Outlook 或所有邮件应用，必须按照[为 SharePoint Online 和 Exchange Online 设置 Azure Active Directory 条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication)中的说明操作，执行 AAD 设备注册和 Active Directory 联合身份验证服务 (AD FS) 配置。

- 如果在 Intune 中有选择地擦除或停用设备，设备可能在停用后几个小时内继续拥有访问权限。 这是因为 Exchange 将缓存访问权限六个小时。 在这种情况下，请考虑保护已停用设备上数据的其他方法。

- 当分配了 Intune 许可证的用户登录时, Surface Hub、批量注册和 DEM 注册的 Windows 设备可以支持条件访问。 但是, 必须将合规性策略部署到设备组 (而非用户组), 才能进行正确的评估。

- 检查符合性策略和条件访问策略的分配。 如果用户不在分配了策略的组中, 或者位于排除的组中, 则不会阻止该用户。 只对已分配组中的用户的设备进行符合性检查。

## <a name="noncompliant-device-is-not-blocked"></a>未阻止不符合设备

如果设备不合规但仍有访问权限, 请执行以下操作。

- 复查目标组和排除组。 如果用户未处于正确的目标组或处于排除组中，则不会将其阻止。 只对目标组中的用户的设备进行合规性检查。

- 请确保设备处于被发现的状态。 Exchange Connector 是否在用户位于 Exchange 2013 服务器上时指向 Exchange 2010 CAS？ 该情况下，如果默认的 Exchange 规则为“允许”，则即使用户处于目标组中，Intune 仍无法发现设备已连接到 Exchange。

- 检查 Exchange 中的设备存在/访问状态：
  - 使用此 PowerShell cmdlet 获取某个邮箱的所有移动设备的列表：“Get-ActiveSyncDeviceStatistics -mailbox mbx”。 如果未列出相应设备，则其未在访问 Exchange。
  
  - 如果列出了相应设备，使用“Get-CASmailbox -identity:’upn’ | fl”cmdlet 获取其访问状态的详细信息，然后将此信息提供给 Microsoft 支持部门。

## <a name="next-steps"></a>后续步骤
如果此信息没有帮助，还可以[获取对 Microsoft Intune 的支持](get-support.md)。
