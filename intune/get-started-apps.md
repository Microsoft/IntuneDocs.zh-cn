---
title: "应用入门"
titlesuffix: Azure portal
description: "查找应用并将应用添加到设备，以便员工完成工作。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28bc8547d56073a2175ca57e03dbd9b94fc03ba9
ms.sourcegitcommit: fa6aaf12611c3e03e38e467806fc30b1d0255e88
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2017
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
4. 选择“添加”，然后将“iOS 应用商店应用”选为“应用类型”。
5. 在文本框中，搜索要分配到设备的应用。 选择应用，然后选择“确定”。
6. 在“添加应用”边栏选项卡中，选择“应用信息”，然后确保完整填入所有应用程序信息。 可添加其他可选填的详细信息，来帮助组织此应用，如“所有者”、“说明”、“开发人员”和用于公司隐私策略的“隐私 URL”。
7. 针对“在公司门户中将此显示为特色应用”，请确保选择“是”，然后选择“确定”。
8. 选择“添加”以添加一个应用。 此时将转到应用的**概述**。 选择“分配”，然后单击“选择组”以将其分配到测试组。 让应用**可供下载**。 然后在测试设备上，应用应显示为**特色应用**。

## <a name="learn-more"></a>了解详细信息

* [什么是使用 Intune 进行应用管理？](app-management.md)
* [应用生命周期概述](app-lifecycle.md)
* [什么是应用保护策略？](app-protection-policy.md)
