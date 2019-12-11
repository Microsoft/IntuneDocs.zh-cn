---
title: 设置 Microsoft Intune Exchange 连接器
titleSuffix: Microsoft Intune
description: 基于 Intune 注册和 Exchange ActiveSync (EAS)，使用本地 Intune Exchange 连接器来管理设备对 Exchange 邮箱的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62db99fc2e47bdfa1a767db3bb2916649dedc074
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74164688"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>设置本地 Intune Exchange 连接器
为了帮助保护对 Exchange 的访问，Intune 依赖于一个称为 Microsoft Intune Exchange 连接器的本地组件。 在 Intune 控制台的某些位置，此连接器也称为“Exchange ActiveSync 本地连接器”  。 

本文中的信息可帮助你安装和监视 Intune Exchange 连接器。 可结合使用此连接器与[条件访问策略](conditional-access-exchange-create.md)，以允许或阻止对 Exchange 本地邮箱的访问。 

此连接器已安装并在本地硬件上运行。 它可以发现连接到 Exchange 的设备，从而将设备信息与 Intune 服务通信。 此连接器根据设备是否已注册且符合要求来允许或阻止设备。 这些通信使用 HTTPS 协议。

设备尝试访问本地 Exchange Server 时，Exchange 连接器会将 Exchange Server 中的 Exchange ActiveSync (EAS) 记录映射到 Intune 记录，以确保设备使用 Intune 注册且符合设备策略。 根据条件访问策略，可以允许或阻止设备。 如需了解更多详情，请参阅[结合使用 Intune 和条件访问的常见方式有哪些？](conditional-access-intune-common-ways-use.md)

“发现”和“允许和阻止”操作都是使用标准 Exchange PowerShell cmdlet 完成的   。 这些操作使用初始安装 Exchange 连接器时提供的服务帐户。 

Intune 支持每个订阅安装多个 Intune Exchange 连接器。 如果有多个本地 Exchange 组织，则可以为其设置单独的连接器。 但是，每个 Exchange 组织只能安装一个连接器。  

按照以下常规步骤设置允许 Intune 与本地 Exchange Server 通信的连接：

1. 从 Intune 门户下载本地连接器。
2. 在本地 Exchange 组织的计算机上安装和配置 Exchange 连接器。
3. 验证 Exchange 连接。
4. 针对要连接到 Intune 的其他每个 Exchange 组织，请重复这些步骤。

## <a name="intune-exchange-connector-requirements"></a>Intune Exchange 连接器的要求

需要具有带 Intune 许可证且可供连接器使用的帐户才能连接到 Exchange。 安装连接器时，指定帐户。  

下表列出了在其中安装 Intune Exchange 连接器的计算机的要求。  

