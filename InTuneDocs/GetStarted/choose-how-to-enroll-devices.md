---
title: "选择如何注册移动设备 |Microsoft Intune"
description: "决定如何通过回答几个简单的问题在 Intune 中注册移动设备"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 2c14071f5fb1a3604b897d6b2f81797d40bedc6d
ms.openlocfilehash: 1fd8495811e2cbcf4761707f2d1b705e49a240c6


---

# 选择如何注册移动设备

你对以下问题的回答可帮助确定所管理设备的最佳注册方法。

## **员工携带他们自己的设备还是由你的组织为他们提供？**

  - **用户拥有的设备** -“自带设备办公”(BYOD) 注册
  - **公司自有设备** - COD 注册

> [!div class="button"]
[BYOD 注册 >](#what-byod-devices-can-your-users-enroll)   
> [!div class="button"]
[COD 注册 >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

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

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以与注册配置文件相关联。 用户首次打开设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”选项。 如果不希望恢复设备的出厂设置，则使用“直接注册”选项。

  - **设备注册管理器 (Intune)** - Intune 的设备注册管理器 (DEM) 允许管理器或管理员使用单个用户帐户注册多个移动设备。 这些设备不能有专用用户（用户关联），并且必须通过安装和登录到公司门户应用来注册。

## **你将如何管理专用的 iOS 设备？**

  > [!div class="button"]
   [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 设置助理](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [使用 IMEI 进行标记](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  你可以使用专用用户注册公司拥有的设备，方法如下：

  - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以与注册配置文件相关联。 用户首次打开设备时，设备将下载 DEP 配置文件，并注册 Intune。

  - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”选项。

  - **使用 IMEI 号码进行标记** - 通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 然后，用户可以通过安装公司门户将其设备注册为个人设备，以访问公司资源（如电子邮件、应用和数据）。



<!--HONumber=Oct16_HO3-->


