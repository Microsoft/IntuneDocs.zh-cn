---
title: 使用 Intune 设置 Better Mobile 集成
titleSuffix: Intune on Azure
description: 将 Better Mobile 连接器与 Intune 集成
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: a677bab1f18fc0d0e0d159f2b40fae314b292e0f
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231102"
---
# <a name="integrate-better-mobile-with-intune"></a>将 Better Mobile 与 Intune 集成

完成以下步骤以将 Better Mobile Threat Defense 解决方案与 Intune 相集成。

## <a name="before-you-begin"></a>在开始之前

> [!NOTE]
> 以下步骤在 [Better Mobile 管理控制台](https://aad.bmobi.net)中完成。

开始将 Better Mobile 与 Intune 集成之前，请确保具有以下各项：

-   Microsoft Intune 订阅

-   用于授予下列权限的 Azure Active Directory 管理员凭据：

    -   登录和读取用户配置文件

    -   使用已登录用户的身份访问目录

    -   读取目录数据

    -   向 Intune 发送设备信息

-   用于访问 Better Mobile 管理控制台的管理员凭据。

### <a name="better-mobile-app-authorization"></a>Better Mobile 应用授权

Better Mobile 应用授权流程如下：

-   允许 Better Mobile 服务将与设备运行状况状态相关的信息反馈给 Intune。

-   同步 Better Mobile 与 Azure AD 注册组成员身份，以填充其设备的数据库。

-   允许 Better Mobile 管理控制台使用 Azure AD 单一登录 (SSO)。

-   允许 Better Mobile 应用使用 Azure AD SSO 登录。

## <a name="to-set-up-better-mobile-integration"></a>要设置 Better Mobile 集成，请执行以下操作：

1. 转到 [Better Mobile 管理控制台](https://aad.bmobi.net)，使用凭据登录。
2. 选择“集成” > “EMM/MDM” > “添加帐户”。

     ![Better Mobile 管理控制台](media/better_mobile_console.png)
 
3. 选择“Intune”。
4. 在“帐户名称”旁边，键入描述符。 
5. 在“Microsoft 登录”窗口中，输入 Intune 凭据。
6. 在“请求权限”窗口中，选择“接受”。
7. 搜索希望 Better Mobile 从中同步设备的 Azure AD 安全组，并在列表中选择它们。 然后，选择“继续”。
8. 选择“完成”。
9. 随即会再次出现“添加帐户”页。 关闭该页。 

## <a name="next-steps"></a>后续步骤

-   [设置更好的客户端应用](mtd-apps-ios-app-configuration-policy-add-assign.md)