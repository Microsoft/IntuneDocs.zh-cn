---
title: "为托管 Exchange 配置 Microsoft Intune Exchange Connector | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# 为 Exchange Online 配置 Intune Service-to-Service Connector

利用以下信息连接由 Office 365 托管的 Microsoft Intune 和 Exchange Online 服务。

## Service-to-Service Connector 的要求
**Service to Service Connector** 仅支持托管 Exchange，对本地基础结构没有要求。

|要求|更多信息|
|---------------|--------------------|
|已配置并且正在运行托管 Exchange|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|移动设备管理机构| [将移动设备管理机构设置为 Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange 版本|你必须有包含 Exchange Server 2013 或更高版本租户的 Office 365 订阅。 只要租户是 Exchange Server 2013 或更高版本，Connector 就支持同一环境中的 Exchange Server 2010。|
|Active Directory 同步|你必须[设置 Active Directory 同步](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用 Intune Connector。|

### Exchange cmdlet 要求

你还必须创建 Intune Exchange Connector 使用的 Exchange Online 用户帐户。 该帐户必须有权使用 Intune 管理控制台并运行以下必需的 Windows PowerShell Exchange cmdlet：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## 设置 Service-to-Service Connector

1. 使用对[上述](#exchange-cmdlet-requirements) cmdlet 具有 Exchange 管理员权限的用户帐户打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)。 Microsoft Intune 会使用当前登录用户的电子邮件地址来设置连接。

2.  在工作区快捷方式窗格中，选择“管理”，然后转到“移动设备管理” > “Microsoft Exchange” > “设置 Exchange 连接”。
![“设置 Service To Service Connector”页](../media/intunesa5cservicetoserviceconnector.png)

3.  在“设置 Exchange 连接”页上，选择“设置服务间连接器”。


Service-to-Service Connector 将自动进行配置并与你的托管 Exchange 环境同步。

## 验证你的 Exchange 连接

成功地配置了 Exchange Connector 之后，请在 Intune 管理控制台中选择“管理”工作区，转到“移动设备管理” > “Microsoft Exchange”，并验证你提供的详细信息是否出现在“Exchange 连接信息”下。

你也可以检查最后一次成功同步尝试的时间和日期。



<!--HONumber=Jun16_HO4-->


