---
title: 适用于 Exchange Online 的 Intune Exchange 连接器
titleSuffix: ''
description: 将 Intune 连接到 Office 365 Exchange 服务以支持 Exchange ActiveSync 移动设备管理 (MDM)。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6be3694a18cd0df09b52b535a0fcd2050bf7a98
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231238"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>为 Intune 和 Exchange Online 配置 Exchange 服务连接器

本文介绍如何将 Microsoft Intune 服务连接到 Exchange Online 或新 Exchange Online Dedicated 服务。 若要确定 Exchange Online Dedicated 环境采用的是**新**版本还是**旧**版本，请与帐户管理员联系。

## <a name="service-to-service-connector-requirements"></a>服务间连接器的要求
Service to Service Connector 仅支持 Exchange Online 或 Exchange Online Dedicated，且对本地基础结构没有要求。


|              要求               |                                                                                                            更多信息                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 已配置且正在运行 Exchange Online |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   移动设备管理机构   |                                                       [将移动设备管理机构设置为 Microsoft Intune](mdm-authority-set.md)                                                       |
|       Microsoft Exchange 版本       |                                                                                      Exchange Online 或新 Exchange Online Dedicated 服务                                                                                      |
|    Active Directory 同步    | 你必须[设置 Active Directory 同步](/intune/users-add)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用 Intune Connector。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

还必须创建 Intune Exchange 服务连接器使用的 Exchange Online 用户帐户。 帐户必须具有运行以下要求的 Windows PowerShell Exchange cmdlets 的权限：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>设置服务间连接器

1. 使用对[上述](#exchange-cmdlet-requirements) cmdlet 具有 Exchange 管理员权限的用户帐户、有效的 Intune 许可证和全局管理员角色登录到 [Azure 门户](http://portal.azure.com)。 Microsoft Intune 会使用当前登录用户的电子邮件地址来设置连接。

2. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3. 选择“Intune”以打开 Microsoft Intune 仪表板。 选择“条件访问”，然后在“设置”下，选择“Exchange 服务连接器”。

4.  在“条件访问 - Exchange 服务连接器”页面，选择“安装 Service To Service Connector”。 
   
     ![显示选择安装 Service to Service Connector 链接的图像](media/exchange_service_connector.png)

服务间连接器将自动配置并与 Exchange Online 或新 Exchange Online Dedicated 环境同步。

## <a name="validate-your-exchange-connection"></a>验证你的 Exchange 连接

成功配置 Exchange Service to Service Connector 后，在“条件访问 - Exchange 服务连接器”页上验证 Exchange Connector Server 信息。

你也可以检查“连接状态”和最后一次成功同步尝试的时间和日期。

## <a name="next-steps"></a>后续步骤
[监视 Microsoft Intune 中的 Exchange 条件访问](conditional-access-exchange-monitor.md)