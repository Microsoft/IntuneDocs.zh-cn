---
title: "选择在 Intune 中注册 Windows 设备的方式"
titlesuffix: Azure portal
description: "了解如何在 Microsoft Intune 中设置 Windows 设备注册。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1bcdaa30df09313d3eda96410b6b394f1a0029d3
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2018
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中注册 iOS 设备

Intune 启用了 iPad 和 iPhone 的移动设备管理 (MDM)，以允许用户访问公司电子邮件和应用。

作为 Intune 管理员，你可以启用 iOS 设备的注册。 可以允许用户注册个人拥有的设备，称为“自带设备”(BYOD) 注册。 还可以启用公司拥有设备的注册。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 注册的先决条件
在启用 iOS 设备之前，请完成以下步骤：
- [设置 Intune](setup-steps.md) - 这些步骤用于设置 Intune 基础结构。 具体而言，设备注册需要用户[设置 MDM 机构](mdm-authority-set.md)。
- [获取 Apple MDM 推送证书](apple-mdm-push-certificate-get.md) - Apple 需要证书才能启用 iOS 和 macOS 设备的管理。

## <a name="user-owned-ios-devices-byod"></a>用户拥有的 iOS 设备 (BYOD)

可以让用户注册其个人设备用于 Intune 管理，这称为“自带设备办公”或 BYOD。 完成先决条件并分配用户许可证后，用户便可从 App Store 下载适用于 iOS 的公司门户应用，然后按照应用中的注册说明进行操作。

## <a name="company-owned-ios-devices"></a>公司拥有的 iOS 设备
对于为用户购买设备的组织，Intune 还支持以下公司自有的 iOS 设备注册方法：

- Apple 设备注册计划 (DEP)
- Apple School Manager
- Apple Configurator 设置助理注册
- Apple Configurator 直接注册

还可使用[设备注册管理器](device-enrollment-manager-enroll.md)帐户注册公司自有的 iOS 设备。

## <a name="device-enrollment-program"></a>设备注册程序
组织可以通过 Apple 的设备注册计划 (DEP) 购买 iOS 设备。 DEP 允许用户通过“无线方式”部署注册配置文件以对设备进行管理。 详细了解[设备注册计划](device-enrollment-program-enroll-ios.md)。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager 是适用于学校的设备购买和注册计划。 与 DEP 一样，用户可以部署一个配置文件以注册设备进行管理。 详细了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator
可以通过在 Mac 计算机上运行的 Apple Configurator 来注册 iOS 设备。 若要使设备准备就绪，请使用 USB 连接它们并安装注册配置文件。 可采用两种方法用 Apple Configurator 注册设备：
- 设置助理注册 - 将设备恢复出厂设置，准备好运行“设置助理”，从而为设备的新用户安装公司策略。
- 直接注册 - 不将设备恢复出厂设置，并使用预定义策略注册设备。 此方法适用于“无用户关联”的设备。

详细了解 [Apple Configurator 注册](apple-configurator-setup-assistant-enroll-ios.md)。
