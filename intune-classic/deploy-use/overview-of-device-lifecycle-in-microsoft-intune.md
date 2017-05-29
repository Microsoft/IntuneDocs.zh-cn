---
title: "MDM 生命周期概述 | Microsoft Docs"
description: "了解 Intune 如何帮助你管理设备的整个生命周期（从注册到配置再到最终停用）。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3311ba5081c4b04d72fdeb1f9a558ffc2e1b02fc
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="overview-of-the-mobile-device-management-mdm-lifecycle"></a>移动设备管理 (MDM) 生命周期概述

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

你管理的所有设备都有一个*生命周期*。 Intune 可以帮助你管理此生命周期（从注册到配置和保护，再到不再需要时停用设备）：

![设备生命周期](./media/device-lifecycle.png "Intune 设备生命周期")

## <a name="enroll"></a>注册
当今的移动设备管理 (MDM) 策略适用于各种手机、平板电脑和电脑（iOS、Android、Windows 和 Mac OS X）。 如果你需要能够管理设备（这对公司拥有的设备来说很常见），第一步便是[设置设备注册](enroll-devices-in-microsoft-intune.md)。 你还可以通过向 Intune (MDM) 注册设备或[安装 Intune 客户端软件](manage-windows-pcs-with-microsoft-intune.md)来管理 Windows 电脑。

## <a name="configure"></a>用户密码重置策略
将你的设备注册只是第一步。 若要充分利用所有这些 Intune 功能并确保你的设备安全且符合公司标准，你可以从各种策略中选择。 这些策略让你能够几乎配置受管理设备运作方式的方方面面。 例如，对于含有公司数据的设备，用户是否应该有密码？ 你可以要求获得密码。 你有公司 Wi-Fi 吗？ 你可以自动配置它。 以下是可用的配置选项类型：

- [**配置策略**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。 这些策略让你能够配置所管理设备的特性和功能。 例如，你可以要求在 Windows Phone 上使用密码，或禁用 iPhone 的照相机。
- [**公司资源访问策略**](enable-access-to-company-resources-with-microsoft-intune.md)。 当你让用户在他们的个人设备上访问他们的工作时，这会给你带来难题。 例如，你怎么确保所有需要访问公司电子邮件的设备是正确配置的呢？ 如何确保用户可以使用 VPN 连接访问公司网络而不用了解很复杂的设置？ Intune 可以自动配置你管理的设备来访问公共公司资源，从而减少这种负担。
- [**Windows 电脑管理策略（使用 Intune 客户端软件）**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。 向 Intune 注册 Windows 电脑会带给你最多的设备管理功能，Intune 将继续支持使用 Intune 客户端软件管理 Windows 电脑。 如果你需要有关可使用电脑执行的一些任务的信息，请从这里开始。

## <a name="protect"></a>保护
在现代 IT 世界中，保护设备免受未经授权的访问是你要执行的最重要的任务之一。 除了设备生命周期的**配置**步骤中的项之外，Intune 还提供以下功能来帮助保护你管理的设备免受未经授权的访问或恶意攻击：
- [**Multi-Factor Authentication**](protect-your-devices-with-microsoft-intune.md)。 对用户登录添加一层额外的身份验证可以帮助增强设备安全性。 很多设备支持多重身份验证，这要求提供第二重身份验证（如电话呼叫或短信），用户才能获得访问权限。
- [**Microsoft Passport 设置**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)。 Microsoft Passport 是一种备用登录方法，可让用户使用*手势*（如指纹或 Windows Hello）而无需密码进行登录。
- [**保护 Windows 电脑的策略（使用 Intune 客户端软件）**](policies-to-protect-windows-pcs-in-microsoft-intune.md)。 当你使用 Intune 客户端软件管理 Windows 电脑时，可以使用允许你在所管理的电脑上控制 Endpoint Protection、软件更新和 Windows 防火墙的设置的策略。

## <a name="retire"></a>停用
当设备丢失或被盗、需要更换，或当用户移到另一个位置时，通常需要[停用或擦除](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)设备。 有多种方法可以完成此操作，包括重置设备、从管理将其删除以及擦除其上的公司数据。

