---
title: "下载 Skycure iOS 应用配置策略"
description: "下载 Skycure iOS 应用配置策略以用于部署到最终用户的 Skycure iOS 应用。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 3159985bfbaec40899dd58766e214daa672ee6d4
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="download-skycure-ios-app-configuration-policy"></a>下载 Skycure iOS 应用配置策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>在开始之前

需要登录到 Skycure 管理控制台才能执行后续步骤。

> [!TIP] 
> 如果使用 Microsoft Internet Explorer 11 或 Microsoft Edge，可能需要使用专用模式打开 Skycure 管理控制台。

## <a name="to-download-the-ios-app-configuration-policy"></a>下载 iOS 应用配置策略

1.  转到 [Skycure 管理控制台](https://aad.skycure.com)。

2.  输入你的“Skycure 管理员凭据”，然后单击“继续”。

    ![Skycure 管理控制台登录](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure 管理员用户名是一个电子邮件帐户，它必须是 Azure Active Directory 中的有效用户帐户，否则登录会失败。 Skycure 使用 Azure Active Directory 对使用单一登录 (SSO) 的管理员用户名进行身份验证。

3.  转到“设置”&gt;“设备管理集成”&gt;“EMM 集成选择”，选择“Microsoft Intune”，然后保存所做选择。

2.  单击“集成设置文件”链接，然后保存生成的 \*.zip 文件。 该 .zip 文件包含 **skycure\_configuration.plist** 文件，该文件用于在 Intune 经典控制台中创建 iOS 应用配置策略。

![Skycure 集成设置文件](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>后续步骤

[添加 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

