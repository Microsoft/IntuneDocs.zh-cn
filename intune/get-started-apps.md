---
title: "Microsoft Intune 中的应用入门"
titlesuffix: 
description: "查找应用并将其添加到设备，以便员工完成工作。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>在 Microsoft Intune 中添加应用入门

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 Intune 支持几种不同的应用类型。 此外，每种应用类型的可用选项也各不相同。

通过 Intune，可向公司设备添加并分配以下应用类型：
- **应用商店中的应用** - 适用于需要对 App Store 中获得的应用实施额外的移动应用程序管理的设备。
- **内部编写的应用（业务线）**- 用于上传下载到用户设备的文件。
- **内置应用** - 用于向 iOS 和 Android 设备分配特选托管应用（例如 Office 365 应用）。 
- **Web 上的应用** - 可供 Intune 用于在设备主屏幕上创建一个到 Web 应用的快捷方式。

## <a name="how-do-i-assign-a-public-store-app"></a>如何分配公共应用商店应用？

以下示例逐步讲述如何在 Microsoft Intune 中添加 iOS 应用。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 边栏选项卡上，选择“移动应用”。
4. 在“移动应用”工作负载中，选择“管理”部分下的“应用”。
5. 选择“应用”窗格右侧的“添加”。
6. 在“应用类型”列表中，选择可用“应用商店应用”类型下的“iOS”。
6. 选择“搜索 App Store”。
7. 在“搜索 App Store”边栏选项卡中，首先选择 App Store 国家/地区的区域设置。
8. 在搜索框中键入名称（或名称的一部分）。 Intune 将搜索应用商店并返回相关结果的列表。
9. 从列表中选择所需应用，然后单击“选择”。
10. 选择“应用信息”，配置应用信息。
11. （可选）可添加详细信息来帮助组织此应用，如“所有者”、“说明”、“开发人员”和“隐私 URL”（指向公司隐私策略）。
12. 对于“在公司门户中将其显示为特色应用”选项，选择“是”。 
13. 添加了所有必要的应用信息后，单击“确定”。
14. 单击“添加应用”边栏选项卡中的“添加”。此时会转到该应用的“概述”。 

## <a name="next-steps"></a>后续步骤

现在已向 Intune 添加了一个应用，因此可以分配能够在其设备上包含该应用的员工组。

- [如何将应用分配到组](apps-deploy.md)
- 
## <a name="learn-more"></a>了解详细信息

* [什么是使用 Intune 进行应用管理？](app-management.md)
* [应用生命周期概述](app-lifecycle.md)
* [什么是应用保护策略？](app-protection-policy.md)
