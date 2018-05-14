---
title: Intune 应用 SDK 的优点
titlesuffix: Microsoft Intune
description: Intune 应用 SDK 同时适用于 iOS 和 Android 平台，并允许通过 Microsoft Intune 使用移动应用管理功能。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bb54772010ef71e7d4bd2252f3886e9a3dd37ef1
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="intune-app-sdk-overview"></a>Intune App SDK 概述
Intune App SDK 可用于 iOS 和 Android，可对应用启用 Intune 应用保护策略。 其将努力使应用开发人员所需的代码更改数量降到最低。 你会发现可以在不改变应用行为的情况下启用大部分 SDK 功能。 为了增强最终用户和 IT 管理员体验，可利用 API 针对需要应用参与的功能来自定义应用行为。

为应用启用应用保护策略后，IT 管理员可部署这些策略来保护应用内的公司数据。

## <a name="app-protection-features"></a>应用保护功能

以下是可通过 SDK 来启用的 Intune 应用保护功能的示例。

### <a name="control-users-ability-to-move-corporate-files"></a>控制用户移动公司文件的能力
IT 管理员可控制应用中的工作或学校数据可移动到什么位置。 例如，他们可以部署策略来禁止应用将公司数据备份到云。

### <a name="configure-clipboard-restrictions"></a>配置剪贴板限制
IT 管理员可以配置 Intune 托管应用中的剪贴板行为。 例如，IT 管理员可部署策略来防止最终用户将数据从应用剪切或复制并粘贴到非托管的个人应用。

### <a name="enforce-encryption-on-saved-data"></a>对已保存数据强制执行加密
IT 管理员可以强制执行策略，确保对应用保存到设备的数据进行加密。

### <a name="remotely-wipe-corporate-data"></a>远程擦除公司数据
IT 管理员可从 Intune 托管的应用远程擦除企业数据。 此功能基于标识，将仅删除与最终用户的公司标识相关联的文件。 若要执行此操作，此功能要求应用的参与。 应用可指定基于用户设置应进行擦除的标识。 在应用没有指定这些用户设置的情况下，默认行为是擦除应用程序目录，并通知最终用户已删除访问权限。

### <a name="enforce-the-use-of-a-managed-browser"></a>强制使用托管浏览器
IT 管理员可使用 [Intune Managed Browser 应用](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)强制打开应用中的 Web 链接。 此功能可确保企业环境中显示的链接保持在 Intune 管理的应用的域中。

### <a name="enforce-a-pin-policy"></a>强制执行 PIN 策略
IT 管理员可要求最终用户输入 PIN 以访问应用中的公司数据。 这可确保使用应用的用户与最初使用工作或学校帐户登录的用户为同一用户。 最终用户配置其 PIN 时，Intune App SDK 使用 Azure Active Directory 验证最终用户的凭据是否为已注册的 Intune 帐户。

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>要求用户使用工作或学校帐户进行登录以访问应用
IT 管理员可以要求用户使用其工作或学校帐户登录以访问该应用。 Intune App SDK 使用 Azure Active Directory 提供单一登录体验，其中一旦输入凭据就将在后续登录中重用该凭据。 我们还支持通过与 Azure Active Directory 联合的标识管理解决方案进行身份验证。

### <a name="check-device-health-and-compliance"></a>检查设备运行状况和合规性
在最终用户访问应用之前，IT 管理员可以检查设备的运行状况及其是否符合 Intune 策略。 在 iOS 上，此策略将检查设备是否已越狱。 在 Android 上，此策略将检查设备是否已获得 root 权限。

### <a name="multi-identity-support"></a>多身份支持
多身份支持功能是 SDK 的一种功能，其允许策略托管（企业）帐户和非托管（个人）帐户在单个应用中共存。

例如，许多用户在 iOS 和 Android 的 Office 移动应用中同时配置公司和个人电子邮件帐户。 当用户使用公司帐户访问数据时，IT 管理员必须确信实施应用保护策略。 但是，当用户访问个人电子邮件帐户时，该数据应在 IT 管理员的控制之外。 Intune App SDK 通过**仅**将应用保护策略应用到应用中的公司标识来实现此功能。

多身份功能有助于解决同时支持个人和工作帐户的应用商店应用带给组织的数据保护问题。
 
### <a name="app-protection-without-device-enrollment"></a>无需设备注册的应用保护

>[!IMPORTANT]
>Intune 应用包装工具、Intune App SDK for Android、Intune App SDK for iOS 和 Intune App SDK Xamarin Bindings 提供无需设备注册的 Intune 应用保护。

许多用户使用个人设备，他们希望在不为其个人设备注册移动设备管理 (MDM) 提供程序的情况下访问公司数据。 由于 MDM 注册要求对设备的全局控制权，而用户对于将其个人设备的控制权交给公司有所顾虑。

无需设备注册的应用保护允许 Microsoft Intune 服务将应用保护策略直接部署到应用，而不依赖设备管理通道来部署策略。
