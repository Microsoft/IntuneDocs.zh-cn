---
title: 部署策略和应用
description: 可以启用策略设置并部署将在设备注册到管理后立即应用的应用。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5283d040c7b4c39c495a13a71643b6569eed09bd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="create-policies-and-publish-apps"></a>创建策略并发布应用

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主题指导 Intune 管理员如何创建策略和发布应用，并将其部署到托管设备。

在开始将应用注册到 Intune 之前，可以启用策略设置以及将会在这些设备进入管理后立即部署的应用。 Intune 策略提供的设置有助于控制移动设备上的安全设置、维护计算机的 Windows 防火墙和 Endpoint Protection 设置以及部署应用程序。 可以配置策略、添加应用并对这些应用进行部署，以便设备在 Intune 中注册后立即接收设置和应用。

策略和应用是特定于平台的。

## <a name="manage-device-settings"></a>管理设备设置

 设备策略设置是以每个平台基础进行配置和管理的。 以下链接提供了适用于各平台的可用设置的列表：

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android 和 Samsung KNOX 标准版](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10（电脑版和移动版）](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows 团队](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [运行 Intune 软件客户端的 Windows 电脑](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

可详细了解如何[使用 Microsoft Intune 策略管理设备上的设置和功能](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)。

## <a name="add-and-deploy-apps"></a>添加和部署应用

可以将应用添加到 Intune，然后通过两种方式将其部署到托管设备：
- **必需的安装** - 应用会自动将应用安装到托管设备
- **可用安装** - 应用将显示在 Intune 公司门户中，以便用户可以选择是否在其设备上安装它们

### <a name="add-apps"></a>添加应用

首先，必须通过以下方法之一使应用在 Intune 中可用：
- [为已注册设备添加应用](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [为 Intune 软件客户端电脑添加应用](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>部署应用

现在该应用已在 Intune 中可用，你可以将其部署到托管设备：
- [将应用部署到设备](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- 部署批量采购的应用：
  - [iOS - 批量采购计划](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
  - [适用于企业的 Microsoft 应用商店](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
  - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    配置应用以便进行部署之后，可以[配置应用](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)。

> [!div class="step-by-step"]
> 
> [&larr; **组织用户和设备**](./start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**自定义公司门户** &rarr;](/intune/company-portal-customize)  
