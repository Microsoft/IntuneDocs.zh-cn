---
title: "应用入门"
titlesuffix: Azure portal
description: "查找应用并将应用添加到设备，以便员工完成工作。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bb02c362f056c454f4d141ce7ae20b9c3ca8035d
ms.sourcegitcommit: a7c1e10e615e5c975bb5d52eca986c5cf5287687
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2017
---
# <a name="get-started-with-adding-apps"></a>应用添加入门

Intune 支持多种将应用部署到公司设备上的方式：

* **软件安装程序**：用于上传下载到用户设备的文件
* __外部链接__：适用于在公共应用商店拥有应用或拥有 Web 应用的情况
* **托管应用**：适用于 iOS 设备，使用这种设备时，需要对 App Store 中获得的应用实施额外的移动应用程序管理

将通过分配公共应用商店应用，实施一种更快捷的应用程序部署方法。

## <a name="how-do-i-assign-a-public-store-app"></a>如何分配公共应用商店应用？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 使用“搜索资源”，搜索 Intune。
3. 选择“移动应用”，然后选择“应用”。
4. 选择“添加”，然后在“Store 应用”下将“iOS”选为“应用类型”。
5. 选择“选择应用”，显示“搜索 App Store”边栏选项卡。
6. 在文本框中，搜索要分配到设备的应用。 选择应用，然后单击“选择”。
7. 在“添加应用”边栏选项卡中，选择“应用信息”，然后确保完整填入所有应用程序信息。 可添加其他可选填的详细信息，来帮助组织此应用，如“所有者”、“说明”、“开发人员”和用于公司隐私策略的“隐私 URL”。
8. 针对“在公司门户中将其显示为特色应用”，请确保选择“是”，然后选择“确定”。
9. 从“添加应用”边栏选项卡选择“添加”，以添加该应用。 此时将转到应用的**概述**。 选择“分配”，然后单击“选择组”以将其分配到测试组。 让应用**可供下载**。 然后在测试设备上，应用应显示为**特色应用**。

## <a name="learn-more"></a>了解详细信息

* [什么是使用 Intune 进行应用管理？](app-management.md)
* [应用生命周期概述](app-lifecycle.md)
* [什么是应用保护策略？](app-protection-policy.md)
