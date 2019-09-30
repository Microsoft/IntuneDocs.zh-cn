---
title: 具有应用保护策略的 iOS 应用
description: 本主题描述 iOS 应用由应用保护策略托管时会出现的情况。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4039c9e3ae53d8db8ee282f802cd86149b40021e
ms.sourcegitcommit: 18be0ccc6e51073af32c44abeba421d69a5ae21a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "71239762"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 应用由应用保护策略管理时会出现的情况

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

 本主题介绍使用已应用了应用保护策略的应用时的用户体验。 仅在工作环境中使用应用时，应用保护策略才适用；例如，用户使用工作帐户访问应用，或访问公司 OneDrive 企业版位置存储的文件时。

## <a name="access-apps"></a>访问应用

如果设备**未在 Intune 中注册**，则用户首次使用应用时需要重启该应用。 必须重启才能将应用保护策略应用到该应用。

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

对于**在 Intune 中注册并托管**的设备，用户看到一条消息，提示应用目前已托管。

## <a name="use-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

支持多身份的应用允许用户使用不同的帐户（工作和个人）访问相同的应用，但仅当在工作环境中使用这些应用时，才会应用应用保护策略。  

例如，用户访问工作数据时会遇到 PIN 提示。 对于 **Outlook 应用**，在用户启动应用时提示他们输入 PIN。 对于 **OneDrive 应用**，在用户键入工作帐户时提示他们输入 PIN。  对于 Microsoft **Word**、**PowerPoint** 和 **Excel**，在用户访问存储在公司 OneDrive for Business 位置的文档时提示他们输入 PIN。

- 详细了解支持 Intune 的[应用保护和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用。

应用保护策略仅用于工作环境。 因此，应用的行为可能有所不同，具体取决于是工作环境还是个人环境。

## <a name="manage-user-accounts-on-the-device"></a>在设备上管理用户帐户

多标识应用程序允许用户添加多个帐户。  Intune 应用仅支持一个托管帐户。  Intune 应用不限制非托管帐户的数量。

当应用程序中存在托管帐户时：
* 如果用户尝试添加第二个托管帐户，则需要选择要使用的托管帐户。  另一个帐户则被删除。
* 如果 IT 管理员将一个策略添加到第二个现有帐户，用户需要选择要使用的托管帐户。  另一个帐户则被删除。

阅读以下示例场景以更深入地了解如何处理多个用户帐户。

用户 A 为两家公司（**X 公司**和 **Y 公司**）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司** **之前**部署应用保护策略。与 X 公司关联的帐户先获取应用保护策略。 如果希望与 Y 公司关联的用户帐户由应用保护策略管理，必须删除与 X 公司关联的用户帐户，并添加与 Y 公司关联的帐户。

### <a name="add-a-second-account"></a>添加第二个帐户

如果使用 iOS 设备，则在同一设备上尝试添加第二个工作帐户时，可能会看到拦截消息。 随即显示帐户，可从中选择要删除的帐户。

## <a name="next-steps"></a>后续步骤
[Android 应用由应用保护策略托管时会出现的情况](end-user-mam-apps-android.md)
