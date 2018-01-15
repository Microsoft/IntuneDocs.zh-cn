---
title: "将 Zimperium 与 Intune 集成"
titleSuffix: Intune on Azure
description: "将 Intune 与 Zimperium 集成"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 515f99f694a9125d60bb9210becc6722bfb9e24f
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/30/2017
---
# <a name="integrate-zimperium-with-intune"></a>将 Zimperium 与 Intune 集成

若要将 Zimperium 移动威胁防御解决方案与 Intune 集成，请完成以下步骤。

## <a name="before-you-begin"></a>在开始之前

> [!NOTE]
> 以下步骤是在 [Zimperium MTD 控制台](https://staging2-console.zimperium.com)中完成。

开始将 Zimperium 与 Intune 集成之前，请确保你具有以下各项：

-   Microsoft Intune 订阅

-   用于授予下列权限的 Azure Active Directory 管理员凭据：

    -   登录和读取用户配置文件

    -   使用已登录用户的身份访问目录

    -   读取目录数据

    -   向 Intune 发送设备信息

-   用于访问 Zimperium MTD 控制台的管理员凭据。

### <a name="zimperium-app-authorization"></a>Zimperium 应用授权

Zimperium 应用授权流程如下：

-   允许 Zimperium 服务将与设备运行状况状态相关的信息反馈给 Intune。

-   同步 Zimperium 与 Azure AD 注册组成员身份，以填充其设备的数据库。

-   允许 Zimperium 管理控制台使用 Azure AD 单一登录 (SSO)。

-   允许 Zimperium 应用使用 Azure AD SSO 登录。

## <a name="to-set-up-zimperium-integration"></a>设置 Zimperium 集成

1.  转到 [Zimperium MTD 控制台](https://staging2-console.zimperium.com)使用你的凭据登录。

2.  从左侧菜单中选择“管理”。

3.  选择“MDM 设置”选项卡。

4.  选择“添加 MDM”，然后从“MDM 提供商”列表中选择“Microsoft Intune”。

5.  将 Microsoft Intune 设置为 MDM 服务后，“Microsoft Intune 配置”窗口弹出，为每个选项选择“添加 Azure Active Directory”，即添加 Zimperium zConsole、zIPS iOS 和 Android 应用，以授权 Zimperium 通过 Azure AD 单一登录与 Intune 和 Azure AD 进行通信。

    > [!IMPORTANT]
    > 必须添加 Zimperium zConsole、zIPS iOS 和 Android 应用，才能完成 Intune 集成过程。

6.  选择“接受”，授权 Zimperium 应用与 Intune 和 Azure Active Directory 通信。

7.  将 Zimperium zConsole、zIPS iOS 和 Android 应用添加到 Azure AD 后，添加 Azure AD 安全组，以便 Zimperium 可以将 Azure AD 安全组与其服务同步。

8.  选择“完成”，保存配置并启动首次 Azure AD 安全组同步。

## <a name="next-steps"></a>后续步骤

-   [设置 Zimperium 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)
