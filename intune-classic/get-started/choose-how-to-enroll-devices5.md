---
title: "选择如何注册移动设备 |Microsoft Docs"
description: "决定如何通过回答几个简单的问题在 Intune 中注册移动设备"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 64f8a051cfa873df034e3d260862181ce637948c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---
# <a name="choose-how-to-enroll-mobile-devices"></a>选择如何注册移动设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

你对这一系列问题的回答将帮助确定你管理的设备的最佳注册方法。

## <a name="how-will-you-manage-shared-ios-devices"></a>**如何管理共享的 iOS 设备？**

> [!div class="button"]
[iOS DEP 注册 >]/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [!div class="button"]
> [iOS 直接注册 >]/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune) [!div class="button"]
[DEM 注册 >]/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。 如果你不希望恢复设备的出厂设置，则使用“直接”注册。

  - **设备注册管理器** - Intune 的设备注册管理器 (DEM) 允许管理器或管理员使用单个用户帐户注册多个移动设备。 这些设备不能有用户相关性（即专用用户），并且必须通过安装和登录到公司门户应用来注册。

> [!div class="button"]
[< 返回](choose-how-to-enroll-devices3.md)

