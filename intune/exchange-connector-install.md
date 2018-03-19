---
title: "设置 Microsoft Intune 本地 Exchange 连接器"
titleSuffix: 
description: "基于 Intune 注册和 Exchange Active Sync (EAS)，使用本地 Exchange 连接器来管理设备对 Exchange 邮箱的访问。"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0caea2e8b7704fe2dfcbec937b59000ac2a12ae5
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>在 Microsoft Intune Azure 中设置 Intune 本地 Exchange Connector

基于设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略，本地 Exchange Server 环境可以使用 Intune 本地 Exchange 连接器来管理设备对本地 Exchange 邮箱的访问。 本地 Exchange Connector 还负责通过使用 Intune 与现有的 Exchange Active Sync (EAS) 记录同步，发现连接到本地 Exchange Server 的移动设备。

> [!IMPORTANT]
> Intune 仅支持每个订阅中存在一个本地 Exchange Connector 连接（任意类型）。

若要设置允许 Microsoft Intune 与本地 Exchange Server 通信的连接，你需要遵循以下步骤：

1.  从 Azure 门户下载 Intune 本地 Exchange Connector。
2.  安装和配置 Intune 本地 Exchange Connector。
3.  验证 Exchange 连接。

## <a name="on-premises-exchange-connector-requirements"></a>本地 Exchange Connector 的要求
下表列出了你在其中安装本地 Exchange Connector 的计算机的要求。

|要求|更多信息|
|---------------|--------------------|
|操作系统|Intune 支持在运行任何版本的 Windows Server 2008 SP2 64 位、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 或 Windows Server 2016 的计算机上安装本地 Exchange Connector。<br /><br />该连接器在任何 Server Core 安装上都不受支持。|
|Microsoft Exchange|本地连接器需要 Microsoft Exchange 2010 SP1 或更高版本或旧版 Exchange Online Dedicated。 若要确定 Exchange Online Dedicated 环境采用的是**新**配置还是**旧**配置，请与帐户管理员联系。|
|移动设备管理机构| [将移动设备管理机构设置为 Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set)。|
|硬件|安装连接器的计算机需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁盘空间。|users-add.md
|Active Directory 同步|必须[设置 Active Directory 同步](users-add.md)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用连接器将 Intune 连接到 Exchange Server。|
|其他软件|Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完全安装必须安装在托管连接器的计算机上。|
|Network (网络)|在其中安装连接器的计算机必须位于与托管 Exchange Server 的域具有信任关系的域中。<br /><br />计算机需要配置才能使其通过防火墙和代理服务器在端口 80 和 443 上访问 Intune 服务。 Intune 使用的域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。|


### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

你必须创建 Intune Exchange Connector 使用的 Active Directory 用户帐户。 帐户必须具有运行以下要求的 Windows PowerShell Exchange cmdlets 的权限：


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>下载本地 Exchange Connector 软件安装包

