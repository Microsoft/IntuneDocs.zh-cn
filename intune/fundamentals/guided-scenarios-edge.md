---
title: 引导式方案 - 部署 Microsoft Edge for Mobile
titleSuffix: Microsoft Intune
description: 在 Microsoft 365 设备管理门户中了解关于部署 Microsoft Edge for Mobile 的引导式方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585691"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>引导式方案 - 部署 Microsoft Edge for Mobile 

按照此[引导式方案](~/fundamentals/guided-scenarios-overview.md)操作，可将 Microsoft Edge 应用分配到组织中使用 iOS 或 Android 设备的用户。 通过分配此应用可让你的用户使用其公司设备无缝浏览内容。 

Microsoft Edge 利用内置功能帮助用户合并、整理和管理工作内容，从而使用户摆脱 Web 混乱的局面。 如果 iOS 和 Android 设备用户在 Microsoft Edge 应用程序中使用其公司 Azure AD 帐户登录，他们将发现其浏览器已预加载工作区“收藏夹”和你定义的网站筛选器  。

> [!NOTE]
> 如果阻止用户注册 iOS 或 Android 设备，则此方案将不会启用注册，用户需要自行安装 Edge。
Intune 策略启用的以下 Microsoft Edge 企业功能包括： 

- **双重标识** - 用户可以同时添加工作帐户以及个人帐户以进行浏览。 两个标识完全独立，这类似于 Office 365 和 Outlook 中的体系结构和体验。 Intune 管理员将能够为工作帐户中受保护的浏览体验设置所需的策略。 
- **Intune 应用保护策略集成** - 管理员现在可以将应用保护策略定向到 Microsoft Edge，包括控制剪切、复制和粘贴，防止执行屏幕捕获，并确保仅在其他托管应用中打开用户选择的链接。
- **Azure 应用程序代理集成** - 管理员可以控制对 SaaS 应用和 Web 应用的访问，帮助确保仅在安全的 Microsoft Edge 浏览器中运行基于浏览器的应用，不论最终用户是从公司网络连接还是从 Internet 连接。 
- **托管收藏夹和主页快捷方式** - 当最终用户处于其企业环境中时，为了便于访问，管理员可以将 URL 设置为显示在收藏夹下。 管理员可以设置主页快捷方式，该快捷方式将在企业用户在 Microsoft Edge 中打开新页面或新选项卡时显示为主快捷方式。

## <a name="prerequisites"></a>必备条件

- [将 MDM 机构设置为 Intune](mdm-authority-set.md#set-mdm-authority-to-intune) - 移动设备管理 (MDM) 机构设置决定了管理设备的方式。 作为 IT 管理员，必须先设置 MDM 机构，然后用户才能注册设备来进行管理。
- 需要的 Intune 管理员权限：
    - 托管应用读取、创建、删除和分配权限
    - 移动应用读取、创建和分配权限
    - 策略集读取、创建和分配权限
    - 组织读取、更新权限

## <a name="step-1---introduction"></a>步骤 1 - 简介

按照 Microsoft Edge for Mobile 引导式方案操作，你将为选定的 iOS 和 Android 用户组设置 Microsoft Edge 的基本部署  。 此部署将实现“双重标识”和“托管收藏夹和主页快捷键”   。 此外，所选用户注册的设备将通过 Intune 自动安装 Microsoft Edge 应用。 此自动安装将用于所有用户驱动的注册类型，包括： 
- 通过公司门户应用进行 iOS 注册 
- 通过 Apple Business Manager 进行 iOS 用户相关性注册 
- 通过公司门户应用进行旧版 Android 注册 

这一引导式方案将自动使 MyApps 出现在 Microsoft Edge 的收藏夹中，并为浏览器配置你为 Intune 公司门户应用设置的品牌  。 

### <a name="what-you-will-need-to-continue"></a>需要继续执行的操作
我们将询问用户所需的工作区收藏夹以及 Web 浏览所需的筛选器。 请确保已完成以下任务，然后再继续操作：

- 将用户添加到 Azure AD 组。 有关详细信息，请参阅[使用 Azure Active Directory 创建基本组以及添加成员](https://go.microsoft.com/fwlink/?linkid=2102458)。
- 在 Intune 中注册 iOS 或 Android 相关设备。 有关详细信息，请参阅[设备注册](https://go.microsoft.com/fwlink/?linkid=2102547)。
- 收集要在 Microsoft Edge 中添加的工作区收藏夹列表。
- 收集要在 Microsoft Edge 中强制执行的网站筛选器列表。

## <a name="step-2---basics"></a>步骤 2 - 基础知识

在此步骤中，必须为新的 Microsoft Edge 策略输入名称和说明。 如果需要更改分配和配置，可以稍后引用这些策略。 引导式方案会为 iOS 设备添加和分配 Microsoft Edge iOS 应用，并为 Android 设备添加和分配 Microsoft Edge Android 应用。 此步骤还将为这些应用创建配置策略。

## <a name="step-3---configuration"></a>步骤 3 - 配置

在此步骤中，引导式方案将配置 Microsoft Edge，使其显示通过 Intune 分配到用户的所有其他应用，并与 Microsoft Intune 公司门户应用共享同一品牌。 可以使用“主页快捷方式 URL”、“托管书签”列表和“阻止的 URL”列表进一步配置 Microsoft Edge    。 用户在其设备上的 Microsoft Edge 中打开新选项卡时，“首页快捷方式 URL”将在搜索栏下方显示为用户的第一个图标  。 用户在其工作环境中使用 Microsoft Edge 时，可以使用“托管书签”中列出的收藏 URL  。 “阻止的 URL”指定阻止用户在工作环境中访问的网站  。 允许其他所有站点。 

## <a name="step-4---assignments"></a>步骤 4 - 分配

在此步骤中，可以选择要包含的用户组，以便为工作配置 Microsoft Edge 移动设备。 Microsoft Edge 还将安装在这些用户注册的所有 iOS 和 Android 设备上。

## <a name="step-5---review--create"></a>步骤 5 - 查看 + 创建

通过最后一个步骤可以查看配置的设置摘要。 查看你的选择后，请单击“创建”以完成引导式方案  。 

> [!NOTE]
> Edge 最多可能需要 12 小时才能接收配置。 有关详细信息，请参阅 [Microsoft Intune 的应用配置策略](~/apps/app-configuration-policies-overview.md)。

> [!IMPORTANT]
> 引导式方案完成后，系统将显示摘要。 可以稍后修改摘要中列出的资源，但是将不会保存显示这些资源的表。

## <a name="next-steps"></a>后续步骤

- 通过设置 Intune 应用保护策略集成来增强使用 Microsoft Edge 的安全性。 有关详细信息，请参阅 [Microsoft Edge 的应用程序保护策略](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge)。
- 如果要包含 Intranet 站点，请使用 Azure 应用程序代理集成探索保护访问。 有关详细信息，请参阅[为 Microsoft Edge 配置应用程序代理设置](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge)。

