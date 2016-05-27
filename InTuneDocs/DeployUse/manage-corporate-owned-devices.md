---
# required metadata

title: 使用 Microsoft Intune 管理公司所有的设备 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 在 Microsoft Intune 中注册公司所有的设备
可以使用多种方法对组织或公司所有的设备 (COD) 进行管理，具体取决于设备和设备的购买方式。

## 公司所有的 iOS 设备
这些注册方法非常适用于“选择你自己的设备”(CYOD) 的情况，即组织为用户购买设备，但想要保持对设备的管理。 如果组织已购买 iOS 设备，那么可以预配置注册，以便在用户第一次打开此设备时就可以对它进行管理。 针对[直接](ios-direct-enrollment-in-microsoft-intune.md)注册或[设置助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)注册，Intune 支持通过 [Apple 的设备注册计划 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 或者是使用 Mac 计算机上运行的 Apple Configurator 工具的注册。

[注册企业所有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## 设备注册管理器
组织可以在 Intune 中使用一个称为设备注册管理器帐户的用户帐户管理大量移动设备。 创建设备注册管理器帐户之后，管理员可使用此帐户为普通用户注册比默认情况下允许的五个标准设备更多的设备。 使用设备注册管理器注册设备仅适用于非特定用户使用的设备。 这些设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。

[使用设备注册管理器注册企业自有设备](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 使用国际移动设备标识 (IMEI) 指定公司所有的设备
唯一的国际移动设备标识 (IMEI) 号是许多移动设备制造商的通用设备属性。 Intune 管理员可以导入公司拥有的设备的 IMEI 号。 当设备由 Intune 管理后，可以将它标记为公司所有的设备并对它使用相应的策略。

[根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)


<!--HONumber=May16_HO2-->


