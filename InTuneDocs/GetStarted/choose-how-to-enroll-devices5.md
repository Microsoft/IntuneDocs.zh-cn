---
title: "选择如何注册移动设备 |Microsoft Intune"
description: "决定如何通过回答几个简单的问题在 Intune 中注册移动设备"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: e1fe6b167b7d46f03472833bc1c3c19030f47bce
ms.openlocfilehash: 825392d060229a6b3f3bd3e84ad4be127118aa21


---
# 选择如何注册移动设备

你对这一系列问题的回答将帮助确定你管理的设备的最佳注册方法。


## **你将如何管理共享的 iOS 设备？**

  > [!div class="button"]
  [iOS DEP 注册 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 直接注册 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) [DEM 注册 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。 如果你不希望恢复设备的出厂设置，则使用“直接”注册。

  - **设备注册管理器** - Intune 的设备注册管理器 (DEM) 允许管理器或管理员使用单个用户帐户注册多个移动设备。 这些设备不能有用户相关性（即专用用户），并且必须通过安装和登录到公司门户应用来注册。

  > [!div class="button"]
  [< 上一步](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO2-->


