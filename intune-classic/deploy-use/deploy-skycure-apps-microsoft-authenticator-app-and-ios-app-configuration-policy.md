---
title: 部署 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略
description: 将 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略部署到 Intune 经典门户。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dab1818e627a120935b48861a32d516fbaf5fe9a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>部署 Skycure 应用、Microsoft Authenticator 应用和 iOS 应用配置策略

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>开始之前

-   需要在 [Intune 经典门户](https://manage.microsoft.com/)中完成以下步骤。

-   使用以前在 Skycure 管理控制台中配置的相同 Azure AD 帐户，这也应该是用于登录 Intune 经典门户的相同帐户。

-   请务必熟悉以下过程：

    -   [使用 Intune 部署应用](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)。

    -   [部署 iOS 应用配置策略](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>部署 Skycure 应用、Microsoft Authenticator 应用和 iOS 应用配置策略

1.  在 Intune 经典门户中，依次选择“应用”&gt;“应用”，查看可以管理的应用列表。

2.  选择以下应用：

    a.  Microsoft Authenticator

    b.  适用于 Android 的 Skycure 应用

    c.  适用于 iOS 的 Skycure 应用

       ![显示要部署的所有应用的 Intune 经典门户](../media/mtp/skycure-deploy-app-1.png)

3.  选择“管理部署”，选择包含 Skycure 用户的 Azure AD 安全组，然后单击“下一步”。

4.  在“部署操作”页上，从“审批”下拉列表选择选项“必需的安装”，然后单击“下一步”。

    ![Intune 经典门户中的“部署操作”](../media/mtp/skycure-deploy-app-2.png)

5.  在“VPN 配置文件”页上，从“VPN 策略”下拉列表选择选项“无”，然后单击“下一步”。

6.  在“移动应用配置”页上，选择此前从“应用配置策略”下拉列表创建的 iOS 应用配置策略，然后单击“完成”。

    ![Intune 经典门户中的“移动应用配置”](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>后续步骤

[使用 Intune 设置 Skycure 集成](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
