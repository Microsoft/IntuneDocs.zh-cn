---
title: "注册移动设备并安装应用 | Microsoft Intune"
description: "注册移动设备并在注册了 Intune 的设备上安装应用"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d422b421c3716ad576c4fc565b181dec28c947e
ms.openlocfilehash: ec478ad05b72a358dbce4f08a6b1a1f106a28303


---

# 注册移动设备并安装应用
若要使用 Intune 设置移动设备管理，首先必须设置移动设备管理机构，启用设备平台管理，然后使用公司门户应用注册设备。 然后，你可以部署在步骤 6 中发布的 Microsoft Skype 应用程序。

## 启用设备管理并注册设备

1.  **将 Intune 设置为移动设备管理机构**在 [Intune 管理控制台](https://manage.microsoft.com/)中，选择**管理** > **移动设备管理**，然后选择**任务**下的**设置 MDM 机构**。  在“MDM 机构”对话框中选择“是”。
    ![管理控制台。 设置 mdm 到 Intune](./media/mdmAuthority.png)

2.  **为设备平台启用 MDM**为要管理的设备平台启用移动设备管理。 根据你的平台，需要的要求不同：

    -   **iOS 和 Mac OS X**：请参阅[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。

    -   **Windows Phone**：请参阅[使用 Microsoft Intune 设置 Windows Phone 管理](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)。

    -   **Android**：Android 移动设备允许用户使用从 [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider) 可用的公司门户应用注册。 Intune 中不需要附加配置。

3.  **注册设备**：

    -   **Android** - 安装 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 中提供的 Microsoft Corporation 的 **Intune 公司门户**应用，并使用前面添加的 Intune 用户凭据登录。

    -   **iOS and Mac OS X** - 安装应用商店中提供的 Microsoft Corporation 的 **Microsoft Intune 公司门户**应用，并使用前面添加的 Intune 用户凭据登录。 查看 **“注册的设备”** 以添加自己的设备。

    -   **Windows Phone 8.1** - 用户安装 Windows Phone 应用商店中提供的 Microsoft Corporation 的**公司门户**应用，并使用前面添加的 Intune 用户凭据登录。  查看 **“注册的设备”** 以添加自己的设备。

    -   **Windows Phone 8.0** - 用户选择**系统设置**&gt;**公司应用**，并使用上面添加的 Intune 用户凭据登录。 公司门户应用将部署到你的手机。

    如果系统提示输入 **“服务器地址”**，请键入“manage.microsoft.com”。

## 在已注册的设备上安装应用
在此快速入门指南的[第 6 步](start-with-a-paid-subscription-to-microsoft-intune-step-6.md)中，你已将 Skype 应用发布到自定义的 Intune 用户组。 现在，你将在新注册的设备上安装此应用。

在已注册的移动设备上打开“公司门户”，选择**应用**，然后安装**Microsoft Skype**。

若要深入了解如何使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理移动设备，请参阅[在 Microsoft Intune 中注册设备的先决条件](/intune/deploy-use/prerequisites-for-enrollment)。


### 后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的最后一步。 由于已完成初始配置，你可考虑启用附加的 MDM 功能。

>[!div class="step-by-step"]

>[&larr;**注册设备**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)[**配置后任务**&rarr;](.\post-configuration-tasks.md)  



<!--HONumber=Oct16_HO4-->


