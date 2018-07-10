---
title: 使用 Intune 设置 Pradeo 集成
titleSuffix: Intune on Azure
description: Pradeo 连接器与 Intune 集成
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
ms.openlocfilehash: 223161bd12f40b3539ce2502599eb3324c7458ca
ms.sourcegitcommit: f70d6aaea59b52cd0d7bd3008afd243868967fd6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37067422"
---
# <a name="integrate-pradeo-with-intune"></a>将 Pradeo 与 Intune 集成

完成以下步骤以将 Pradeo 移动威胁防御解决方案与 Intune 相集成。

## <a name="before-you-begin"></a>在开始之前

> [!NOTE]
> 以下步骤在 [Pradeo Security 控制台](https://www.apps-security.com)中完成。

开始将 Pradeo 与 Intune 集成之前，请确保具有以下各项：

-   Microsoft Intune 订阅

-   用于授予下列权限的 Azure Active Directory 管理员凭据：

    -   登录和读取用户配置文件

    -   使用已登录用户的身份访问目录

    -   读取目录数据

    -   向 Intune 发送设备信息

-   用于访问 Pradeo Security 控制台的管理员凭据。

### <a name="pradeo-app-authorization"></a>Pradeo 应用授权

Pradeo 应用授权流程如下：

-   允许 Pradeo 服务将与设备运行状况状态相关的信息反馈给 Intune。

-   同步 Pradeo 与 Azure AD 注册组成员身份，以填充其设备的数据库。

-   允许 Pradeo 管理控制台使用 Azure AD 单一登录 (SSO)。

-   允许 Pradeo 应用使用 Azure AD SSO 登录。

## <a name="to-set-up-pradeo-integration"></a>设置 Pradeo 集成

1.  转到 [Pradeo Security 控制台](https://www.apps-security.com)，使用凭据登录。

2.  从菜单中选择“管理 - 企业移动性管理”。

3.  选择“Intune 徽标”。

4.  在“EMM (企业移动性管理) - Intune”窗口中的“第 1 步”下，选择“Pradeo 连接器”按钮。 

    ![Pradeo EMM Intune 窗口](./media/pradeo_setup.png)

5. 在 Microsoft Intune 连接窗口中，输入 Intune 凭据。

5.  Pradeo 网页重新打开。 在“第 2 步”下，选择“Pradeo 设备运行状况”按钮。

7. 在 Pradeo Intune 连接器窗口中，选择“接受”。 

8. 在 Pradeo 设备 API 连接器窗口中，选择“接受”。

9. Pradeo 网页重新打开。 在“第 3 步”下，选择“连接到 Microsoft”按钮。 

10. 在 Microsoft Intune 身份验证窗口中，输入 Intune 凭据。

11. 出现“成功集成”消息即表示集成已完成。

## <a name="next-steps"></a>后续步骤

-   [设置 Pradeo 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)