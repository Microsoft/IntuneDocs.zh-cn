---
title: "下载 Skycure iOS 应用配置策略以配合使用 Intune"
titleSuffix: Intune Azure preview
description: "下载 Skycure iOS 应用配置策略以配合使用 Intune。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d21f440ee6806b545d2b346559d6516993a9cbf
ms.openlocfilehash: f346b365915b482772e9f5eeaa86afb2cee9319f
ms.contentlocale: zh-cn
ms.lasthandoff: 06/14/2017


---

# <a name="download-skycure-ios-app-configuration-policy"></a>下载 Skycure iOS 应用配置策略

## <a name="before-you-begin"></a>在开始之前

需要登录到 Skycure 管理控制台才能执行后续步骤。

> [!TIP] 
> 如果使用 Microsoft Internet explorer 11 或 Edge，可能需要使用专用模式打开 Skycure 管理控制台。

## <a name="to-download-the-ios-app-configuration-policy"></a>下载 iOS 应用配置策略

1.  转到 [Skycure 管理控制台](https://aad.skycure.com)。

2.  输入你的“Skycure 管理员凭据”，然后单击“继续”。

    ![Skycure 管理控制台登录](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Skycure 管理员用户名是一个电子邮件帐户，它必须是 Azure Active Directory 中的有效用户帐户，否则登录会失败。 Skycure 使用 Azure Active Directory 对使用单一登录 (SSO) 的管理员用户名进行身份验证。

3.  转到“设置”&gt;“设备管理集成”&gt;“EMM 集成选择”，选择“Microsoft Intune”，然后保存所做选择。

4.  单击“集成设置文件”链接，然后保存生成的 \*.zip 文件。 该 .zip 文件包含 **skycure\_configuration.plist** 文件，该文件用于在 Intune 经典控制台中创建 iOS 应用配置策略。

![Skycure 集成设置文件](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>后续步骤

[添加 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略](skycure-microsoft-authenticator-app-ios-app-configuration-policy-add.md)

