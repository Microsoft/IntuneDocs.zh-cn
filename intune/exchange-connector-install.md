---
title: 设置 Microsoft Intune 本地 Exchange 连接器
titleSuffix: Microsoft Intune
description: 基于 Intune 注册和 Exchange Active Sync (EAS)，使用本地 Exchange 连接器来管理设备对 Exchange 邮箱的访问。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e236548002f2779377e7ac57443077d48869e1f9
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047695"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>在 Microsoft Intune 中设置 Intune 本地 Exchange 连接器
本文中的信息有助于安装和监视 Intune 的 Exchange Active Sync 本地连接器。  结合使用 Intune 本地 Exchange 连接器与[条件访问策略，以允许或阻止对 Exchange 本地邮箱的访问](conditional-access-exchange-create.md)。 

设备尝试访问本地 Exchange 时，Exchange 连接器会将 Exchange Server 中的 Exchange Active Sync (EAS) 记录映射到 Intune 记录，以检查设备是否使用 Intune 注册，以及是否符合设备符合性策略。 根据条件访问策略，可以允许或阻止设备访问。 如需了解更多详情，请参阅[结合使用 Intune 和条件访问的常见方式有哪些？](conditional-access-intune-common-ways-use.md)

Intune 支持每个订阅安装多个本地 Exchange 连接器。 如果有多个本地 Exchange 组织，则可以为其设置单独的连接器。 但是，每个 Exchange 组织只能安装一个连接器以供使用。 

以下是设置允许 Intune 与本地 Exchange Server 通信的连接的常规步骤：

1. 从 Intune 门户下载 Intune 本地 Exchange 连接器。
2. 在本地 Exchange 组织的计算机上安装和配置 Exchange 连接器。
3. 验证 Exchange 连接。
4. 针对要连接到 Intune 的其他每个 Exchange 组织，请重复这些步骤。

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune 本地 Exchange 连接器的要求
需要具有带 Intune 许可证且可供连接器使用的帐户才能连接到 Exchange。 安装连接器时，指定帐户。  

下表列出了在其中安装本地 Exchange 连接器的计算机的要求。  

|  要求  |   更多信息     |
|---------------|------------------------|
|  操作系统        | Intune 支持在运行任何版本的 Windows Server 2008 SP2 64 位、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的计算机上安装本地 Exchange 连接器。<br /><br />该连接器在任何 Server Core 安装上都不受支持。  |
| Microsoft Exchange          | 本地连接器需要 Microsoft Exchange 2010 SP3 或更高版本或旧版 Exchange Online Dedicated。 若要确定 Exchange Online Dedicated 环境采用的是<strong>新</strong>配置还是<strong>旧</strong>配置，请与帐户管理员联系。 |
| 移动设备管理机构           | [将移动设备管理机构设置为 Intune](mdm-authority-set.md)。 |
| 硬件              | 安装连接器的计算机需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁盘空间。 |
|  Active Directory 同步             | 必须[设置 Active Directory 同步](users-add.md)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用连接器将 Intune 连接到 Exchange Server。 |
| 其他软件         | Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完全安装必须安装在托管连接器的计算机上。 |
| Network (网络)               | 在其中安装连接器的计算机必须位于与托管 Exchange Server 的域具有信任关系的域中。<br /><br />计算机需要配置才能使其通过防火墙和代理服务器在端口 80 和 443 上访问 Intune 服务。 Intune 使用的域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

创建将由本地 Exchange 连接器使用的 Active Directory 用户帐户。 帐户必须具有运行以下要求的 Windows PowerShell Exchange cmdlets 的权限：


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

2. 转到“Intune” > “Exchange 访问”  

3. 在“设置”下，选择“Exchange ActiveSync 本地连接器”，然后选择“添加”。

4. 在“添加连接器”页上，选择“下载本地连接器”。 本地 Exchange 连接器位于可以打开或保存的压缩 (.zip) 文件夹中。 在“文件下载”对话框中，选择“保存”以将压缩的文件夹存储到安全位置。

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

4. 在“用户(域\用户)”和“密码”字段中，输入连接到 Exchange 服务器所需的凭据。 指定的帐户必须具有使用 Intune 的许可证。 

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
Intune 支持每个订阅有多个本地 Exchange 连接器。 对于有多个 Exchange 组织的租户，可以为每个 Exchange 组织设置一个连接器，但是任何一个组织都只能有一个连接器。 

