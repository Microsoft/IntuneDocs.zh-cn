---
title: Intune 设备注册的多重身份验证
description: 如何在 Azure AD 中要求对设备注册进行多重身份验证。
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: e8572834aed14ee08b3ba3c74bc7504193397ef5
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune 设备注册的多重身份验证

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 集成 Azure AD 多重身份验证 (MFA) 用于设备注册，从而帮助你保护公司资源的安全。

MFA 需要使用以下任意两种或多种验证方法： 

- 你知道的信息（通常为密码或 PIN）。
- 你拥有的东西（不容易复制的受信任设备，如手机）。
- 你自身的特征（生物识别）。

在 iOS、Android、Windows 8.1 或更高版本、或 Windows Phone 8.1 或更高版本的设备中均支持 MFA。

> [!NOTE]
> 在较旧版本的配置管理器（早于版本 1610 的版本）中，你仍可以在配置管理器管理员控制台中看到 MFA 设置。 请勿尝试在配置管理器管理员控制台中配置 MFA，因为此操作无法生效。 按照本主题所述配置 MFA。

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>将 Intune 配置为要求对设备注册进行多重身份验证
若要在注册设备时需要 MFA，请执行以下步骤：

1. 使用管理员凭据登录到 [Microsoft Azure 门户](https://manage.windowsazure.com)。
2. 选择你的租户。
2. 选择“**应用程序**”选项卡。你将看到一个服务列表，可以为该列表中的服务配置 Azure AD 安全功能。
3. 选择“**Microsoft Intune 注册**”。
4. 选择**配置**。 
5. 在“**多重身份验证和基于位置的访问规则**中，你可以：
    
    -  启用访问规则
    -  选择是否对所有用户或特定 Azure AD 安全组应用该规则。
    -  要求对所有设备的注册进行多重身份验证。
    -  在设备未工作时，要求对注册进行多重身份验证。
    -  选择“**阻止访问企业资源**”，在设备尚未连接到企业网络时阻止该设备注册。 
4. 你还可以单击链接以**定义/编辑你的工作网络位置**，以便配置对设备注册的网络连接要求。

> [!IMPORTANT]
> 
> 请勿为 Microsoft Intune 注册配置**基于设备的访问规则**。
