---
title: Exchange Connector for Exchange Online | Microsoft Docs
description: "将 Intune 连接到 Office 365 Exchange 服务以支持 Exchange ActiveSync 移动设备管理 (MDM)。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4b73767f585cfa6283c7fb0601e7061efe42c606
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>为 Exchange Online 配置 Intune 服务间连接器

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

此信息可用于连接 Microsoft Intune 和 Exchange Online 或新 Exchange Online Dedicated 服务。 若要确定 Exchange Online Dedicated 环境采用的是**新**版本还是**旧**版本，请与帐户管理员联系。 Intune 仅支持每个订阅中存在一个 Exchange Connector 连接（任意类型）。

## <a name="service-to-service-connector-requirements"></a>服务间连接器的要求
**服务间连接器**仅支持 Exchange Online 或 Exchange Online Dedicated，且对本地基础结构没有要求。

|要求|更多信息|
|---------------|--------------------|
|已配置且正在运行 Exchange Online|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|移动设备管理机构| [将移动设备管理机构设置为 Microsoft Intune](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Microsoft Exchange 版本|Exchange Online 或新 Exchange Online Dedicated 服务|
|Active Directory 同步|你必须[设置 Active Directory 同步](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)，以便将本地用户和安全组与 Azure Active Directory 的实例同步，然后才能使用 Intune Connector。|

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 要求

你还必须创建 Intune Exchange Connector 使用的 Exchange Online 用户帐户。 该帐户必须有权使用 Intune 管理控制台并运行以下必需的 Windows PowerShell Exchange cmdlet：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>设置服务间连接器

1. 使用对[上述](#exchange-cmdlet-requirements) cmdlet 具有 Exchange 管理员权限的用户帐户打开 [Microsoft Intune](https://manage.microsoft.com) 管理控制台。 Microsoft Intune 会使用当前登录用户的电子邮件地址来设置连接。

2.  在工作区快捷方式窗格中，选择“管理”>“移动设备管理” > “Microsoft Exchange” > “设置 Exchange 连接”。
![设置服务间连接器页面](../media/intunesa5cservicetoserviceconnector.png)

3.  在“设置 Exchange 连接”页上，选择“设置服务间连接器”。


服务间连接器将自动配置并与 Exchange Online 或新 Exchange Online Dedicated 环境同步。

## <a name="validate-your-exchange-connection"></a>验证你的 Exchange 连接

成功配置 Exchange Connector 后，请转到 [Microsoft Intune 管理控制台](https://manage.microsoft.com)。 选择“管理”> “移动设备管理” > “Microsoft Exchange”。 然后，验证你提交的详细信息是否显示在 **Exchange 连接信息**之下。

你也可以检查最后一次成功同步尝试的时间和日期。

