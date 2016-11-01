---
title: "注册设备 | Microsoft Intune"
description: "移动设备管理 (MDM) 使用注册将设备纳入管理并允许访问资源。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 92e40930c0ccbeb3d98bef43b115fd92f24beaef
ms.openlocfilehash: 136f91e26a367ab107a80673930e735c85008ac7


---

# 在 Intune 中注册设备以进行管理
可注册包括 Windows 电脑在内的设备，使用 Microsoft Intune 启用移动设备管理 (MDM)。 本主题介绍了在 Intune 管理中注册移动设备的不同方法。 注册设备的方式取决于设备类型、所有权和所需管理级别。 “自带设备办公”(BYOD) 注册允许用户注册其个人电话、平板电脑或电脑。 “企业拥有的设备” (COD) 注册允许用户为设备启用远程擦除、共享设备、或用户关联等管理方案。

若使用 [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune)（在本地或在云中承载），无需注册就可启用简单的 Intune 管理。 还可以使用 [Intune 客户端软件](#manage-windows-pcs-with-intune)管理 Windows 电脑。

## 设备注册方法概述

下表列出了 Intune 的注册方法及其支持的功能。 这些功能包括：
- **擦除** - 恢复设备出厂设置，删除所有数据。 有关详细信息，请参阅[停用设备](retire-devices-from-microsoft-intune-management.md)。
- **关联** - 将设备与用户关联。 对于移动应用程序管理 (MAM) 和公司数据的条件访问是必需的。 有关详细信息，请参阅[用户关联](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)。
- **锁定** - 阻止用户删除设备使其不受管理。 iOS 设备需要使用监管模式进行锁定。 有关详细信息，请参阅[远程锁定](retire-devices-from-microsoft-intune-management.md#block-access-a-device)。

**iOS 注册方法**

| **方法** |  **擦除** |  **相关性**    |   **锁定** | **详细信息** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [更多信息](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  | [更多信息](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   是 |   可选 |  可选|[更多信息](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| 是 |   可选 |  否| [更多信息](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| 否 |    否  | 否|[更多信息](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows 注册方法**

| **方法** |  **擦除** |  **相关性**    |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 是|   是 |   否 | [更多信息](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  |[更多信息](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android 注册方法**

| **方法** |  **擦除** |  **相关性**    |   **锁定** | **详细信息**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 否|    是 |   否 | [更多信息](prerequisites-for-enrollment.md#set-up-device-management)|
|**[DEM](#dem)**|   否 |否 |否  |[更多信息](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

若要了解有助于找到适当方法的一系列问题，请参阅[选择如何注册设备](/intune/get-started/choose-how-to-enroll-devices1)。

## BYOD
“自带设备办公”用户安装公司门户应用并注册其设备。 这让用户可连接到公司网络，并加入该域或 Azure Active Directory。 对于大多数平台，需要为许多 COD 方案启用 BYOD 注册。 有关详细信息，请参阅[设备注册的先决条件](prerequisites-for-enrollment.md)。 （[返回到表](#overview-of-device-enrollment-methods)）

## 企业持有设备
可以通过使用 Intune 控制台管理公司拥有的设备 (COD)。 可以直接通过 Apple 提供的工具注册 iOS 设备。 管理员或经理可以使用设备注册管理器注册所有设备类型。 具有 IMEI 号码的设备也可以标识并标记为公司拥有，以实现 COD 方案。

有关详细信息，请参阅[注册公司拥有的设备](manage-corporate-owned-devices.md)。

### DEM
设备注册管理员是一个特殊的 Intune 帐户，用于注册和管理多个公司拥有的设备。 管理员可安装公司门户并注册多个无用户设备。 了解有关 [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) 的详细信息。 （[返回到表](#overview-of-device-enrollment-methods)）

### DEP
通过 Apple 设备注册计划 (DEP) 管理，可“无线”创建策略并将其部署到通过 DEP 购买和管理的 iOS 设备。 用户第一次开启设备并运行 iOS 设置助理时，将注册设备。 此方法支持 **iOS 监督**模式，此模式又允许：
  - 锁定注册
  - 条件性访问
  - 越狱检测
  - 移动应用程序管理

了解有关 [DEP](ios-device-enrollment-program-in-microsoft-intune.md) 的详细信息。 （[返回到表](#overview-of-device-enrollment-methods)）

### USB-SA
使用 Intune 策略准备连接了 USB 的企业自有设备。 对于设置助理注册，管理员创建此 Intune 策略并将其导出到 Apple 配置器。 管理员必须手动注册每个设备。 用户收到其设备并运行设置助理，注册其设备。 此方法支持 **iOS 监督**模式，此模式又允许：
  - 条件性访问
  - 越狱检测
  - 移动应用程序管理

了解有关[使用 Apple Configurator 设置助理注册](ios-setup-assistant-enrollment-in-microsoft-intune.md)的详细信息。 （[返回到表](#overview-of-device-enrollment-methods)）

### USB-Direct
对于直接注册，管理员创建 Intune 策略并将其导出到 Apple 配置器。 连接了 USB 的公司拥有的设备可直接进行注册，无需恢复出厂设置。 管理员必须手动注册每个设备。 这些设备作为无用户设备进行管理。 它们未锁定、不受监控，且无法支持条件性访问、越狱检测或移动应用管理。 了解有关[使用 Apple Configurator 直接注册](ios-direct-enrollment-in-microsoft-intune.md)的详细信息。 （[返回到表](#overview-of-device-enrollment-methods)）

## 使用 Exchange ActiveSync 和 Intune 管理移动设备
可以使用 EAS MDM 策略，通过 Intune 管理未注册、但连接到 Exchange ActiveSync (EAS) 的移动设备。 Intune 使用 Exchange Connector 与 EAS 在本地或云托管环境中进行通信。

有关详细信息，请参阅[使用 Exchange ActiveSync 和 Intune 管理移动设备](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)。


## 使用 Intune 管理 Windows 电脑  
还可以使用 Microsoft Intune 管理使用 Intune 客户端软件的 Windows 电脑。 使用 Intune 客户端管理的电脑可以：

 - 报告软件和硬件清单
 - 安装桌面应用程序（例如 .exe 和 .msi 文件）
 - 防火墙设置

使用 Intune 客户端软件管理的电脑不能完全擦除，但可以选择性擦除。 使用 Intune 软件客户端管理的电脑不能利用许多 Intune 管理功能，如条件访问、VPN 和 Wi-Fi 设置或证书和电子邮件配置的部署。

有关详细信息，请参阅[使用 Intune 管理 Windows 电脑](manage-windows-pcs-with-microsoft-intune.md)。

## 支持的设备平台

Intune 可以管理以下设备平台：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## 后续步骤
- [设备注册的先决条件](prerequisites-for-enrollment.md)
- [管理企业自有设备](manage-corporate-owned-devices.md)
- [支持的移动设备和计算机](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Oct16_HO3-->


