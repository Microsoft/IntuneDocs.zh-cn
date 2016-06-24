---
# required metadata

title: 管理公司拥有的设备 | Microsoft Intune
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
通过 Intune，可采用多种方法来管理组织或公司拥有的设备 (COD)，这具体取决于设备、其购买方式及组织需求。

## 公司所有的 iOS 设备
这些注册方法非常适用于“选择你自己的设备”(CYOD) 的情况，即组织为用户购买设备，但想要保持对设备的管理。 如果组织已购买 iOS 设备，那么可以预配置注册，以便在用户第一次打开此设备时就可以对它进行管理。 针对[直接](ios-direct-enrollment-in-microsoft-intune.md)注册或[设置助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)注册，Intune 支持通过 [Apple 的设备注册计划 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 或者是使用 Mac 计算机上运行的 Apple Configurator 工具的注册。

[注册企业所有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## 设备注册管理器
组织可以在 Intune 中使用一个称为设备注册管理器帐户的用户帐户管理大量移动设备。 创建设备注册管理器帐户之后，管理员可使用此帐户为普通用户注册比默认情况下允许的五个标准设备更多的设备。 使用设备注册管理器注册设备仅适用于非特定用户使用的设备。 这些设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。

[使用设备注册管理器注册企业自有设备](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 国际移动设备标识 (IMEI)
唯一的国际移动设备标识 (IMEI) 号是许多移动设备制造商的通用设备属性。 Intune 管理员可以导入公司拥有的设备的 IMEI 号。 当设备由 Intune 管理后，可以将它标记为公司所有的设备并对它使用相应的策略。

[根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## 公司拥有的设备注册方法概述

下表显示了公司拥有的设备的注册方法及其优势。

**iOS 注册方法**

| **方法** |  **[重置](#Reset)** |   **[相关性](#Affinity)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |
|**[DEP](#DEP)**|   是 |   选择 |   选择|
|**[USB-SA](#USB-SA)**| 是 |   选择 |   否|
|**[USB-Direct](#USB-Direct)**| 否 |    否  | 否|

**Windows 和 Android 的注册方法**

| **方法** |  **[擦除](#Wipe)** | **[User](#User)**   |   **[Locked](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | 否|    是 |   否 |
|**[DEM](#DEM)**|   否 |否 |否  |

**公司拥有的设备的注册方法**

### BYOD
“自带设备办公。” 用户安装公司门户应用并注册其设备。 通过公司门户注册设备将会使其加入工作区。 通过公司门户注册 iOS 设备需要 Apple ID。 对于公司拥有的设备，BYOD 无需其他配置。 参阅[设置设备管理](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md)的相关步骤。 （[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### DEM
设备注册管理器。 管理员创建 DEM 帐户。 然后，管理人员可安装公司门户并注册多个无用户设备。 了解有关 [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) 的详细信息。 （[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### DEP
Apple 设备注册计划。 管理员创建“无限升级”策略并将其部署到使用 DEP 购买和管理的 iOS 设备。 用户运行 iOS 设置助理时，就会对设备进行注册。 此方法支持**iOS 监督**模式，此模式转而又可：
  - 锁定注册
  - 条件性访问
  - 越狱检测
  - 移动应用程序管理

了解有关 [DEP](ios-device-enrollment-program-in-microsoft-intune.md) 的详细信息。 （[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### USB-SA
USB 连接、设置助理注册。 管理员创建 Intune 策略并将其导出到 Apple Configurator。 使用 Intune 策略准备连接了 USB 的设备。 管理员必须手动注册每个设备。 用户收到其设备并运行设置助理，注册其设备。 此方法支持**iOS 监督**模式，此模式转而又可：
  - 条件性访问
  - 越狱检测
  - 移动应用程序管理

了解有关[使用 Apple Configurator 设置助理注册](ios-setup-assistant-enrollment-in-microsoft-intune.md)的详细信息。 （[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### USB-Direct
直接注册。 管理员创建 Intune 策略并将其导出到 Apple Configurator。 连接了 USB 的设备可直接进行注册，无需恢复出厂设置。 管理员必须手动注册每个设备。 这些设备作为无用户设备进行管理。 它们未锁定、不受监控，且无法支持条件性访问、越狱检测和移动应用程序管理。 了解有关[使用 Apple Configurator 直接注册](ios-direct-enrollment-in-microsoft-intune.md)的详细信息。 （[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

**公司拥有的移动设备的行为**

### 重置
指定是否需要将设备恢复出厂设置才可注册设备，该操作将删除设备中的所有数据，并将设备退回到原始状态。
（[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### 相关性
指定注册方法是否支持“用户关联”，该关联可将设备与特定用户相连接。 无论是否关联了用户，都可注册“选择”设备。 需要关联用户才可支持以下内容：
  - 移动应用程序管理 (MAM) 应用
  - 对电子邮件和公司数据的条件性访问
  - 公司门户应用

（[返回到表](#overview-of corporate-owned-device-enrollment-methods)）

### 锁定
指定是否可锁定设备以防止用户删除 Intune 策略，进而使得设备不受管理。 对于 iOS 设备，其需要处于监管模式才可进行锁定。
（[返回到表](#overview-of corporate-owned-device-enrollment-methods)）（[返回到表](#overview-of corporate-owned-device-enrollment-methods)）


<!--HONumber=Jun16_HO3-->


