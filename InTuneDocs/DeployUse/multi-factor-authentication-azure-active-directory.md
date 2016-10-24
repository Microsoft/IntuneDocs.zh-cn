---
title: "使用 Azure AD 进行多重身份验证 | Microsoft Intune"
description: "如何在 Azure AD 中要求对设备注册进行多重身份验证。"
keywords: 
author: nbigman
ms.author: nbigman
manager: angerobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: ccd55cc8637ebccfdbddd05c4f6b182c7923a2ab


---

# Microsoft Intune 的多重身份验证

Intune 集成 Azure AD 多重身份验证 (MFA) 用于设备注册，从而帮助你保护公司资源的安全。 除用户名和密码外，MFA 需要身份验证因素，例如文本身份验证。 在 iOS、Android、Windows 8.1 或更高版本、或 Windows Phone 8.1 或更高版本的设备中均支持身份验证。

> [!NOTE]
>
> 在较旧版本的配置管理器（早于版本 1610 的版本）中，你仍可以在配置管理器管理员控制台中看到 MFA 设置。 请勿尝试在配置管理器管理员控制台中配置 MFA，因为此操作无法生效。 按照本主题所述配置 MFA。

### 将 Intune 配置为要求对设备注册进行多重身份验证
若要要求对设备注册执行 MFA，请按照以下步骤操作：

1. 使用管理员凭据登录到 [Microsoft Azure 门户](https://manage.windowsazure.com)。
2. 选择你的租户。
2. 选择“**应用程序**”选项卡。 你将看到一个服务列表，可以为该列表中的服务配置 Azure AD 安全功能。
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



<!--HONumber=Sep16_HO4-->