|  要求  |   更多信息     |
|---------------|------------------------|
|  操作系统        | Intune 支持在运行任何版本的 Windows Server 2008 SP2 64 位、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的计算机上安装 Intune Exchange 连接器。<br /><br />该连接器在任何 Server Core 安装上都不受支持。  |
| Microsoft Exchange          | 本地连接器需要 Microsoft Exchange 2010 SP3 或更高版本或旧版 Exchange Online Dedicated。 若要确定 Exchange Online Dedicated 环境采用的是*新*配置还是*旧*配置，请与帐户管理员联系。 |
| 移动设备管理机构           | [将移动设备管理机构设置为 Intune](../fundamentals/mdm-authority-set.md)。 |
| 硬件              | 安装连接器的计算机需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁盘空间。 |
|  Active Directory 同步             | 在使用连接器将 Intune 连接到 Exchange Server 之前，[设置 Active Directory 同步](../fundamentals/users-add.md)。 本地用户和安全组必须与 Azure Active Directory 的实例同步。 |
| 其他软件         | 托管连接器的计算机必须具有 Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完全安装。 |
| Network (网络)               | 在其中安装连接器的计算机必须位于与托管 Exchange Server 的域具有信任关系的域中。<br /><br />配置计算机，使其通过防火墙和代理服务器在端口 80 和 443 上访问 Intune 服务。 Intune 使用以下域： <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Intune Exchange 连接器与以下服务通信： <br> - Intune 服务：HTTPS 端口 443 <br> - Exchange 客户端访问服务器 (CAS)：WinRM 服务端口 443<br> - Exchange 自动发现 443<br> - Exchange Web 服务 (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

创建 Intune Exchange 连接器的 Active Directory 用户帐户。 帐户必须具有运行以下 Windows PowerShell Exchange cmdlet 的权限：  

- `Get-ActiveSyncOrganizationSettings`、`Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`、`Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`、`Set-ActiveSyncMailboxPolicy`、`New-ActiveSyncMailboxPolicy`、`Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`、`Set-ActiveSyncDeviceAccessRule`、`New-ActiveSyncDeviceAccessRule`、`Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`、`Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>下载安装包

在可支持 Intune Exchange 连接器的 Windows Server 上：

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。  使用属于本地 Exchange Server 中的管理员且具有使用 Exchange Server 的许可证的帐户。

2. 选择“租户管理” > “Exchange 访问”   。  

3. 在“设置”下，选择“Exchange ActiveSync 本地连接器”，然后选择“添加”    。

4. 在“添加连接器”页上，选择“下载本地连接器”   。 Intune Exchange 连接器位于可以打开或保存的压缩 (.zip) 文件夹中。 在“文件下载”  对话框中，选择“保存”  以将压缩的文件夹存储到安全位置中。

## <a name="install-and-configure-the-intune-exchange-connector"></a>安装和配置 Intune Exchange 连接器

按照以下步骤安装 Intune Exchange 连接器。 如果有多个 Exchange 组织，请为每个要设置的 Exchange 连接器重复这些步骤。

1. 在支持 Intune Exchange 连接器的操作系统上，将“Exchange_Connector_Setup.zip”中的文件提取到安全位置  。
   > [!IMPORTANT]
   > 请勿重命名或移动 Exchange_Connector_Setup  文件夹中的文件。 这些更改将导致连接器安装失败。

2. 提取文件后，打开提取的文件夹并双击“Exchange_Connector_Setup.exe”，以安装连接器  。

   > [!IMPORTANT]
   > 如果目标文件夹不是安全位置，则在完成安装本地连接器后删除证书文件“MicrosoftIntune.accountcert”  。

3. 在“Microsoft Intune Exchange Connector”  对话框中，选择“本地 Microsoft Exchange Server”  或“托管 Microsoft Exchange Server”  。

   ![显示选择 Exchange Server 类型的位置的图像](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   对于本地 Exchange 服务器，请提供托管**客户端访问服务器**角色的 Exchange 服务器的服务器名称或完全限定的域名。

   对于托管 Exchange 服务器，请提供 Exchange 服务器地址。 查找托管 Exchange 服务器 URL：

   1. 打开 Outlook for Office 365。

   2. 选择左上角的 **?** 图标 ，然后选择“关于”  。

   3. 找到“POP 外部服务器”  值。

   4. 选择“代理服务器”  以指定托管 Exchange 服务器的代理服务器设置。

       1. 选择“同步移动设备信息时使用代理服务器”  。

       1. 输入要用于访问服务器的 **代理服务器名称** 和 **端口号** 。

       1. 如果必须提供用户凭据来访问代理服务器，请选择“使用凭据连接到代理服务器”  。 然后输入“域\用户”  和“密码”  。

       1. 选择“确定”  。

4. 在“用户(域\用户)”  和“密码”  字段中，输入用于连接到 Exchange Server 的凭据。 指定的帐户必须具有使用 Intune 的许可证。 

5. 提供凭据，将通知发送到用户的 Exchange Server 邮箱。 此用户可专用于通知。 通知用户需要 Exchange 邮箱才能通过电子邮件发送通知。 可使用 Intune 中的条件访问策略配置这些通知。  

   确保在 Exchange CAS 上配置自动发现服务和 Exchange Web 服务。 有关详细信息，请参阅[客户端访问服务器](https://technet.microsoft.com/library/dd298114.aspx)。

6. 在“密码”  字段中提供此帐户的密码，使 Intune 能够访问 Exchange Server。

   > [!NOTE]
   > 用于登录租户的帐户必须至少是 Intune 服务管理员。 如果没有此管理员帐户，则会导致连接失败，并出现错误“远程服务器返回错误:(400) 错误请求。”

7. 选择“连接”  。

   > [!NOTE]
   > 可能需要几分钟时间才能配置该连接。

在配置期间，Exchange 连接器会存储代理设置以便能够访问 Internet。 如果代理设置发生更改，则重新配置 Exchange 连接器才能将更新的代理设置应用于 Exchange 连接器。

Exchange 连接器设置连接后，与 Exchange 管理的用户关联的移动设备会自动同步并添加到 Exchange 连接器中。 此同步可能需要一些时间才能完成。

> [!NOTE]
> 如果安装 Intune Exchange 连接器，并且稍后需要删除 Exchange 连接，则必须从安装该连接器的计算机中将其卸载。

## <a name="install-connectors-for-multiple-exchange-organizations"></a>为多个 Exchange 组织安装连接器

Intune 支持每个订阅有多个 Intune Exchange 连接器。 对于拥有多个 Exchange 组织的租户，只能为每个 Exchange 组织设置一个连接器。 

若要安装连接器以连接到多个 Exchange 组织，请下载一次 .zip 文件夹。 为你安装的每个连接器重复使用相同的下载。 对于每个其他连接器，请按照上一节中的步骤在 Exchange 组织中的服务器上提取并运行安装程序。

连接到 Intune 的每个 Exchange 组织都支持高可用性、监视和手动同步。以下部分介绍这些功能。

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>本地 Intune Exchange 连接器高可用性支持  

对于本地连接器，高可用性意味着，如果连接器使用的 Exchange CAS 变得不可用，则连接器可以转换为该 Exchange 组织的其他 CAS。 Exchange 连接器本身不支持高可用性。 如果连接器出现故障，不会进行自动故障转移。 必须[安装新的连接器](#reinstall-the-intune-exchange-connector)才能替换失败的连接器。

若要进行故障转移，连接器需使用指定的 CAS 来创建与 Exchange 的成功连接。 然后发现该 Exchange 组织的其他 CAS。 如果有可用的 CAS，此发现可使连接器故障转移到其他 CAS，直到主 CAS 可用。

默认情况下，发现其他 CAS 是启用的。 如果需要关闭故障转移：

1. 在安装 Exchange 连接器的服务器上，请转到 %ProgramData%\Microsoft\Windows Intune Exchange Connector  。

2. 使用文本编辑器打开“OnPremisesExchangeConnectorServiceConfiguration.xml”  。

3. 将 \<IsCasFailoverEnabled>true\</IsCasFailoverEnabled>  更改为 \<IsCasFailoverEnabled>false\</IsCasFailoverEnabled>  。

## <a name="performance-tune-the-exchange-connector-optional"></a>优化 Exchange 连接器的性能（可选）

Exchange ActiveSync 支持 5,000 台或更多设备时，可以配置可选设置以提高连接器的性能。 通过使 Exchange 能够使用 PowerShell 命令运行空间的多个实例，可以提高性能。

在进行此更改之前，请确保用于运行 Exchange 连接器的帐户不用于其他 Exchange 管理目的。 Exchange 帐户具有有限数量的运行空间，连接器将使用其中的大多数空间。

性能优化不适用于在较旧或性能低下的硬件上运行的连接器。

若要提高 Exchange 连接器的性能，请执行以下操作：

1. 在安装了连接器的服务器上，打开连接器的安装目录。  默认位置是 C:\ProgramData\Microsoft\Windows Intune Exchange Connector  。

2. 编辑文件 OnPremisesExchangeConnectorServiceConfiguration.xml  。

3. 找到“EnableParallelCommandSupport”并将值设置为“true”   ：

   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>

4. 保存文件，然后重启 Microsoft Intune Exchange 连接器服务。

## <a name="reinstall-the-intune-exchange-connector"></a>重新安装 Intune Exchange 连接器

可能需要重新安装 Intune Exchange 连接器。 由于只有单个连接器才能连接到每个 Exchange 组织，因此如果为组织安装第二个连接器，则安装的新连接器将替换原始连接器。

1. 若要安装新的连接器，请按照[安装和配置 Exchange 连接器](#install-and-configure-the-intune-exchange-connector)部分中的步骤进行操作。

2. 系统出现提示时，请选择“替换”以安装新的连接器  。
   ![替换连接器的配置警告](./media/exchange-connector-install/prompt-to-replace.png)

3. 继续[安装和配置 Intune Exchange 连接器](#install-and-configure-the-intune-exchange-connector)部分中的步骤，然后再次登录到 Intune。

4. 在最后一个窗口中，选择“关闭”  以完成安装。
   ![完成设置](./media/exchange-connector-install/successful-reinstall.png)

## <a name="monitor-an-exchange-connector"></a>监视 Exchange 连接器

在成功配置 Exchange 连接器之后，可以查看连接的状态和上次成功同步尝试的状态。

验证 Exchange 连接器的连接：

1. 在 Intune 仪表板上，选择“Exchange 访问”  。

2. 选择“Exchange 本地访问”以验证每个 Exchange 连接器的连接状态  。

你也可以检查最后一次成功同步尝试的时间和日期。

自 Intune 1710 发布起，[用于 Exchange 连接器和 Intune 的 System Center Operations Manager 管理包](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)可供使用。 在需要进行问题故障排除时，管理包可提供监视 Exchange 连接器的多种方法。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手动强制执行快速同步或完全同步

Intune Exchange 连接器会定期自动同步 EAS 和 Intune 设备记录。 如果设备的符合性状态发生更改，则自动同步过程会定期更新记录，以便阻止或允许设备访问。

- 定期执行“快速同步”，每天执行若干次  。 快速同步会检索自上次同步以来发生更改的 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。

- 默认情况下，每天进行一次“完全同步”  。 完全同步会检索所有 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。 完全同步还会检索 Exchange Server 信息，并确保 Azure 门户中 Intune 指定的配置已在 Exchange Server 上更新。

可以使用 Intune 仪表板上的“快速同步”或“完全同步”选项强制连接器运行同步   ：

   1. 在 Intune 仪表板上，选择“Exchange 访问”  。

   2. 选择“Exchange 本地访问”  。

   3. 选择要同步的连接器，然后选择“快速同步”或“完全同步”   。

## <a name="next-steps"></a>后续步骤

[为本地 Exchange 服务器创建条件访问策略](conditional-access-exchange-create.md)。
