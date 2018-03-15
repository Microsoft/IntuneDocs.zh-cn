---
title: "选择如何在 Intune 中注册 iOS 设备"
titlesuffix: Microsoft Intune
description: "了解如何在 Microsoft Intune 中设置 iOS 设备注册。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e79122c1bea970525faaf443f9bf4271d050abe2
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
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
- 设置助理注册 - 将设备恢复出厂设置，准备好运行“设置助理”，从而为设备的新用户安装公司策略。
- 直接注册 - 不将设备恢复出厂设置，并使用预定义策略注册设备。 此方法适用于“无用户关联”的设备。

详细了解 [Apple Configurator 注册](apple-configurator-setup-assistant-enroll-ios.md)。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>在注册了 DEP 或 Apple 配置器的设备上使用公司门户

配置了用户关联的设备可以安装和运行公司门户应用，以下载应用和管理设备。 用户收到设备后，必须完成一些其他步骤，以便完成设置助理并安装公司门户应用。

需要关联用户才可支持以下内容：
  - 移动应用程序管理 (MAM) 应用
  - 对电子邮件和公司数据的条件性访问
  - 公司门户应用

**用户如何注册具有用户关联的公司所有的 iOS 设备**
1. 用户打开设备时，系统会提示其完成设置助理。 安装过程中，系统会提示用户输入其凭据。 用户必须使用与其在 Intune 中的订阅相关的凭据（即唯一的个人名称或 UPN）。

2. 安装过程中，系统会提示用户输入 Apple ID。 必须提供 Apple ID 才能允许设备安装公司门户。 设置完成后，他们还可以提供 iOS 设置菜单中的 ID。

3. 完成设置后，iOS 设备必须从应用商店安装公司门户应用。

4. 现在用户可以使用在设置设备时使用的 UPN 登录公司门户。

5. 登录后，系统会提示用户注册其设备。 第一步是识别其设备。 应用会提供一份已为公司注册并已被分配到用户的 Intune 帐户的 iOS 设备列表。 他们应选择匹配的设备。

  如果该设备还不是公司注册的设备，他们应选择“**新设备**”以使用标准注册流程继续操作。

6. 在下一个屏幕上，用户必须确认新设备的序列号。 用户可以点击“确认序列号”链接，以启动有关如何使用“设置”应用验证序列号的说明。 然后用户必须将序列号的最后 4 个字符输入到公司门户应用中。

  此步骤验证该设备是否是在 Intune 中注册的企业设备。 如果设备上的序列号不匹配，则选择了错误的设备。 用户需返回到上一屏幕并选择其他设备。

7. 验证序列号后，公司门户应用将重定向到公司门户网站以完成注册。 然后该网站会提示用户返回到应用。

8. 注册现已完成。 现在用户可以使用此设备的完整功能集。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>有关无用户关联的企业拥有的托管设备

配置为无用户关联的设备不支持公司门户，并且不应安装应用。 公司门户适用于具有企业凭据的用户，并且需要访问个性化企业资源（例如邮件）的权限。 注册为无用户关联的设备并不具有专用的用户登录。 展台、销售点 (POS) 或共享实用程序设备是注册为“无用户关联”的设备的典型用例。

如果需要用户关联，注册设备前请确保设备的注册配置文件选中“**用户关联**”。 若要更改设备的关联状态，必须停用并重新注册设备。

