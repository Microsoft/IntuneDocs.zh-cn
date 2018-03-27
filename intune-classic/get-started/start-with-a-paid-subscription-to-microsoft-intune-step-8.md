---
title: 启用设备注册
description: 设置 MDM 机构，并启用 iOS、Windows、Android 和 Mac 设备的注册。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e9572181fb15ec97e7ae4c11a8ab2e4fe4cc9b30
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="enable-enrollment-for-mobile-devices"></a>启用移动设备注册

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题指导 Intune 管理员如何启用移动设备注册。 有关在手机上使用 Intune 的帮助，请参阅[使用托管设备来完成工作](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions)。

若要使用 Intune 设置移动设备管理，必须先设置“移动设备管理机构”，它标识可管理与你的帐户关联的设备的服务。 本指南假设你将使用 Intune 服务，而不是 System Center Configuration Manager。 设置 MDM 机构后，便可以启用对设备平台的管理，并使用公司门户应用注册设备。

## <a name="enable-device-enrollment"></a>启用设备注册

1. **将 Intune 设置为移动设备管理机构** 在[“Intune 管理控制台”](https://manage.microsoft.com/)中，选择“管理”>“移动设备管理”，然后在“任务”下选择“设置 MDM 机构”。  

2. 在“MDM 机构”对话框中选择“是”。

    ![管理控制台。 设置 mdm 到 Intune](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>选择设备注册方式

Intune 可以根据你公司的需求以多种方式管理设备。 几种可用的注册方案包括：“自带设备”(BYOD)、公司拥有的设备、“选择自己的设备”(CYOD) 和 Kiosk 模式设备。

按照以下步骤操作，[选择设备注册方式](choose-how-to-enroll-devices1.md)。

## <a name="enable-mdm-for-your-device-platform"></a>为设备平台启用 MDM
必须为 iOS、Mac 和 Android for Work 设备启用注册，从而在平台提供程序与 Intune 租户之间建立关系。 Windows 和 Android 设备不需要其他步骤，但对于 Windows 设备，你可以通过创建一个特殊的 DNS 注册表项来简化用户的设备注册。

为要管理的设备平台启用设备注册。 根据你的平台，需要的要求不同：

- [iOS 和 macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 和 Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [Windows 电脑](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)（Intune 软件客户端）
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

启用注册后，用户可以将公司门户应用下载到其设备，并完成设备注册过程。

### <a name="enable-company-owned-device-enrollment"></a>启用公司拥有的设备注册
还可以启用多种[公司拥有的设备注册](/intune-classic/deploy-use/manage-corporate-owned-devices)方案，包括：
- [Apple 设备注册计划](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator 设置助理注册](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator 直接注册](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [设备注册管理器](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的最后一步。 由于已完成初始配置，你可考虑启用附加的 MDM 功能。

>[!div class="step-by-step"]
>[&larr;**注册设备**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)[**配置后任务**&rarr;](.\post-configuration-tasks.md)  
