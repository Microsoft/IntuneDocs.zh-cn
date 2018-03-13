---
title: "设置 Check Point SandBlast 与 Intune 的集成"
titlesuffix: Azure portal
description: "设置 Check Point SandBlast 与 Intune 的集成"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b1ea4804005abb1e2fcbc5dc3b5ef1382edd4db
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>将 Check Point SandBlast Mobile 与 Intune 集成

## <a name="before-you-begin"></a>在开始之前

> [!NOTE] 
> 需要在 [Check Point SandBlast Mobile MTD 控制台](https://intune-4.eu1.locsec.net/)中执行以下步骤。

开始将 Check Point SandBlast Mobile 与 Intune 集成之前，请确保你具有以下各项：

-   Microsoft Intune 订阅

-   用于授予下列权限的 Azure Active Directory 管理员凭据：

    -   登录和读取用户配置文件

    -   使用已登录用户的身份访问目录

    -   读取目录数据

    -   向 Intune 发送设备信息

-   用于访问 Check Point SandBlast Mobile MTD 控制台的管理员凭据。

### <a name="check-point-sandblast-app-authorization"></a>Check Point SandBlast 应用授权

Check Point SandBlast 应用授权流程包含下列内容：

-   允许 Check Point SandBlast Mobile 服务将与设备运行状况状态相关的信息反馈给 Intune。

-   同步 Check Point SandBlast Mobile 与 Azure AD 注册组成员身份，以填充其设备的数据库。

-   允许 Check Point SandBlast 管理控制台使用 Azure AD 单一登录 (SSO)。

-   允许 Check Point SandBlast Mobile 应用使用 Azure AD SSO 登录。

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>设置 Check Point SandBlast Mobile 集成

1.  请转到 [Check Point SandBlast Mobile MTD 控制台](https://intune-4.eu1.locsec.net/)，并使用凭据登录。

2.  单击“设置”选项卡。

3.  依次选择“设备管理”和“设置”。

4.  从“MDM 服务”下拉列表中选择 “Microsoft Intune”。

5.  将 Microsoft Intune 设置为 MDM 服务后，系统会弹出“Microsoft Intune 配置”窗口，请为每个设备平台（ iOS、Android 和 Windows）选择“添加到我的组织”，授权 Check Point SandBlast Mobile 与 Intune 和 Azure AD 进行通信。

    ![Check Point MTD Intune 配置](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > 必须添加所有设备平台，才能继续执行下一步。

6.  选择“接受”，授权 Check Point SandBlast Mobile 应用与 Intune 和 Azure Active Directory 进行通信。

7.  启用所有设备平台后，需要输入 Azure AD 安全组。

8.  选择“验证”，Azure AD 安全组成功通过验证后，选择“保存”。

## <a name="next-steps"></a>后续步骤

- [设置 Check Point SandBlast Mobile 应用](mtd-apps-ios-app-configuration-policy-add-assign.md)