如果要安装连接器以连接到多个 Exchange 组织，请一次性下载 .zip 文件夹，然后为安装的每个连接器重复使用相同的下载文件。 对于每个其他连接器，请按照上一节中的步骤在 Exchange 组织中的服务器上提取并运行安装程序。

每个连接到 Intune 的 Exchange 组织均支持以下各节中所述的高可用性、监视和手动同步功能。

## <a name="on-premises-exchange-connector-high-availability-support"></a>本地 Exchange 连接器高可用性支持 
本地 Exchange 连接器的高可用性意味着，如果连接器使用的 Exchange 客户端访问服务器 (CAS) 变得不可用，则连接器可以转换为使用该 Exchange 组织的其他 CAS。 Exchange 连接器本身不支持高可用性。 如果连接器无法正常工作，则不会进行自动故障转移，必须通过[安装新的连接器](#reinstall-the-on-premises-exchange-connector)来替换该连接器。 

为完成故障转移，在连接器使用指定 CAS 创建与 Exchange 的成功连接后，连接器将发现该 Exchange 组织的其他 CAS。 如果有其他可用的 CAS，可使连接器故障转移到其他 CAS，直到主 CAS 可用，请了解这一点。 默认情况下，启用其他 CAS 的发现。 可以使用以下过程关闭故障转移：  
1. 在安装 Exchange 连接器的服务器上，请转到 %ProgramData%\Microsoft\Windows Intune Exchange Connector。 
2. 使用文本编辑器打开“OnPremisesExchangeConnectorServiceConfiguration.xml”。
3. 将“&lt;IsCasFailoverEnabled&gt;true&lt;/IsCasFailoverEnabled&gt;”更改为“&lt;IsCasFailoverEnabled&gt;false&lt;/IsCasFailoverEnabled&gt;”，禁用此功能。    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>重新安装本地 Exchange 连接器
可能需要重新安装 Exchange 连接器。 由于支持单个连接器连接到每个 Exchange 组织，因此如果为组织安装第二个连接器，则安装的新连接器将替换原始连接器。

1. 使用[安装和配置 Intune 本地 Exchange 连接器](#install-and-configure-the-intune-on-premises-exchange-connector)中的步骤以开始安装新连接器。 
2. 系统出现提示时，请选择“替换”以安装新的连接器。  
   ![替换连接器的配置提示](./media/exchange-connector-install/prompt-to-replace.png)

3. 继续使用上一过程中的步骤，并再次登录 Intune。
4. 系统出现最终屏幕时，选择“关闭”以完成安装。  
   ![完成安装](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>监视 Exchange 连接器活动

在成功配置 Exchange 连接器之后，可以查看连接的状态和最后一次成功同步尝试的状态。 验证 Exchange 连接器的连接：

1. 在 Intune 仪表板上，选择“Exchange 访问”。
2. 选择“Exchange 本地访问”以验证每个 Exchange 连接器的连接状态。

你也可以检查最后一次成功同步尝试的时间和日期。
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager 管理包

自 Intune 1710 发布起，[用于 Exchange 连接器和 Intune 的 Operations Manager 管理包](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)可供使用。 使用管理包，在需要进行问题故障排除时，可提供监视 Exchange 连接器的多种方法。

## <a name="manually-force-a-quick-sync-or-full-sync"></a>手动强制执行快速同步或完全同步
本地 Exchange 连接器会定期自动同步 EAS 和 Intune 设备记录。 如果设备的符合性状态发生更改，则自动同步过程会定期更新记录，以便阻止或允许设备访问。

   - 定期执行“快速同步”，每天执行若干次。 快速同步会检索自上次同步以来发生更改的 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。

   - 默认情况下，每天进行一次“完全同步”。 完全同步会检索所有 Intune 许可用户和本地 Exchange 条件访问目标用户的设备信息。 完全同步还会检索 Exchange 服务器信息，并确保 Azure 门户中 Intune 指定的配置已在 Exchange 服务器上更新。 


可以使用 Intune 仪表板上的“快速同步”或“完全同步”选项强制连接器运行同步，步骤如下：

   1. 在 Intune 仪表板上，选择“Exchange 访问”。
   2. 选择“Exchange 本地访问”。
   3. 选择要同步的连接器，然后选择“快速同步”或“完全同步”。

## <a name="next-steps"></a>后续步骤
[为 Exchange 内部部署创建条件访问策略](conditional-access-exchange-create.md)
