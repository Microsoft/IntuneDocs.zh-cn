---
title: "选择在 Intune 中注册 Windows 设备的方式"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中设置 Windows 设备注册。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中注册 iOS 设备

Intune 启用了 iPad 和 iPhone 的移动设备管理 (MDM)，以允许用户访问公司电子邮件和应用。

作为 Intune 管理员，你可以启用 iOS 设备的注册。 可以允许用户注册个人拥有的设备，称为“自带设备”(BYOD) 注册。 还可以启用公司拥有设备的注册。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 注册的先决条件
在启用 iOS 设备之前，请完成以下步骤：
- [设置 Intune](setup-steps.md) - 这些步骤用于设置 Intune 基础结构。 具体而言，设备注册需要用户[设置 MDM 机构](mdm-authority-set.md)。
- [获取 Apple MDM 推送证书](apple-mdm-push-certificate-get.md) - Apple 需要证书才能启用 iOS 和 macOS 设备的管理。

在完成这些先决条件后，用户就可以安装公司门户应用来注册其个人的 iOS 设备，或者管理员可以设置企业自有的 iOS 设备管理。 管理员还可以分配[设备注册管理员](device-enrollment-manager-enroll.md)，这些管理员可以使用单个管理帐户注册多个设备。 Intune 支持以下公司自有的 iOS 设备注册方法：

## <a name="device-enrollment-program"></a>设备注册程序
组织可以通过 Apple 的设备注册计划 (DEP) 购买 iOS 设备。 DEP 允许用户通过“无线方式”部署注册配置文件以对设备进行管理。 详细了解[设备注册计划](device-enrollment-program-enroll-ios.md)。

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager 是适用于学校的设备购买和注册计划。 与 DEP 一样，用户可以部署一个配置文件以注册设备进行管理。 详细了解 [Apple School Manager](apple-school-manager-set-up-ios.md)。

## <a name="apple-configurator"></a>Apple Configurator
可以通过在 Mac 计算机上运行的 Apple Configurator 来注册 iOS 设备。 若要使设备准备就绪，请使用 USB 连接它们并安装注册配置文件。 可采用两种方法用 Apple Configurator 注册设备：
- 设置助理注册 - 将设备恢复出厂设置，准备好运行“设置助理”，从而为设备的新用户安装公司策略。
- 直接注册 - 不将设备恢复出厂设置，并使用预定义策略注册设备。 此方法适用于“无用户关联”的设备。

详细了解 [Apple Configurator 注册](apple-configurator-setup-assistant-enroll-ios.md)。
