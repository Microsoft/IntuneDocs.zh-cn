---
title: "选择如何在 Intune 中注册 iOS 设备"
titleSuffix: Intune on Azure
description: "了解如何在 Microsoft Intune 中设置 iOS 设备注册。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>选择 iOS 和 macOS 设备的注册方式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题介绍了 IT 管理员可用于在 Intune 中启用 iOS 设备注册的方法。

使用以下信息确定哪些要用于注册 iOS 设备的方法。 除 BYOD 方法外，以下所有方法都用于注册公司拥有的设备。

**先决条件：**需要 [Apple 推送通知服务证书](apple-mdm-push-certificate-get.md)。

## <a name="user-owned-ios-devices-byod"></a>用户拥有的 iOS 设备 (BYOD)

如果用户要注册其个人、BYOD（自带办公设备）设备，他们可以从应用商店下载适用于 iOS 的公司门户应用，然后按照应用中的注册说明进行操作。 注册后，用户可连接到公司网络、加入域或 Azure Active Directory，并有权访问公司资源。 若要启用 BYOD，仅需要提供 [Apple 推送通知服务证书](apple-mdm-push-certificate-get.md)即可。 还可以阻止个人拥有的 iOS 设备的注册。 请参阅 [Set device type restrictions](enrollment-restrictions-set.md)（设置设备类型限制）了解相关说明。

## <a name="user-owned-macos-devices-byod"></a>用户拥有的 macOS 设备 (BYOD)

你可以启用 macOS 设备注册。 若要启用 macOS 注册，仅需要提供 [Apple 推送通知服务证书](apple-mdm-push-certificate-get.md)即可。 有关详细信息，请参阅[注册 macOS 设备](./macos-enroll.md)

## <a name="enrollment-program-with-apple"></a>Apple 的注册计划
Apple 提供了包括设备注册和管理基础结构的设备购买计划。 通过任一这些计划购买的设备可通过分配用于 Intune 管理的设备序列号以“无线”方式进行批量注册。

- **设备注册计划 (DEM)** - 适用于组织和企业的 Apple 的设备注册计划。 有关详细信息，请参阅[使用设备注册计划注册 iOS 设备](device-enrollment-program-enroll-ios.md)。
- **Apple School Manager** - 适用于学校的 Apple 的设备注册计划。 有关详细信息，请参阅[通过 Apple School Manager 进行 iOS 设备注册](apple-school-manager-set-up-ios.md)

## <a name="apple-configurator"></a>Apple Configurator

可通过导出公司注册配置文件，然后将那些移动设备连接到运行 Apple 配置器的 Mac 来注册 iOS 设备。 Apple 配置器支持两种形式的注册：

- “**设置助理注册**”：将设备重置为出厂设置，使其准备好由设备的新用户进行设置。 此方法要求管理员通过 USB 将 iOS 设备连接到运行 Apple Configurator 的 Mac 计算机以预配置注册。 然后，将设备提供给设备首次启用时运行设置助理的用户。 此过程使用用户的工作或学校凭据配置该设备，并完成注册过程。 有关详细信息，请参阅[使用 Apple Configurator 和设置助理注册 iOS 设备](apple-configurator-setup-assistant-enroll-ios.md)。

- **直接注册**：在设备准备过程中创建 Apple Configurator 兼容文件以供使用。 已注册设备没有进行出厂重置，且没有用户隶属关系。 若要注册设备，需要管理员通过 USB 将 iOS 设备连接到运行 Apple Configurator 的 Mac 计算机。 有关详细信息，请参阅[使用 Apple Configurator 直接注册注册 iOS 设备](apple-configurator-direct-enroll-ios.md)。

## <a name="use-the-device-enrollment-program-dep"></a>使用设备注册程序 (DEP)

DEP 将注册配置文件“无线”部署到通过 DEP 购买的设备。 用户在设备上首次启动运行设置助理时，设备会在 Intune 中进行注册。 有关详细信息，请参阅[使用设备注册计划注册 iOS 设备](device-enrollment-program-enroll-ios.md)。

## <a name="use-the-device-enrollment-manager-dem"></a>使用设备注册管理器 (DEM)
设备注册管理器是可注册和管理多达 1,000 台设备的通用用户帐户类型，无需。 由于 DEM 托管设备无法具备用户相关性，因此，设备始终没有所有者。 可以向 Intune 用户授予 DEM 权限，以向其提供这些功能。 DEM 用户注册的每个设备将使用各自的 Intune 许可证。 有关详细信息，请参阅[使用设备注册管理器注册设备](device-enrollment-manager-enroll.md)。
