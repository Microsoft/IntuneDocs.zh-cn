---
title: "管理公司拥有的设备 | Microsoft Intune"
description: "使用多种方法对公司自有设备 (COD) 进行管理，具体取决于设备、设备购买的方式以及组织的需要。"
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26ac7d52c0ad3e37e517b60d448a94849c0f4b30
ms.openlocfilehash: 6cf620a96b39540c8b7ca618936af1367971bb8f


---

# 在 Microsoft Intune 中注册公司所有的设备
通过 Intune，可采用多种方法来管理组织或公司拥有的设备 (COD)，这具体取决于设备、其购买方式及组织需求。

## 公司所有的 iOS 设备
这些注册方法非常适用于“选择你自己的设备”(CYOD) 的情况，即组织为用户购买设备，但想要保持对设备的管理。 如果组织已购买 iOS 设备，那么可以预配置注册，以便在用户第一次打开此设备时就可以对它进行管理。 针对[直接](ios-direct-enrollment-in-microsoft-intune.md)注册或[设置助理](ios-setup-assistant-enrollment-in-microsoft-intune.md)注册，Intune 支持通过 [Apple 的设备注册计划 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 或者是使用 Mac 计算机上运行的 Apple Configurator 工具的注册。

[注册企业所有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## 设备注册管理器
组织可以在 Intune 中使用一个称为设备注册管理器帐户的用户帐户管理大量移动设备。 创建设备注册管理器帐户之后，管理员可使用此帐户为普通用户注册比默认情况下允许的五个标准设备更多的设备。 使用设备注册管理器注册设备仅适用于非特定用户使用的设备。 这些设备非常适用于销售点或实用工具应用，但是不适用于需要访问电子邮件或公司资源的用户。

[使用设备注册管理器注册企业自有设备](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## 注册公司自有的 Windows 10 桌面

如果你的组织拥有 Azure Active Directory Premium (AADP) 或企业管理套件 (EMS)，你可以[注册 Windows 10 企业版](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)，当用户添加他们的工作或学校帐户时，它们将被自动标记为“公司自有”。

## 将设备标识为“公司自有”

公司自有设备在设备列表的“**所有权**”下，以“**公司**”列出。 设备可以通过以下方式被标识为“公司自有”：

 - [使用设备注册管理器 (DEM) 注册](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - 使用 Apple 的[设备注册程序 (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) 或 [Apple 配置器](ios-setup-assistant-enrollment-in-microsoft-intune.md)注册。
 - [使用 IMEI 号预先说明设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Windows 10 设备的 Azure Active Directory/企业管理套件注册](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### 国际移动设备标识 (IMEI)

唯一的国际移动设备标识 (IMEI) 号是许多移动设备制造商的通用设备属性。 Intune 管理员可以导入公司拥有的设备的 IMEI 号。 当设备变为由 Intune 管理后，该设备被标记为公司自有设备。

[根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jul16_HO3-->


