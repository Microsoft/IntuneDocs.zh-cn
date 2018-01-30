---
title: "Intune 应用生命周期概述"
description: "了解有关 Intune 托管应用的生命周期（从添加到最终停用）。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 87bd0ceed846052444e4dac4366e3a0304b1452c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="overview-of-the-app-lifecycle"></a>应用生命周期概述

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

当添加 Intune 应用并进一步完成其他阶段时，该应用的生命周期便已开始，直到你删除它。

![应用生命周期](./media/app-lifecycle.png "Intune 应用生命周期")

## <a name="add"></a>添加

应用部署的第一步是添加你要管理的应用并将其分配到 Intune 中。 尽管你可以使用许多不同的应用类型，但基本的过程都是相同的。 借助 Intune，你可以为[已注册设备](apps-add.md)（[经典门户](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)）和[使用 Intune 客户端软件管理的 Windows 电脑](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)添加应用。

## <a name="deploy"></a>部署

在将应用添加到 Intune 后，就可以[将其分配到你管理的用户和设备](apps-deploy.md)（[经典门户](/intune-classic/deploy-use/deploy-apps)）。 使用 Intune 可让这一过程变得更加简单，在部署应用之后，你可以从 Intune 管理控制台[监视是否成功](apps-monitor.md)部署（[经典门户](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)）。 此外，在一些应用商店中，如 [Apple](vpp-apps-ios.md)（[经典门户](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)）和 [Windows](windows-store-for-business.md)（[经典门户](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)）应用商店，你还可以为公司批量购买应用许可证。 Intune 可以同步这些商店的数据，从而让你直接从 Intune 管理控制台为这些类型的应用部署和跟踪许可证使用情况。

## <a name="configure"></a>用户密码重置策略

作为应用生命周期的一部分，将定期发布新版本的应用。 Intune 提供了一些工具，可轻松地将你部署的[应用更新](apps-add.md)（[经典门户](/intune-classic/deploy-use/update-apps-using-microsoft-intune)）到较新版本。 此外，你还可以为一些应用配置额外的功能，例如：
- [iOS 应用配置策略](app-configuration-policies-use-ios.md)（[经典门户](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)）为应用运行时所使用的兼容 iOS 应用提供设置。 例如，某个应用可能需要特定的品牌设置或要连接到的服务器的名称。
- [Managed Browser 策略](app-configuration-managed-browser.md)（[经典门户](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)）可帮助你为 Intune Managed Browser 配置设置，这将取代默认设备浏览器，并让你能够限制用户可访问的网站。

## <a name="protect"></a>保护

Intune 为你提供了许多方法来帮助保护你的应用中的数据。 主要方法是：
- [条件性访问](conditional-access.md)（[经典访问](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)）可根据你指定的条件控制对电子邮件和其他服务的访问。 条件包括设备类型或者是否符合已部署的[设备符合性策略](device-compliance.md)（[经典门户](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)）。
- [应用保护策略](app-protection-policy.md)（[经典门户](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)）作用于各个应用，可帮助保护它们使用的公司数据。 例如，你可以限制在非托管应用和你管理的应用之间复制数据，或者可以阻止应用在已越狱或取得 root 权限的设备上运行。

## <a name="retire"></a>停用

最后，有可能你部署的应用会过期，并且需要将其删除。 Intune 使得[从服务停用应用](device-management.md)变得简单（[经典门户](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)）。
