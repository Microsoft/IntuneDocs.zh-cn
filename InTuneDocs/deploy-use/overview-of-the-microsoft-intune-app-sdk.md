---
title: "Microsoft Intune App SDK 概述 | Microsoft Docs"
description: "Intune 应用 SDK 同时适用于 iOS 和 Android 平台，并允许通过 Microsoft Intune 使用移动应用管理功能。"
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 99f3aa3c8640dd41133584b3e1cb056dfd493efa


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Microsoft Intune App SDK 概述

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 应用 SDK 同时适用于 iOS 和 Android 平台，并允许通过 Microsoft Intune 使用移动应用管理功能。 此外，还尽量减少开发人员需要进行的代码更改量。

你会发现你可以在不改变应用行为的情况下启用大部分 SDK 功能。 为了增强最终用户和 IT 管理员的体验，可利用 API 针对需要应用参与的功能来自定义应用行为。

你启用应用后，IT 管理员即可将策略部署到 Intune 托管应用，并利用这些功能保护其公司数据。

## <a name="features"></a>功能
### <a name="control-users-ability-to-move-corporate-documents"></a>控制用户移动公司文档的能力
IT 管理员可以控制 Intune 托管应用中公司文档的文件迁移。 例如，可部署一个策略，禁止文件备份应用将公司数据备份到云。  

### <a name="configure-clipboard-restrictions"></a>配置剪贴板限制
IT 管理员可以配置 Intune 托管应用中的剪贴板行为。 例如，可部署一个策略，让最终用户无法使用剪贴板从 Intune 管理的应用进行剪切或复制并粘贴到不受管理的应用。

### <a name="enforce-encryption-on-saved-data"></a>对已保存数据强制执行加密
IT 管理员可强制实施一个策略，确保对应用保存到设备的数据进行加密。

### <a name="remotely-wipe-corporate-data"></a>远程擦除公司数据
当从 Microsoft Intune 取消注册设备时，IT 管理员可远程擦除 Intune 托管应用上的公司数据。 此功能基于标识，将仅删除与公司标识相关的最终用户文件。 若要执行此操作，此功能要求应用的参与。 应用可指定基于用户设置应进行擦除的标识。 在应用没有指定这些用户设置的情况下，默认行为是擦除应用程序目录，并通知最终用户已删除公司资源访问权限。

### <a name="enforce-the-use-of-a-managed-browser"></a>强制使用托管浏览器
当用户从 Intune 管理的应用打开链接时，IT 管理员可以强制使用受管理的浏览器。 当最终用户使用 Microsoft Intune 管理的浏览器时，有助于确保电子邮件（位于 Intune 管理的邮件客户端中）中显示的链接保持在 Intune 管理的应用域中。

### <a name="enforce-a-pin-policy"></a>强制执行 PIN 策略
启动 Intune 托管应用时，IT 管理员可以强制执行 PIN 策略。 此策略有助于确保将其设备注册到 Microsoft Intune 的最终用户与应用启动者是同一个人。 当最终用户配置其 PIN 时，Intune 应用 SDK 使用 Azure Active Directory 验证其凭据是否为设备注册凭据。

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>要求用户先输入凭据才能启动应用
IT 管理员可要求最终用户输入其凭据才能启动 Intune 管理的应用。 Intune 应用 SDK 使用 Azure Active Directory 提供单一登录体验。 这意味着一旦输入凭据，后续登录将重复使用该凭据。 SDK 还支持通过[与 Azure Active Directory 联合](/active-directory/active-directory-aadconnect-federation-compatibility)的标识管理解决方案进行身份验证。

### <a name="check-device-health-and-compliance"></a>检查设备运行状况和合规性
在最终用户访问 Intune 管理的应用之前，IT 管理员可检查设备的运行状况及其是否符合公司策略。 在 iOS 平台上，此策略将检查设备是否已越狱。 在 Android 平台上，此策略将检查设备是否已获得 root 权限。  



<!--HONumber=Dec16_HO3-->


