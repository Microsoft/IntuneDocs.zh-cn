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
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: c671610b9c56d8b92d126d9902cce9c8c689ed63
ms.openlocfilehash: aac4eee56ec7326b2ce466d19b580aa5f1388aea


---

# 选择如何注册移动设备

你对以下问题的回答将帮助确定你管理的设备的最佳注册方法。

## **员工携带他们自己的设备还是由你的组织为他们提供？**

  - **用户拥有的设备** -“自带设备办公”(BYOD) 注册
  - **公司自有设备** - COD 注册

> [!div class="button"]
[BYOD 注册 >](#what-byod-devices-can-your-users-enroll)   [COD 注册 >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **你的用户可以注册哪些 BYOD 设备？**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS 和 Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 移动版和 Window Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows 电脑](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **你的公司拥有的设备是共享的还是他们拥有专用用户？**

> [!div class="button"]
[共享 >](#what-operating-system-are-your-shared-devices-running)   [专用 >](#how-will-you-manage-dedicated-ios-devices)


## **你的共享设备运行的是哪种操作系统？**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **你将如何管理共享的 iOS 设备？**

  > [!div class="button"]
  [iOS DEP 注册 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 直接注册 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) [DEM 注册 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。 如果你不希望恢复设备的出厂设置，则使用“直接”注册。

  - **设备注册管理器** - Intune 的设备注册管理器 (DEM) 允许管理器或管理员使用单个用户帐户注册多个移动设备。 这些设备不能有用户相关性（即专用用户），并且必须通过安装和登录到公司门户应用来注册。

## **你将如何管理专用的 iOS 设备？**

  > [!div class="button"]
  [具有 IMEI 标记 >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 设置助手](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [具有 IMEI 标记](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  你可以使用专用用户注册公司拥有的设备，方法如下：

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并向 Intune 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。

  - **使用 IMEI 号码进行标记** - 通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 然后，用户可以通过安装公司门户将其设备注册为个人设备，以访问公司资源（如电子邮件、应用和数据）。



<!--HONumber=Aug16_HO1-->


