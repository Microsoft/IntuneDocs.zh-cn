---
title: "在 Intune 中注册 macOS 设备 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何在 Intune Azure 预览版中注册 macOS 设备。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>在 Intune Azure 预览版中注册 macOS 设备

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

作为 Intune 管理员，你可以管理 macOS 设备。 默认情况下，Azure 门户允许用户注册其 macOS 设备。 只需告知用户转到[公司门户网站](http://portal.manage.microsoft.com)并注册其 macOS 设备即可。 

## <a name="prerequisites"></a>先决条件

设置 macOS 设备注册之前请先完成以下先决条件：

- [配置域](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [设置 MDM 机构](set-mdm-authority.md)
- [创建组](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [配置公司门户](/intune-azure/manage-apps/company-portal-app.md)
- 在 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)中分配用户许可证
- [获取 Apple MDM Push Certificate](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>设置 macOS 注册

默认情况下，Intune 已准备好进行设置，以允许注册 macOS 设备。 

若要查看允许或阻止注册 macOS 设备的设置，请转到 Azure 门户中的“Intune”边栏选项卡，然后选择“注册” > “注册限制”。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告诉用户如何注册其设备以访问公司资源

有关最终用户注册说明，请参阅[在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)。 注册过程会告知用户将出现的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

有关其他最终用户任务的信息，请参阅以下文章：

- [有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [通过 Intune 使用 iOS 或 macOS 设备](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


