---
title: "在 Intune 中注册 macOS 设备"
titlesuffix: Azure portal
description: "了解如何在 Intune 中注册 macOS 设备。"
keywords: 
author: ErikjeMS
ms.author: erikje
nmanager: dougeby
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8528b3ec28499657b1eb39e1b981f92be3ab83ca
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-macos-devices-in-intune"></a>在 Intune 中注册 macOS 设备

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可借助 Intune 管理 macOS 设备。 若要启用设备管理，用户必须转到[公司门户网站](http://portal.manage.microsoft.com)，并按照提示注册其设备。 macOS 设备处于托管状态后，可[为 macOS 设备创建自定义设置](custom-settings-macos.md)。 即将推出更多功能。

## <a name="prerequisites"></a>必备条件

设置 macOS 设备注册之前请先完成以下先决条件：

- [配置域](custom-domain-name-configure.md)
- [设置 MDM 机构](mdm-authority-set.md)
- [创建组](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [配置公司门户](company-portal-app.md)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>设置 macOS 注册

默认情况下，Intune 允许注册 macOS 设备。

若要阻止 macOS 注册设备，请参阅[设置设备类型限制](enrollment-restrictions-set.md)。

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

告知最终用户转到[“公司门户”网站](http://portal.manage.microsoft.com)，并按照提示注册自己的设备。 还可以向他们发送指向在线注册步骤的链接：[在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)
- [通过 Intune 使用 iOS 或 macOS 设备](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
