---
title: "注册评估移动设备 | Microsoft Intune"
description: "当你注册 Intune 的免费 30 天评估时，如何注册移动设备并安装应用"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 581e880fa4308ec627f5b2c1242fb5b30b713743
ms.openlocfilehash: 7bd5f5d8f4931133a8ef1e697b2fec4cccd07b83


---

# 注册评估移动设备并安装应用
若要使用 Intune 设置移动设备管理，首先你必须设置移动设备管理机构，启用设备平台管理，然后使用公司门户应用注册设备。 然后，你可以部署自己发布的 Microsoft Skype 应用。

## 为设备管理准备好服务

1.  **将 Intune 设置为移动设备管理机构**

    在 [Intune 管理员控制台](https://manage.microsoft.com/)中，选择“管理员”&gt;“移动设备管理”。 选择“任务” > “设置 MDM 机构”，然后在“MDM 机构”对话框中选择“是”。

2.  **为设备平台启用 MDM**

    为要管理的设备平台启用移动设备管理。 根据你的平台，需要的要求不同：

    -   **iOS 和 Mac OS X**：请参阅[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune)。

    -   **Android**：Android 移动设备允许用户使用从 Google Play 可用的公司门户应用注册。 Intune 中不需要附加配置。

    -   **Windows Phone**：请参阅[使用 Microsoft Intune 设置 Windows Phone 管理](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune)。

## 注册测试设备

### iOS 和 Mac OS X
安装应用商店中提供的 Microsoft Corporation 的“Microsoft Intune 公司门户”应用，并使用前面添加的 Intune 用户凭据登录。 查看 **“注册的设备”** 以添加自己的设备。

### Android
安装 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 中提供的 Microsoft Corporation 的“Intune 公司门户”应用，并使用前面添加的 Intune 用户凭据登录。

### Windows Phone 8.1
用户会安装 Windows Phone 应用商店中提供的 Microsoft Corporation 的“公司门户”应用，并使用前面添加的 Intune 用户凭据登录。  查看 **“注册的设备”** 以添加自己的设备。

## 安装以前部署的应用
在移动设备上打开“公司门户”，选择“应用”，然后安装“Microsoft Skype”。

若要了解有关使用 Intune 进行移动设备管理的详细信息，请参阅[为在 Microsoft Intune 中注册设备做好准备](/Intune/deploy-use/prerequisites-for-enrollment)。

### 后续步骤
祝贺你！ 你刚完成了“Microsoft Intune 评估”演练的步骤 5。

>[!div class="step-by-step"]

>[&larr;**创建策略**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [**选项和其他功能**&rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  



<!--HONumber=Oct16_HO2-->


