---
title: "在 Intune 中注册 macOS 设备"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何在 Intune Azure 预览版中注册 macOS 设备。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 63ac5ecf6fbe9ae66c879466c7785b051dfb7a61
ms.lasthandoff: 02/18/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>在 Intune Azure 预览版中注册 macOS 设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可借助 Intune 管理 macOS 设备。 若要启用设备管理，用户必须转到[公司门户网站](http://portal.manage.microsoft.com)，并按照提示注册其设备。 macOS 设备处于托管状态后，可[为 macOS 设备创建自定义设置](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-macos)。 即将推出更多功能。

## <a name="prerequisites"></a>先决条件

设置 macOS 设备注册之前请先完成以下先决条件：

- [配置域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [设置 MDM 机构](set-mdm-authority.md)
- [创建组](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [配置公司门户](/intune-azure/manage-apps/company-portal-app.md)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>设置 macOS 注册

默认情况下，Intune 允许注册 macOS 设备。 

若要阻止 macOS 注册设备，请参阅[设置设备类型限制](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions)。 

若要设置用户可注册的最多设备数，请参阅 [Set device limit restrictions](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions)（设置设备限制约束）。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

需告知最终用户转到[公司门户网站](http://portal.manage.microsoft.com)并按照提示注册其设备。 还可以向他们发送指向在线注册步骤的链接：[在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)。 

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [通过 Intune 使用 iOS 或 macOS 设备](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)
