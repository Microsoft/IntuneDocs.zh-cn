---
title: "选择如何注册移动设备 |Microsoft Intune"
description: "决定如何通过回答几个简单的问题在 Intune 中注册移动设备"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 178df739-d3b9-43cb-8440-c5c110b1276b
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: b5cc645ea50e6c4bb521e04371037c3978c9426a


---

# <a name="choose-how-to-enroll-mobile-devices"></a>选择如何注册移动设备

移动设备注册是通过 Microsoft Intune 将智能手机、平板电脑和 PC 带入管理的过程。 作为管理员，你需要确定如何基于以下信息以最佳方式注册设备：

 -  所有权（个人与 公司拥有）
 -  使用情况（共享与 个人）
 -  平台（iOS、Android、Windows Phone、Windows PC、Mac PC）

你对以下问题的回答将帮助确定你管理的设备的最佳注册方法。

## <a name="do-employees-bring-their-own-devices-or-are-devices-provided-by-your-organization"></a>**员工自带设备办公还是由组织为他们提供？**

  - **用户拥有的设备** -“BYOD”（自带设备办公）注册 – 用户可以在其设备上安装 Intune 公司门户应用，然后注册它，从而获取对公司资源（如电子邮件、公司应用、公司数据和支持）的访问权限。  

  - **公司拥有的设备** - 可以多种方式注册公司拥有的设备 (COD)，具体取决于组织的需求和管理的设备的类型。

> [!div class="button"]
[BYOD 注册 >](#what-byod-devices-can-your-users-enroll)   [COD 注册 >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## <a name="what-byod-devices-can-your-users-enroll"></a>**用户可以注册哪些 BYOD 设备？**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS 和 Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 移动版和 Window Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [Windows 电脑](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## <a name="are-your-company-owned-devices-shared-or-do-they-have-dedicated-users"></a>**你的公司拥有的设备是共享的还是他们拥有专用用户？**

- **共享公司拥有的设备** - 这些设备没有单个用户，并且通常没有配置为可以访问电子邮件。 例如，网亭设备或面向任务的设备用户根据需要从池中抽取，然后返回。 建议的注册方法取决于设备的平台。

- **专用用户** - 分发给个人用户的公司拥有的设备需要作为公司资产对其进行跟踪，同时允许用户作为个人设备访问电子邮件和数据。 建议的注册方法取决于设备的平台。

> [!div class="button"]
[共享 >](#what-operating-system-are-your-shared-devices-running)   [专用 >](#how-will-you-manage-dedicated-ios-devices)


## <a name="what-operating-system-are-your-shared-devices-running"></a>**你的共享设备运行的是哪种操作系统？**

> [!div class="button"]
[Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## <a name="how-will-you-manage-shared-ios-devices"></a>**如何管理共享的 iOS 设备？**

- **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册

- **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。 如果你不希望恢复设备的出厂设置，则使用“直接”注册。

- **设备注册管理器** - Intune 的设备注册管理器 (DEM) 允许管理器或管理员使用单个用户帐户注册多个移动设备。 这些设备不能有用户相关性（即专用用户），并且必须通过安装和登录到公司门户应用来注册。

  > [!div class="button"]
  [iOS DEP 注册 >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 直接注册 >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [DEM 注册 >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

## <a name="how-will-you-manage-dedicated-ios-devices"></a>**如何管理专用 iOS 设备？**

你可以使用专用用户注册公司拥有的设备，方法如下：

- **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并向 Intune 进行注册。

- **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。

- **使用 IMEI 号码进行标记** - 通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 然后，用户可以通过安装公司门户将其设备注册为个人设备，以访问公司资源（如电子邮件、应用和数据）。

  > [!div class="button"]
  [具有 IMEI 标记 >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [iOS 设置助手](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [具有 IMEI 标记](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Nov16_HO4-->


