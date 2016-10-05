---
title: "部署 Lookout for Work 应用 | Microsoft Intune"
description: "配置并部署 Android 版 Lookout for Work 应用。"
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c4d05b9ba7249e4068d21480b1c9db342277757e
ms.openlocfilehash: 687a102ccb34cb7acfaab1e8a1d4b67cb54b9e92


---

# 配置并部署 Lookout for Work 应用
本文介绍了如何为已注册的设备和运行 Android 4.1 或更高版本的设备配置和部署 Lookout for Work 应用。

* **步骤 1：**在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，转到“应用”并选择“添加应用”。   
* **步骤 2：**在发布者的“软件设置”页选择“外部链接”，并指定下列 URL：https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>请勿单击要求使用托管浏览器的框。

* **步骤 3：**在“软件描述”页填入以下信息：
  * **发布者：**Lookout Mobile Security
  * **名称：**Lookout for Work
  * **说明：**Lookout 能为设备提供针对移动威胁的最佳保护。 在设备上安装 Lookout 应用后，该应用可让设备免受威胁，并将在发现任何威胁时向用户、公司和管理员发出警报。
  * **类型：**计算机管理
* **步骤 4：**成功完成时将显示消息“数据已成功上传至 Microsoft Intune”。

在 Intune 管理员控制台中单击“应用”时，列表中立即显示 Lookout for Work 应用 ![Intune 管理员控制台应用页面的屏幕截图，其中显示了列出的 Lookout for Work 应用](../media/mtp/lookout-app-listed-intune-console.png)

**若要将应用部署到用户**，请选择以上屏幕中显示的 Lookout for Work 应用，并选择“管理部署”。

选择的用户必须与添加到 Lookout MTP 控制台“注册管理”选项中的用户一致。  请参阅[为订阅配置 Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) 部分中的步骤 3，了解有关将用户组添加到 Lookout MTP 的信息。
>[!IMPORTANT]
> Intune 应用部署向导并未识别到 Azure AD 用户组且使用的是 Intune 用户组，因此必须基于在 Lookout MTP 控制台中注册的 Azure AD 用户组创建 Intune 用户组（如[本](plan-your-user-and-device-groups.md)主题所述）。

选择“必需安装”选项，该选项要求在用户设备上安装 Lookout 应用。


选择部署“必需安装”选项后，Intune 会将 Lookout for Work 应用程序推送到设备。   

用户在设备上打开 Lookout for Work 时，将提示其激活应用并选择“使用 Azure Active Directory 登录”选项。 以下主题中提供了最终用户操作流程的详细指导：

* [系统提示在 Android 设备上安装 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Lookout for Work 在 Android 设备上发现威胁，请解除该威胁](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## 后续步骤
* [在合规性策略中启用设备威胁保护规则](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO3-->


