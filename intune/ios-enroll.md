---
title: 选择如何在 Intune 中注册 iOS 设备
titlesuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中设置 iOS 设备注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c92b1b660856fb52f6259514ad9075ab96fb2fc
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313286"
---
# <a name="enroll-ios-devices-in-intune"></a>在 Intune 中注册 iOS 设备

Intune 启用了 iPad 和 iPhone 的移动设备管理 (MDM)，以允许用户访问公司电子邮件和应用。

作为 Intune 管理员，你可以启用 iOS 设备的注册。 可以允许用户注册个人拥有的设备，称为“自带设备”(BYOD) 注册。 还可以启用公司拥有设备的注册。

## <a name="prerequisites-for-ios-enrollment"></a>iOS 注册的先决条件
在启用 iOS 设备之前，请完成以下步骤：
- [设置 Intune](setup-steps.md) - 这些步骤用于设置 Intune 基础结构。 具体而言，设备注册需要用户[设置 MDM 机构](mdm-authority-set.md)。
- [获取 Apple MDM 推送证书](apple-mdm-push-certificate-get.md) - Apple 需要证书才能启用 iOS 和 macOS 设备的管理。

## <a name="user-owned-ios-devices-byod"></a>用户拥有的 iOS 设备 (BYOD)

可以让用户注册其个人设备用于 Intune 管理，这称为“自带设备办公”或 BYOD。 完成先决条件并分配用户许可证后，用户便可从 App Store 下载 Intune 公司门户应用，然后按照应用中的注册说明进行操作。

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
- 设置助理注册 - 擦除设备，准备好运行设置助理，从而为设备的新用户安装公司策略。
- 直接注册 - 不擦除设备，并使用预定义策略注册设备。 此方法适用于“无用户关联”的设备。

详细了解 [Apple Configurator 注册](apple-configurator-setup-assistant-enroll-ios.md)。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>在注册了 DEP 或 Apple 配置器的设备上使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成一些其他步骤，以便完成设置助理并安装公司门户应用。

需要关联用户才可支持以下内容：
  - 移动应用程序管理 (MAM) 应用
  - 对电子邮件和公司数据的条件性访问
  - 公司门户应用

**用户如何注册具有用户关联的公司所有的 iOS 设备**
1. 用户打开设备时，系统会提示其完成设置助理。 
2. 安装完成后，系统会提示用户输入 Apple ID。 必须提供 Apple ID 才能允许设备安装公司门户。 
3. IOS 设备会自动从应用商店安装公司门户应用。
4. 用户应启动公司门户应用，并使用与其在 Intune 中的订阅关联的凭据（如唯一的个人名称或 UPN）登录。 
5. 登录后，即完成注册。 现在用户可以使用此设备的完整功能集。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>有关无用户关联的企业拥有的托管设备

配置为无用户关联的设备不支持公司门户，并且不应安装应用。 公司门户适用于具有企业凭据的用户，并且需要访问个性化企业资源（例如电子邮件）的权限。 注册为无用户关联的设备并不具有专用的用户登录。 展台、销售点 (POS) 或共享实用程序设备是注册为“无用户关联”的设备的典型用例。

如果需要用户关联，注册设备前请确保设备的注册配置文件选中“**用户关联**”。 若要更改设备的关联状态，必须停用并重新注册设备。

