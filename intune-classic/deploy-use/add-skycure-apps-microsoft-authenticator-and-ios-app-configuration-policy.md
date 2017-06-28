---
title: "添加 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略"
description: "将 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略添加到 Intune 经典控制台。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 425b86e92281bb6e3657a6c806be269ccae94311
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>添加 Skycure 应用、Microsoft Authenticator 应用和 iOS 配置策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

需要使用 Intune 来添加和部署 Skycure 应用程序，以便最终用户可以在其移动设备中确定某个威胁时接收通知，并接收指导来解除威胁。

此外，你需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，使用户可以通过 Azure AD 检查其身份，并需要 iOS 应用配置策略来指示 Skycure iOS 应用使用 Intune 和 Azure AD 单一登录 (SSO)，让用户无需在每次登录 Skycure 应用时都键入用户名和密码。

## <a name="before-you-begin"></a>在开始之前

-   需要在 [Intune 经典控制台](https://manage.microsoft.com/)中完成以下步骤。

-   使用以前在 Skycure 管理控制台中配置的相同 Azure AD 帐户，它应该是用于登录到 Intune 经典控制台的同一帐户。

-   你需要具有可供使用的 Skycure 集成文件。 这是此前从 Skycure 管理控制台下载的 .zip 文件，它包含文件 **skycure\_configuration.plist** 和 iOS 应用配置策略参数。

-   请务必熟悉以下过程：

    -   [将应用添加到 Intune](/intune-classic/deploy-use/add-apps)。

    -   [将 iOS 应用配置策略添加到 Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。

## <a name="to-add-the-skycure-app-for-android"></a>添加适用于 Android 的 Skycure 应用

1.  在 Intune 经典控制台中，选择“应用”&gt;“添加应用”来启动 Intune 软件发行者，然后单击“下一步”。

2.  在“软件安装程序”页上，选择“外部链接”，然后在“指定 URL”下粘贴“[适用于 Android 的 Skycure 应用 URL](https://play.google.com/store/apps/details?id=com.skycure.skycure)”。

    ![Intune 软件发行者指定 URL](../media/mtp/skycure-add-apps-1.png)

3.  在“软件描述”页上，输入“发行者”、“名称”和“说明”，选择选项“将此应用显示为特色应用并在公司门户中突出显示”，然后单击“下一步”。

    ![Intune 软件发行者软件描述](../media/mtp/skycure-add-apps-2.png)

4.  单击“上传”，然后单击“关闭”。

## <a name="to-add-the-skycure-app-for-ios"></a>添加适用于 iOS 的 Skycure 应用

1.  在 Intune 经典控制台中，选择“应用”&gt;“添加应用”来启动 Intune 软件发行者，然后单击“下一步”。

2.  在“软件安装程序”页上，选择“来自应用商店的托管 iOS 应用”，然后在“指定 URL”下粘贴[“适用于 iOS 的 Skycure 应用 URL”](https://itunes.apple.com/us/app/skycure/id695620821?mt=8)。

    ![Intune 软件发行者托管的 iOS 应用](../media/mtp/skycure-add-apps-3.png)

3.  在“软件描述”页上，输入“发行者”、“名称”和“说明”，选择选项“将此应用显示为特色应用并在公司门户中突出显示”，然后单击“下一步”。

    ![Intune 软件发行者选项](../media/mtp/skycure-add-apps-4.png)

4.  在“要求”页上，选择“移动设备类型”下的选项“任何”，然后单击“下一步”。

5.  单击“上传”，然后单击“关闭”。

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>添加适用于 iOS 的 Microsoft Authenticator 应用

1.  在 Intune 经典控制台中，选择“应用”&gt;“添加应用”来启动 Intune 软件发行者，然后单击“下一步”。

2.  在“软件安装程序”页上，选择“来自应用商店的托管 iOS 应用”，然后在“指定 URL”下粘贴[“适用于 iOS 的 Microsoft Authenticator 应用 URL”](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)。

    ![Intune 软件发行者托管的 iOS 应用 2](../media/mtp/skycure-add-apps-5.png)

3.  在“软件描述”页上，输入“发行者”、“名称”和“说明”，选择选项“将此应用显示为特色应用并在公司门户中突出显示”，然后单击“下一步”。

    ![Intune 软件发行者托管的 iOS 应用 3](../media/mtp/skycure-add-apps-6.png)

4.  在“要求”页上，选择“移动设备类型”下的选项“任何”，然后单击“下一步”。

5.  单击“上传”，然后单击“关闭”。

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>添加 Skycure iOS 应用配置策略

1.  在 Intune 经典控制台中，选择“策略”&gt;“概述”**&gt;“添加策略”**。

2.  在策略列表中，展开“iOS”，选择“移动应用配置策略(iOS 8.0 及更高版本)”，然后选择“创建策略”。

    ![iOS 应用配置策略](../media/mtp/skycure-add-apps-7.png)

3.  在“创建策略”页的“常规”部分中，输入 iOS 应用配置策略的名称和可选描述。

    a.  使用文本编辑器（如记事本）打开 **skycure\_configuration.plist** 文件，将其内容复制并粘贴到“移动应用配置策略”正文中，选择“验证”，然后选择“保存策略”。

       ![iOS 应用配置策略 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>后续步骤

[部署 Skycure 应用、Microsoft Authenticator 应用和 iOS 应用配置策略](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

