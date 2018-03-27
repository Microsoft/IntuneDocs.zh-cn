---
title: 选择如何注册移动设备
description: 决定如何通过回答几个简单的问题在 Intune 中注册移动设备
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/27/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.openlocfilehash: fd09126b8226828ccb60f30e0daa6135643303e2
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="choose-how-to-enroll-mobile-devices"></a>选择如何注册移动设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

你对这一系列问题的回答将帮助确定你管理的设备的最佳注册方法。

## <a name="how-will-you-manage-dedicated-corporate-owned-devices"></a>**如何管理企业所拥有的专用设备？**

  > [!div class="button"]
[iOS DEP >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)  
> [!div class="button"]
[iOS 设置助理 >](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
> [!div class="button"]
[IMEI 标记>](/intune-classic/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  你可以使用专用用户注册公司拥有的设备，方法如下：

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并向 Intune 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。

  - **使用 IMEI 号码进行标记** - 通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 这是将专用（“单一用户”）Windows 和 Android 设备标识为由公司所有的唯一方法。 对于无法使用 Apple 设备注册程序或 Apple 配置器进行注册的 iOS 设备，也可使用 IMEI 号码进行标记。 预先声明设备以将其标记为“企业”后，可以将设备分配给用户。 然后，用户可以通过安装公司门户将其设备注册为专用设备，以访问公司资源（如电子邮件、应用和数据）。

> [!div class="button"]
[< 返回](choose-how-to-enroll-devices3.md)
