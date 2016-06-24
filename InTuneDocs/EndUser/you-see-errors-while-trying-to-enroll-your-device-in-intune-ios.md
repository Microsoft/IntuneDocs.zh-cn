---
# required metadata

title: 尝试在 Intune 中注册 iOS 设备时遇到错误| Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer: esmich
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 尝试在 Intune 中注册 iOS 设备时遇到错误

下表列出了在 Intune 中注册 iOS 设备时可能遇到的错误。 与你的 IT 管理员分享此链接。 有关他们的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

|错误消息|问题|需要你的 IT 管理员了解的内容|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|DeviceCapReached|你已注册太多的移动设备。|注册其他移动设备前，用户必须从公司门户中删除当前已注册的移动设备之一。 请参阅你使用的设备类型的说明：[Android](unenroll-your-device-from-intune-android.md)、[iOS](unenroll-your-device-from-intune-ios) 和 [Windows](unenroll-your-device-from-intune-windows)。|
|APNSCertificateNotValid|允许移动设备与公司网络通信的证书存在问题。<br /><br />请联系你的 IT 管理员，告知其你在尝试注册移动设备时收到消息 **APNSCertificateNotValid**，并请其查看此表中的解决办法。|Apple 推送通知服务 (APNS) 提供通道以与注册的 iOS 设备联系。 如果未执行用于获取 APNS 证书的步骤，或者 APNS 证书已过期，则注册尝试将会失败并且会出现此消息。<br /><br />查看[同步 Active Directory 并将用户添加到 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中有关设置用户的信息。|
|AccountNotOnboarded|允许移动设备与公司网络通信的证书存在问题。<br /><br />请联系你的 IT 管理员，告知其你在尝试注册移动设备时收到消息 **APNSNotOnboarded**，并请其查看此表中的解决办法。|Apple 推送通知服务 (APNS) 提供通道以与注册的 iOS 设备联系。 如果未执行用于获取 APNS 证书的步骤，或者 APNS 证书已过期，则注册尝试将会失败并且会出现此消息。<br /><br />有关详细信息，请查看[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deployuse/set-up-ios-and-mac-management-with-microsoft-intune)。|
|DeviceTypeNotSupported|你可能已尝试使用非 iOS 设备进行注册。 不支持你正在尝试注册的移动设备类型。<br /><br />请确保设备正在运行 iOS 版本 7.1 或更高版本。<br /><br />请联系你的 IT 管理员，告知其你在尝试注册移动设备时收到消息 **DeviceTypeNotSupported**，并请其查看此表中的解决办法。|请确保用户的设备正在运行 iOS 版本 7.1 或更高版本。|
|UserLicenseTypeInvalid|无法注册你的移动设备，因为你的用户帐户还不是所需用户组的成员。<br /><br />请联系你的 IT 管理员，告知其你在尝试注册移动设备时收到消息 **UserLicenseTypeInvalid**，并请其查看此表中的解决办法。|用户必须是正确的用户组成员才能注册其设备。 此消息表明用户持有的指定移动设备管理机构许可证类型不正确。 例如，如果已将 Intune 指定为移动设备管理机构，并且用户正在使用 System Center 2012 R2 Configuration Manager 许可证，则将收到此错误消息。<br /><br />有关详细信息，请查看以下内容：<br /><br />查看 [同步 Active Directory 并将用户添加到 Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) 和[组织用户和设备](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5)中的[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)和有关设置用户的信息。|
|MdmAuthorityNotDefined|IT 管理员需要配置你公司的移动设备的管理方式。<br /><br />请联系你的 IT 管理员，告知其你在尝试注册移动设备时收到消息 **MdmAuthorityNotDefined**，并请其查看此表中的解决办法。|尚未在 Intune 中指定移动设备管理机构。<br /><br />查看[开始使用 Microsoft Intune 的 30 天试用版](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中的“步骤 6：注册移动设备并安装应用”部分的第 1 项。|

### 另请参阅
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)

<!--HONumber=Jun16_HO2-->


