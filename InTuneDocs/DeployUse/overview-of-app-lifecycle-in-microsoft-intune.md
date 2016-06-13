---
# required metadata

title: 应用生命周期概述 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 应用生命周期概述

当应用被添加并进一步完成其他阶段时，Intune 应用生命周期便已开始，直到你删除它们。

![应用生命周期](./media/app-lifecycle.png "the Intune app lifecycle")

## 添加

应用部署的第一步是添加你要管理的应用并将其部署到 Intune 中。 尽管你可以使用许多不同的应用类型，但基本的过程都是相同的。 Intune 使你可以为[已注册设备](add-apps-for-mobile-devices-in-microsoft-intune.md)和[使用 Intune 客户端软件管理的 Windows 电脑](add-apps-for-windows-pcs-in-microsoft-intune.md)添加应用。

## 部署

一旦你将应用添加到 Intune 后，就可以[将其部署到你管理的设备](deploy-apps.md)。 Intune 让这一过程变得简单，在部署应用之后，你可以从 Intune 管理控制台[监视是否成功](monitor-apps-in-microsoft-intune.md)部署。 此外，一些应用商店，如 [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) 和 [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) 应用商店，允许你为公司批量购买应用许可证。 Intune 可以同步这些商店的数据，从而让你直接从 Intune 管理控制台为这些类型的应用部署和跟踪许可证使用情况。

## 用户密码重置策略

作为应用生命周期的一部分，将定期发布新版本的应用。 Intune 提供工具来轻松地[更新你已部署的应用](update-apps-using-microsoft-intune.md)到最新版本。 此外，一些应用还让你配置额外的功能，例如：
- [iOS 应用配置策略](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)让你为应用运行时所使用的可兼容 iOS 应用提供设置。 例如，某个应用可能需要特定的品牌设置或要连接到的服务器的名称。
- [托管浏览器策略](manage-internet-access-using-managed-browser-policies.md)帮助你为 Intune 托管的浏览器配置设置，该浏览器替换默认设备浏览器并让你能够限制你的用户可以访问的网站。

## 保护

Intune 为你提供了许多方法来帮助保护你的应用中的数据。 主要方法是：
- [条件性访问](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)让你基于指定的条件（如设备类型或是否符合所部署的[设备合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)）来控制对电子邮件和其他服务的访问。
- [移动应用程序管理 (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)作用于个人应用以帮助保护它们使用的公司数据。 例如，你可以限制在未托管应用和你管理的应用之间复制数据，或者可以阻止应用在已越狱或取得 root 权限的设备上运行。

## 停用

最后，有可能你部署的应用会过期且需要被删除。 Intune 使得[从服务停用应用](retire-apps-using-microsoft-intune.md)变得简单。


<!--HONumber=May16_HO2-->


