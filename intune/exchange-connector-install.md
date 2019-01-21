---
title: 设置 Microsoft Intune 本地 Exchange 连接器 | Microsoft Intune
description: 基于 Intune 注册和 Exchange Active Sync (EAS)，使用本地 Exchange 连接器来管理设备对 Exchange 邮箱的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3e66dd3d77cc36a6d311afea82e0f2087b469495
ms.sourcegitcommit: 8c1590db761cc411369cae26677f909d3a8ca297
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2019
ms.locfileid: "54239585"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>在 Microsoft Intune Azure 中设置 Intune 本地 Exchange 连接器

在本地 Exchange Server 环境中，Intune 条件访问可用于允许或阻止访问 Exchange 本地邮箱。 使用 Exchange Active Sync 本地连接器将 Intune 连接到 Exchange 组织，并设置 Intune 条件访问以及设备符合性策略。 然后，当设备尝试连接到 Exchange 时，Intune 会确定该设备是否注册到 Intune 以及是否合规。 若要确定在 Intune 中注册哪些设备，本地 Exchange 连接器会将 Exchange Server 中的 Exchange Active Sync (EAS) 记录映射到 Intune 记录。 有关此工作方式的详细信息，请参阅[通过 Intune 使用条件访问的常见方式有哪些？](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune 现支持每个订阅有多个本地 Exchange 连接器。 如果你拥有多个本地Exchange组织，则可以为每个 Exchange 组织设置一个单独的连接器。

若要设置允许 Microsoft Intune 与本地 Exchange Server 通信的连接，可采用以下常规步骤：

1.  从 Azure 门户下载 Intune 本地 Exchange 连接器。
2.  在本地 Exchange 组织的计算机上安装和配置 Exchange 连接器。
3.  验证 Exchange 连接。
4. 对要连接到 Intune 的每个 Exchange 组织重复这些步骤。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune 本地 Exchange 连接器的要求
下表列出了在其中安装本地 Exchange 连接器的计算机的要求。


|            要求             |                                                                                                                                                                                                        更多信息                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         操作系统          |                                                               Intune 支持在运行任何版本的 Windows Server 2008 SP2 64 位、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的计算机上安装本地 Exchange 连接器。<br /><br />该连接器在任何 Server Core 安装上都不受支持。                                                                |
|         Microsoft Exchange         |                                                                           本地连接器需要 Microsoft Exchange 2010 SP3 或更高版本或旧版 Exchange Online Dedicated。 若要确定 Exchange Online Dedicated 环境采用的是<strong>新</strong>配置还是<strong>旧</strong>配置，请与帐户管理员联系。                                                                           |
| 移动设备管理机构 |                                                                                                                              [将移动设备管理机构设置为 Intune](mdm-authority-set.md)。                                                                                                                               |
|              硬件              |                                                                                                                                                     安装连接器的计算机需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁盘空间。                                                                                                                                                      |
|  Active Directory 同步  |                                                                                      必须[设置 Active Directory 同步](users-add.md)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用连接器将 Intune 连接到 Exchange Server。                                                                                      |
|        其他软件         |                                                                                                                                           Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完全安装必须安装在托管连接器的计算机上。                                                                                                                                           |
|              Network (网络)               | 在其中安装连接器的计算机必须位于与托管 Exchange Server 的域具有信任关系的域中。<br /><br />计算机需要配置才能使其通过防火墙和代理服务器在端口 80 和 443 上访问 Intune 服务。 Intune 使用的域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

必须创建本地 Exchange 连接器使用的 Active Directory 用户帐户。 帐户必须具有运行以下要求的 Windows PowerShell Exchange cmdlets 的权限：


 -   Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox、Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy、Set-ActiveSyncMailboxPolicy、New-ActiveSyncMailboxPolicy、Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice、Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>下载本地 Exchange 连接器软件安装包

1. 在本地 Exchange 连接器支持的 Windows Server 操作系统上，使用用户帐户（该帐户是本地 Exchange Server 中的管理员且有使用 Exchange Server 的许可证）打开 [Azure 门户](https://portal.azure.com)。

2. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3. 选择“Intune”，并在“Intune 仪表板”打开时，选择“本地访问”。

4. 在“安装”下，选择“Exchange ActiveSync 连接器”，然后选择“下载本地连接器”。

5.  本地 Exchange 连接器位于可以打开或保存的压缩 (.zip) 文件夹中。 在“文件下载”对话框中，选择“保存”以将压缩的文件夹存储到安全位置。

    > [!IMPORTANT]
    > 请勿重命名或移动本地 Exchange 连接器文件夹中的文件。 移动或重命名该文件夹的内容将导致 Exchange 连接器安装失败。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>安装和配置 Intune 本地 Exchange 连接器
执行下列步骤以安装 Intune 本地 Exchange 连接器。 如果有多个 Exchange 组织，请为每个要设置的其他 Exchange 连接器重复这些步骤。

1. 在支持本地 Exchange 连接器的操作系统上，将“Exchange_Connector_Setup.zip”中的文件提取到安全位置。

2. 提取文件后，打开提取的文件夹并双击“Exchange_Connector_Setup.exe”，以安装本地 Exchange 连接器。

   > [!IMPORTANT]
   > 如果目标文件夹不是安全位置，则应该在完成安装本地连接器后删除证书文件“MicrosoftIntune.accountcert”。

3. 在“Microsoft Intune Exchange Connector”对话框中，选择“本地 Microsoft Exchange Server” 或“托管 Microsoft Exchange Server”。

   ![显示选择 Exchange Server 类型的位置的图像](./media/intune-sa-exchange-connector-config.png)

   对于本地 Exchange 服务器，请提供托管**客户端访问服务器**角色的 Exchange 服务器的服务器名称或完全限定的域名。

   对于托管 Exchange 服务器，请提供 Exchange 服务器地址。 查找托管 Exchange 服务器 URL：

   1. 打开 Office 365 Web 上的 Outlook。

   2. 选择左上角的 **?** 图标 然后选择“关于”。

   3. 找到“POP 外部服务器”  值。

   4. 选择“代理服务器”以指定托管 Exchange 服务器的代理服务器设置。
       1. 选择“同步移动设备信息时使用代理服务器” 。

       2. 输入要用于访问服务器的 **代理服务器名称** 和 **端口号** 。

       3. 如果必须提供用户凭据来访问代理服务器，请选择“使用凭据连接到代理服务器”。 然后输入“域\用户”和“密码”。

       4. 选择“确定”。

4. 在“用户(域\用户)”和“密码”字段中，输入连接到 Exchange 服务器所需的凭据。

5. 提供必要的凭据，将通知发送到用户的 Exchange Server 邮箱。 此用户可专用于通知。 通知用户需要 Exchange 邮箱才能通过电子邮件发送通知。 可使用 Intune 中的条件访问策略配置这些通知。  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. 在“密码”字段中提供此帐户的密码，使 Intune 能够访问 Exchange 服务器。

7. 选择“连接”。

   > [!NOTE]
   > 可能需要几分钟时间才能完成配置该连接。

在配置期间，Exchange 连接器会存储代理设置以便能够访问 Internet。 如果代理设置发生更改，则必须重新配置 Exchange 连接器才能将更新的代理设置应用于 Exchange 连接器。

Exchange 连接器设置连接后，与在 Exchange 中管理的用户关联的移动设备会自动同步并添加到 Exchange 连接器中。 此同步可能需要一些时间才能完成。

> [!NOTE]
> 如果已经安装了本地 Exchange 连接器并且在某一时刻删除 Exchange 连接，则必须从安装了本地 Exchange 连接器的计算机中卸载此软件。

## <a name="install-connectors-for-multiple-exchange-organizations"></a>为多个 Exchange 组织安装连接器
Intune 支持每个订阅有多个本地 Exchange 连接器。 对于拥有多个 Exchange 组织的租户，可以为每个 Exchange 组织设置一个连接器。 下载一次 .zip 文件夹，然后按照上一节中的步骤为每个 Exchange 组织提取并运行组织服务器上的安装程序。

每个连接到 Intune 的 Exchange 组织均支持以下各节中所述的高可用性、监控和手动同步功能。

## <a name="on-premises-exchange-connector-high-availability-support"></a>本地 Exchange 连接器高可用性支持 
使用指定的 CAS 建立与 Exchange 的连接后，Exchange 连接器就可以发现其他 CAS。 如果主 CAS 不可用，在主 CAS 的故障修复前，连接器会先故障转移到其他可用的 CAS。 此功能默认处于启用状态。 可以按照下面的过程操作，禁用此功能：
1. 在安装 Exchange Connector 的服务器上，依次转到“%*ProgramData*%\Microsoft\Windows Intune Exchange Connector”。 
2. 使用文本编辑器打开“OnPremisesExchangeConnectorServiceConfiguration.xml”。
3. 将“&lt;IsCasFailoverEnabled&gt;true&lt;/IsCasFailoverEnabled&gt;”更改为“&lt;IsCasFailoverEnabled&gt;false&lt;/IsCasFailoverEnabled&gt;”，禁用此功能。    


## <a name="monitor-the-exchange-connector-activity"></a>监视 Exchange 连接器活动

在成功配置 Exchange 连接器后，可以查看连接的状态和最后一次成功同步尝试的状态。 若要验证 Exchange 连接器的连接：

1. 在“Intune 仪表板”中，选择“本地访问”。
2. 在“安装”下，选择“Exchange ActiveSync 连接器”以验证每个 Exchange 连接器的连接状态。

你也可以检查最后一次成功同步尝试的时间和日期。

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager 管理包

自 Intune 1710 发布起，[用于 Exchange 连接器和 Intune 的 Operations Manager 管理包](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)可供使用。 它在你需要进行问题故障排除时，可提供监视 Exchange 连接器的多种方式。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手动强制执行快速同步或完全同步
本地 Exchange 连接器会定期自动同步 EAS 和 Intune 设备记录。 如果设备的符合性状态发生更改，则自动同步过程会定期更新记录，以便相应地阻止或允许设备访问。

   - 定期执行“快速同步”，每天执行若干次。 快速同步会检索自上次同步以来发生更改的 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。

   - 默认情况下，每天进行一次“完全同步”。 完全同步会检索所有 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。 完全同步还会检索 Exchange 服务器信息，并确保 Azure 门户中 Intune 指定的配置已在 Exchange 服务器上更新。 

可以使用 Intune 仪表板上的“快速同步”或“完全同步”选项强制连接器运行同步，步骤如下：

   1. 在“Intune 仪表板”上，选择“本地访问”。
   2. 在“安装”下，选择“Exchange Active Sync 连接器”。
   3. 选择要同步的连接器，然后选择“快速同步”或“完全同步”。

## <a name="next-steps"></a>后续步骤
[为 Exchange 内部部署创建条件访问策略](conditional-access-exchange-create.md)
