---
title: "本地 EAS 的 Exchange 连接器"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：Exchange ActiveSync MDM - 使用连接器工具启用 Intune 管理控制台和本地 Exchange Server 之间的通信"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 8f31db9ba2c57277c90315a7a395cae8012b37f0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017


---

# <a name="install-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure-preview"></a>在 Microsoft Intune Azure 预览版中安装 Intune 本地 Exchange Connector

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


若要设置连接以使 Microsoft Intune 能够与托管移动设备邮箱的 Exchange Server 通信，则必须从 Intune 管理控制台下载和配置本地 Exchange Connector。 Intune 仅支持每个订阅中存在一个 Exchange Connector 连接（任意类型）。

## <a name="on-premises-exchange-connector-requirements"></a>本地 Exchange Connector 的要求
下表列出了你在其中安装本地 Exchange Connector 的计算机的要求。

|要求|更多信息|
|---------------|--------------------|
|操作系统|Intune 支持在运行任何版本的 Windows Server 2008 SP2 64 位、Windows Server 2008 R2、Windows Server 2012 或 Windows Server 2012 R2 的计算机上安装 本地 Exchange Connector。<br /><br />该连接器在任何 Server Core 安装上都不受支持。|
|Microsoft Exchange|本地连接器需要 Microsoft Exchange 2010 SP1 或更高版本或旧版 Exchange Online Dedicated。 若要确定 Exchange Online Dedicated 环境采用的是**新**配置还是**旧**配置，请与帐户管理员联系。|
|移动设备管理机构| [将移动设备管理机构设置为 Intune](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)。|
|硬件|安装连接器的计算机需要 1.6 GHz CPU、2 GB RAM 和 10 GB 可用磁盘空间。|
|Active Directory 同步|必须[设置 Active Directory 同步](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用连接器将 Intune 连接到 Exchange Server。|
|其他软件|Microsoft .NET Framework 4.5 和 Windows PowerShell 2.0 的完全安装必须安装在托管连接器的计算机上。|
|网络|在其中安装连接器的计算机必须位于与托管 Exchange Server 的域具有信任关系的域中。<br /><br />计算机需要配置才能使其通过防火墙和代理服务器在端口 80 和 443 上访问 Intune 服务。 Intune 使用的域包括 manage.microsoft.com、&#42;manage.microsoft.com 和 &#42;.manage.microsoft.com。|


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

1. 在本地 Exchange Connector 支持的 Windows Server 操作系统上，使用用户帐户（该帐户是 Exchange 租户中的管理员且有使用 Exchange Server 的许可证）打开 [Azure 门户](http://portal.azure.com)。

2.  选择“条件访问”工作负荷。
3.  在 Azure 门户中选择“条件访问”工作负荷以打开“本地”边栏选项卡。

4. 在“设置”部分中，选择“Exchange ActiveSync 本地连接器”，然后选择“下载本地连接器”。

4.  本地 Exchange Connector 包含在可以打开或保存的压缩 (.zip) 文件夹中。 在“文件下载”对话框中，选择“保存”以将压缩的文件夹存储到安全位置。

> [!IMPORTANT]
> 请勿重命名或移动本地 Exchange Connector 文件夹中的文件。 移动或重命名该文件夹的内容将导致安装失败。

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>安装和配置 Intune On-Premises Exchange Connector
执行下列步骤以安装 Intune On-Premises Exchange Connector。 每个 Intune 订阅只能安装一次本地 Exchange Connector，并且只能安装在一台计算机上。 如果尝试配置其他本地 Exchange Connector，新连接将替换原始连接。

1.  在支持本地连接器的操作系统上，将 **Exchange_Connector_Setup.zip** 中的文件提取到安全位置。

2.  提取文件后，打开提取的文件夹并双击 **Exchange_Connector_Setup.exe** 安装本地 Exchange Connector。

    > [!IMPORTANT]
    > 如果目标文件夹不是安全位置，则应该在安装本地连接器之后删除证书文件 **WindowsIntune.accountcert**。

3.  在“Microsoft Intune Exchange Connector”对话框中，选择“本地 Microsoft Exchange Server” 或“托管 Microsoft Exchange Server”。

  ![选择 Exchange 服务器类型](../media/intune-sa-exchange-connector-config.png)

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

    6.  提供必要的管理凭据将通知发送到用户的 Exchange Server 邮箱。 可使用 Intune 中的条件访问策略配置这些通知。

        确保在 Exchange 客户端访问服务器上配置 Autodiscover 服务和 Exchange Web 服务。 有关详细信息，请参阅[客户端访问服务器](https://technet.microsoft.com/library/dd298114.aspx)。

    7.  在“密码”字段中提供此帐户的密码，使 Intune 能够访问 Exchange 服务器。

    8. 选择“连接”。

可能需要几分钟时间才能完成配置该连接。

在配置期间，Exchange Connector 会存储你的代理设置以便能够访问 Internet。 如果代理设置发生更改，则必须重新配置 Exchange Connector 才能将更新的代理设置应用于 Exchange Connector。

Exchange Connector 设置连接后，与在 Exchange Connector 中管理的用户关联的移动设备会自动同步并添加到 Exchange Connector 中。 此同步可能需要一些时间才能完成。

> [!NOTE]
> 如果已经安装了本地 Exchange Connector 并且在某一时刻删除 Exchange 连接，则必须从安装了本地 Exchange Connector 的计算机中卸载此软件。

## <a name="validate-the-exchange-connection"></a>验证 Exchange 连接

在成功配置 Exchange Connector 之后，可以查看连接的状态和最后一次成功同步尝试的状态。 在 [Azure 门户](http://portal.azure.com)中，选择“Intune” > “条件访问”工作负荷。 在“设置”下，选择“Exchange 本地连接器”，然后验证连接是否显示为活动状态。

你也可以检查最后一次成功同步尝试的时间和日期。

## <a name="next-steps"></a>后续步骤
[为 Exchange 内部部署创建条件访问策略](create-conditional-access-policy-for-exchange-on-premises.md)