1. 在本地 Exchange Connector 支持的 Windows Server 操作系统上，使用用户帐户（该帐户是本地 Exchange server 中的管理员且有使用 Exchange Server 的许可证）打开 [Azure 门户](http://portal.azure.com)。

2. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3. 选择 Intune 后，即打开“Intune 仪表板”，选择“本地访问”。

4. 选择“Exchange ActiveSync 连接器”，然后选择“下载本地连接器”。

5.  本地 Exchange Connector 包含在可以打开或保存的压缩 (.zip) 文件夹中。 在“文件下载”对话框中，选择“保存”以将压缩的文件夹存储到安全位置。

    > [!IMPORTANT]
    > 请勿重命名或移动本地 Exchange Connector 文件夹中的文件。 移动或重命名该文件夹的内容将导致 Exchange Connector 安装失败。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>安装和配置 Intune On-Premises Exchange Connector
执行下列步骤以安装 Intune On-Premises Exchange Connector。 每个 Intune 订阅只能安装一次本地 Exchange Connector，并且只能安装在一台计算机上。 如果尝试配置其他本地 Exchange Connector，新连接将替换原始连接。

1.  在支持本地连接器的操作系统上，将 **Exchange_Connector_Setup.zip** 中的文件提取到安全位置。

2.  提取文件后，打开提取的文件夹并双击 **Exchange_Connector_Setup.exe** 安装本地 Exchange Connector。

    > [!IMPORTANT]
    > 如果目标文件夹不是安全位置，则应该在安装本地连接器之后删除证书文件 **WindowsIntune.accountcert**。

3.  在“Microsoft Intune Exchange Connector”对话框中，选择“本地 Microsoft Exchange Server” 或“托管 Microsoft Exchange Server”。

  ![显示选择 Exchange Server 类型的位置的图像](./media/intune-sa-exchange-connector-config.png)

  对于本地 Exchange 服务器，请提供托管**客户端访问服务器**角色的 Exchange 服务器的服务器名称或完全限定的域名。

  对于托管 Exchange 服务器，请提供 Exchange 服务器地址。 查找托管 Exchange 服务器 URL：

    1. 打开 Outlook Web App for Office 365。

    2. 选择左上角的 **?** 图标 然后选择“关于”。

    3. 找到“POP 外部服务器”  值。

    4. 选择“代理服务器”以指定托管 Exchange 服务器的代理服务器设置。
        1. 选择“同步移动设备信息时使用代理服务器” 。

        2. 输入要用于访问服务器的 **代理服务器名称** 和 **端口号** 。

        3. 如果必须提供用户凭据来访问代理服务器，请选择“使用凭据连接到代理服务器”。 然后输入“域\用户”和“密码”。

        4. 选择“确定”。

    5. 在“用户(域\用户)”和“密码”字段中，输入连接到 Exchange 服务器所需的凭据。

    6.  提供必要的凭据，将通知发送到用户的 Exchange Server 邮箱。 此用户可专用于通知。 通知用户需要 Exchange 邮箱才能通过电子邮件发送通知。 可使用 Intune 中的条件访问策略配置这些通知。  

        确保在 Exchange 客户端访问服务器上配置 Autodiscover 服务和 Exchange Web 服务。 有关详细信息，请参阅[客户端访问服务器](https://technet.microsoft.com/library/dd298114.aspx)。

    7.  在“密码”字段中提供此帐户的密码，使 Intune 能够访问 Exchange 服务器。

    8. 选择“连接”。

    > [!NOTE]
    > 可能需要几分钟时间才能完成配置该连接。

在配置期间，Exchange Connector 会存储你的代理设置以便能够访问 Internet。 如果代理设置发生更改，则必须重新配置 Exchange Connector 才能将更新的代理设置应用于 Exchange Connector。

Exchange Connector 设置连接后，与在 Exchange Connector 中管理的用户关联的移动设备会自动同步并添加到 Exchange Connector 中。 此同步可能需要一些时间才能完成。

> [!NOTE]
> 如果已经安装了本地 Exchange Connector 并且在某一时刻删除 Exchange 连接，则必须从安装了本地 Exchange Connector 的计算机中卸载此软件。

## <a name="on-premises-exchange-connector-high-availability-support"></a>本地 Exchange 连接器高可用性支持 
使用指定的 CAS 建立与 Exchange 的连接后，Exchange 连接器就可以发现其他 CAS。 如果主 CAS 不可用，在主 CAS 的故障修复前，连接器会先故障转移到其他可用的 CAS。 此功能默认处于启用状态。 可以按照下面的过程操作，禁用此功能：
1. 在安装 Exchange Connector 的服务器上，依次转到“%*ProgramData*%\Microsoft\Windows Intune Exchange Connector”。 
2. 使用文本编辑器打开“OnPremisesExchangeConnectorServiceConfiguration.xml”。
3. 将“&lt;IsCasFailoverEnabled&gt;true&lt;/IsCasFailoverEnabled&gt;”更改为“&lt;IsCasFailoverEnabled&gt;false&lt;/IsCasFailoverEnabled&gt;”，禁用此功能。    


## <a name="monitor-the-exchange-connector-activity"></a>监视 Exchange 连接器活动

在成功配置 Exchange Connector 之后，可以查看连接的状态和最后一次成功同步尝试的状态。 若要验证验证 Exchange Connector 连接：

1. 在“Intune 仪表板”中，选择“本地访问”。
2. 在“管理”下，选择“Exchange 本地访问”以验证连接状态。

你也可以检查最后一次成功同步尝试的时间和日期。

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) 管理包

自 Intune 1710 发布起，[用于 Exchange 连接器和 Intune 的 SCOM 管理包](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)可供使用。 它在你需要进行问题故障排除时，可提供监视 Exchange 连接器的多种方式。

## <a name="next-steps"></a>后续步骤
[为 Exchange 内部部署创建条件访问策略](conditional-access-exchange-create.md)
