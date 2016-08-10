---
title: Exchange Connector for Exchange Online | Microsoft Intune
description: "将 Intune 连接到 Office 365 Exchange 服务以支持 Exchange ActiveSync 移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd


---

# 为 Exchange Online 配置 Intune Service-to-Service Connector

利用以下信息连接 Microsoft Intune 和 Exchange Online 或新 Exchange Online Dedicated 服务。 若要确定 Exchange Online Dedicated 环境采用的是**新**配置还是**旧**配置，请与帐户管理员联系。 Intune 仅支持每个订阅中存在一个 Exchange Connector 连接（任意类型）。

## Service-to-Service Connector 的要求
**Service to Service Connector** 仅支持 Exchange Online 或新 Exchange Online Dedicated，且对本地基础结构没有要求。

|要求|更多信息|
|---------------|--------------------|
|已配置且正在运行 Exchange Online|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|移动设备管理机构| [将移动设备管理机构设置为 Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange 版本|Exchange Online 或新 Exchange Online Dedicated 服务|
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


Service-to-Service Connector 将自动配置并与 Exchange Online 或新 Exchange Online Dedicated 环境同步。

## 验证你的 Exchange 连接

成功地配置了 Exchange Connector 之后，请在“[Microsoft Intune 管理控制台](http://manage.microsoft.com)”中选择“**管理**”，转到“**移动设备管理**” > “**Microsoft Exchange**”，并验证你提供的详细信息是否出现在“**Exchange 连接信息**”下。

你也可以检查最后一次成功同步尝试的时间和日期。



<!--HONumber=Jul16_HO5-->


