---
title: 具有应用保护策略的 iOS/iPadOS 应用
description: 本主题描述 iOS/iPadOS 应用由应用保护策略管理时会出现的情况。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c854811a9deb938613af872f3cf86244ab9121b3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514653"
---
# <a name="what-to-expect-when-your-iosipados-app-is-managed-by-app-protection-policies"></a>iOS/iPadOS 应用由应用保护策略托管时会出现的情况

Intune 应用保护策略适用于用于工作或学校的应用。 这意味着，当员工和学生在个人上下文中使用应用时，他们可能不会注意到任何不同的体验。 但是，在工作或学校上下文中，他们可能会收到提示，用于提醒他们做出帐户决策、更新设置或与你联系以获得帮助。 请使用本文了解用户尝试访问和使用受 Intune 保护的应用时的体验。  

## <a name="access-apps"></a>访问应用

如果设备**未在 Intune 中注册**，则用户首次使用应用时需要重启该应用。 必须重启才能将应用保护策略应用到该应用。

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS/iPadOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

对于**在 Intune 中注册并托管**的设备，用户看到一条消息，提示应用目前已托管。

## <a name="use-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

支持多标识的应用允许使用不同的工作和个人帐户访问同一个应用。 当用户在工作或学校上下文中访问这些应用时，应用保护策略将激活，这类似于输入设备 PIN。   

在各个应用中，用户可能会体验不同的 PIN 提示，具体取决于配置此策略的方式。  例如，可以通过配置策略实现以下目的：       
* 在用户启动应用时 Microsoft Outlook 提示他们输入 PIN。 
* 在用户登录工作帐户时 OneDrive 提示他们输入 PIN。  
* 在用户访问存储在公司 OneDrive for Business 位置的文档时，Microsoft Word、PowerPoint 和 Excel 提示他们输入 PIN。  

- 详细了解支持 Intune 的[应用保护和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用。  

## <a name="manage-user-accounts-on-the-device"></a>在设备上管理用户帐户  

Intune 应用保护策略限制用户的每个应用中只能有一个托管工作或学校帐户。 应用保护策略不限制用户可以添加的非托管帐户数。   

- 如果用户尝试添加第二个托管帐户，则需要选择要使用的托管帐户。 若用户添加第二个帐户，将删除第一个帐户。
- 若将保护策略添加到用户的另一个帐户，将要求用户选择要使用哪一个托管帐户。 另一个帐户则被删除。 

一些用户不会获得切换或选择托管帐户的选项。 在以下设备中，此选项不可用：
* 由 Intune 托管  
* 由第三方企业移动性管理解决方案托管并且配置有 IntuneMAMUPN 设置 

以下示例场景说明了如何处理多个用户帐户：  

用户 A 为两家公司（**X 公司**和 **Y 公司**）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 X 公司在 Y 公司之前部署应用保护策略。    与 X 公司  关联的帐户先获取应用保护策略。 如果希望与 Y 公司关联的用户帐户由应用保护策略管理，必须删除与 X 公司关联的用户帐户，并添加与 Y 公司关联的帐户。  

## <a name="next-steps"></a>后续步骤

[Android 应用由应用保护策略托管时会出现的情况](end-user-mam-apps-android.md)
