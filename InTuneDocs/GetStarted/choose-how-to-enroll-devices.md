---
# required metadata

title: 选择如何注册移动设备 |Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 06/06/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: damionw
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 选择如何注册移动设备

移动设备注册是通过 Microsoft Intune 将智能手机、平板电脑和 PC 带入管理的过程。 作为管理员，你需要确定如何基于以下信息以最佳方式注册设备：

 -  所有权（个人与 公司拥有）
 -  使用情况（共享与 个人）
 -  平台（iOS、Android、Windows Phone、Windows PC、Mac PC）

你对以下问题的回答将帮助确定你管理的设备的最佳注册方法。

## 员工携带他们自己的设备还是由你的组织为他们提供？

  **用户拥有的设备** -“BYOD”（自带设备办公）注册 – 用户可以在其设备上安装 Intune 公司门户应用，然后注册它，从而获取对公司资源（如电子邮件、公司应用、公司数据和支持）的访问权限。  
  > [!div class="button"]   [BYOD 注册>](..deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

  **公司拥有的设备** - 可以多种方式注册公司拥有的设备 (COD)，具体取决于组织的需求和管理的设备的类型。 下一个问题...

## 共享你公司拥有的设备还是他们有单独的用户？

**共享公司拥有的设备** - 这些设备没有单个用户，并且通常没有配置为可以访问电子邮件。 例如，网亭设备或面向任务的设备用户根据需要从池中抽取，然后返回。 建议的注册方法取决于设备的平台。

  - **Windows 和 Android 设备** - *设备注册管理器*是可用于使用公司门户应用注册多个共享的设备的 Intune 帐户。
  > [!div class="button"]   [设备注册管理器>](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **iOS 设备** - 可以通过三种方式管理共享的 iOS 设备。  **你将如何注册共享的 iOS 设备？**

    - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并使用配置文件 DEP 进行注册
    > [!div class="button"]     [DEP 注册>](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)

    - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。 如果你不希望恢复设备的出厂设置，则使用“直接”注册。

    > [!div class="button"]     [设置助理注册>](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)或[直接注册>](../deploy-use/ios-direct-enrollment-in-microsoft-intune)

    - **以上都不是** - 如果你不能或不想使用 Apple 的 DEP 或 Apple Configurator 注册方法，则使用 Intune 的设备注册管理器。
    > [!div class="button"]     [DEM 注册>](../deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

**单个用户** - 颁发给单个用户的公司拥有的设备需要作为公司资产进行跟踪，同时允许用户作为个人设备访问电子邮件和数据。 建议的注册方法取决于设备的平台。

  - **Windows 和 Android 设备** - 通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 然后，用户可以通过安装公司门户将其设备注册为个人设备，以访问公司资源（如电子邮件、应用和数据）。
  > [!div class="button"]   [标记 IMEI>](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  - **iOS 设备** - 可以通过三种方式管理共享的 iOS 设备。  **你将如何注册共享的 iOS 设备？**

    - **Apple 的设备注册计划 (DEP)** - 通过 DEP 购买或管理的 iOS 设备可以面向注册配置文件。 当用户第一次开启他们的设备时，设备将下载 DEP 配置文件，并根据配置文件进行注册。
    > [!div class="button"]     [DEP 注册>](../deploy-use/ios-device-enrollment-program-in-microsoft-intune)。

    - **Mac 上的 Apple Configurator** - Apple Configurator 是在 Mac PC 上运行的 Apple 应用程序。 你可以使用 USB 电缆将 iOS 设备连接到 Mac 以在设备上安装注册配置文件。 如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。

    如果你不希望恢复设备的出厂设置，则使用“直接”注册。
    如果你愿意恢复设备的出厂设置对它们进行注册，请使用“设置助理”注册。
    > [!div class="button"][iOS 设置助理注册](../deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [!div class="button"][iOS 直接注册](../deploy-use/ios-direct-enrollment-in-microsoft-intune)。

    - **以上都不是** - 如果你不能或不想使用 Apple 的 DEP 或 Apple Configurator 注册方法，则通过导入公司拥有的设备的国际移动设备标识 (IMEI) 号，你可以在 Intune 中将它们标记为公司拥有的设备。 然后，用户可以通过安装公司门户将其设备注册为个人设备，以访问公司资源（如电子邮件、应用和数据）。 > [!div class="button"][使用 IMEI 号码标记设备](../deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)


<!--HONumber=Jun16_HO1-->


