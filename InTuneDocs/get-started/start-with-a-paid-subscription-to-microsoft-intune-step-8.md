---
title: "启用设备注册 | Microsoft Docs"
description: "设置 MDM 机构，并启用 iOS、Windows、Android 和 Mac 设备的注册。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4726cc621d65200211a5cef6f80c14b2c447b8a7
ms.openlocfilehash: 4fcf991ec2d982c945814ccc49ae3862dece52b3


---

# <a name="enroll-mobile-devices-and-install-an-app"></a>注册移动设备并安装应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要使用 Intune 设置移动设备管理，必须先设置“移动设备管理机构”，它标识可管理与你的帐户关联的设备的服务。 本指南假设你将使用 Intune 服务，而不是 System Center Configuration Manager。 设置 MDM 机构后，便可以启用对设备平台的管理，并使用公司门户应用注册设备。

## <a name="enable-device-enrollment"></a>启用设备注册

1. **将 Intune 设置为移动设备管理机构**
    在 [Intune 管理控制台](https://manage.microsoft.com/)中，选择“管理”**** > “移动设备管理”****，然后在“任务”****下选择“设置 MDM 机构”****。  

2. 在“MDM 机构”对话框中选择“是”。

    ![管理控制台。 设置 mdm 到 Intune](./media/mdmAuthority.png)

## <a name="choose-how-to-enroll-devices"></a>选择设备注册方式

Intune 可以根据你公司的需求以多种方式管理设备。 几种可用的注册方案包括：“自带设备”(BYOD)、公司拥有的设备、“选择自己的设备”(CYOD) 和 Kiosk 模式设备。

按照以下步骤操作，[选择设备注册方式](choose-how-to-enroll-devices1.md)。

## <a name="enable-mdm-for-your-device-platform"></a>为设备平台启用 MDM
必须为 iOS、Mac 和 Android for Work 设备启用注册，从而在平台提供程序与 Intune 租户之间建立关系。 Windows 和 Android 设备不需要其他步骤，但对于 Windows 设备，你可以通过创建一个特殊的 DNS 注册表项来简化用户的设备注册。

为要管理的设备平台启用设备注册。 根据你的平台，需要的要求不同：

-  [iOS 和 macOS](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
-  [Windows 电脑](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)
-  [Windows 10 移动版和 Windows Phone](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work)

启用注册后，用户可以将公司门户应用下载到其设备，并完成设备注册过程。

### <a name="enable-company-owned-device-enrollment"></a>启用公司拥有的设备注册
还可以启用多种[公司拥有的设备注册](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices)方案，包括：
- [Apple 设备注册计划](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator 设置助理注册](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator 设置助理注册](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [设备注册管理器](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的最后一步。 由于已完成初始配置，你可考虑启用附加的 MDM 功能。

>[!div class="step-by-step"]

>[&larr;**注册设备**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)[**配置后任务**&rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Jan17_HO3-->


