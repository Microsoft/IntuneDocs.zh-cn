---
title: "尝试在 Intune 中注册 iOS 设备时遇到错误 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 9da632e906a1486ac705a0af99179ce9669c8a24


---

# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>尝试在 Intune 中注册 iOS 设备时遇到错误

下表列出了在 Intune 中注册 iOS 设备时可能遇到的错误。 与 IT 管理员共享此链接。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

|错误消息|问题|需要 IT 管理员了解的内容|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|无注册策略|检查是否已设置所有注册必备组件（如 Apple Push Notification 服务 (APNs) 证书），并确保已启用“iOS 平台”。 有关说明，请参阅[设置 iOS 和 Mac 设备管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceCapReached|你已注册太多的移动设备。|注册其他移动设备前，用户必须从公司门户中删除当前已注册的移动设备之一。 请参阅你使用的设备类型的说明：[Android ](unenroll-your-device-from-intune-android.md)、[iOS](unenroll-your-device-from-intune-ios.md) 和 [Windows](unenroll-your-device-from-intune-windows.md)。|
|APNSCertificateNotValid|移动设备用于与公司网络通信的证书存在问题。<br /><br />请联系 IT 管理员，告知其你在尝试注册移动设备时收到消息 **APNSCertificateNotValid**，并请其查看此表中的解决办法。|Apple Push Notification 服务 (APNs) 提供与已注册 iOS 设备通信的通道。 如果未执行获取 APNs 证书的步骤，或者 APNs 证书已过期，则注册尝试将失败并将显示此消息。<br /><br />查看[同步 Active Directory 并将用户添加到 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中有关如何设置用户的信息。|
|AccountNotOnboarded|移动设备用于与公司网络通信的证书存在问题。<br /><br />请联系 IT 管理员，告知其你在尝试注册移动设备时收到消息 **APNSNotOnboarded**，并请其查看此表中的解决办法。|Apple Push Notification 服务 (APNs) 提供与已注册 iOS 设备通信的通道。 如果未执行获取 APNs 证书的步骤，或者 APNs 证书已过期，则注册尝试将失败并将显示此消息。<br /><br />有关详细信息，请查看[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|可能已尝试使用非 iOS 设备进行注册。 不支持你正在尝试注册的移动设备类型。<br /><br />请确保设备正在运行 iOS 版本 8.0 或更高版本。<br /><br />请联系 IT 管理员，告知其你在尝试注册移动设备时收到消息 **DeviceTypeNotSupported**，并请其查看此表中的解决办法。|请确保用户的设备正在运行 iOS 版本 8.0 或更高版本。|
|UserLicenseTypeInvalid|无法注册你的移动设备，因为你的用户帐户还不是所需用户组的成员。<br /><br />请联系 IT 管理员，告知其你在尝试注册移动设备时收到消息 **UserLicenseTypeInvalid**，并请其查看此表中的解决办法。|用户必须是相应用户组的成员才能注册其设备。 此消息表明用户持有的指定移动设备管理机构许可证类型不正确。 例如，如果已将 Intune 指定为移动设备管理机构，并且用户正在使用 System Center 2012 R2 Configuration Manager 许可证，则将收到此错误消息。<br /><br />有关详细信息，请查看以下内容：<br /><br />查看[同步 Active Directory 并将用户添加到 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中的[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)以及有关如何设置用户的信息。|
|MdmAuthorityNotDefined|IT 管理员要求设置公司移动设备的管理方式。<br /><br />请联系 IT 管理员，告知其你在尝试注册移动设备时收到消息 **MdmAuthorityNotDefined**，并请其查看此表中的解决办法。|尚未在 Intune 中指定移动设备管理机构。<br /><br />查看[开始使用 Microsoft Intune 的 30 天试用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中的“步骤 6：注册移动设备并安装应用”部分的第 1 项。|



<!--HONumber=Dec16_HO2-->


