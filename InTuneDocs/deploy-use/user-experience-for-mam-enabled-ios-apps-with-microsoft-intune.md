---
title: "具有应用保护策略的 iOS 应用 | Microsoft Docs"
description: "本主题描述 iOS 应用由应用保护策略托管时会出现的情况。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 665d3347636d5ec0c698ffb93b768028c9d59ce3
ms.openlocfilehash: fba18027039a0e49c5301f9d1a16947e97408034
ms.lasthandoff: 03/07/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 应用由应用保护策略托管时会出现的情况

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 本主题描述具有应用保护策略的应用的用户体验。 仅在工作环境中使用应用时，应用保护策略才适用；例如，用户使用工作帐户访问应用，或访问公司 OneDrive 企业版位置存储的文件时。

##  <a name="access-apps"></a>访问应用

如果设备**未在 Intune 中注册**，则用户首次使用应用时需要重启该应用。  必须重启才能将应用保护策略应用到该应用。 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

对于**在 Intune 中注册并托管**的设备，用户看到一条消息，提示应用目前已托管。

##  <a name="use-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

应用保护策略仅用于工作环境。 因此，应用的行为可能有所不同，具体取决于是工作环境还是个人环境。

 例如，用户访问工作数据时会遇到 PIN 提示。 对于 **Outlook 应用**，在用户启动应用时提示他们输入 PIN。 对于 **OneDrive 应用**，在用户键入工作帐户时提示他们输入 PIN。  对于 Microsoft **Word**、**PowerPoint** 和 **Excel**，在用户访问存储在公司 OneDrive for Business 位置的文档时提示他们输入 PIN。

##  <a name="manage-user-accounts-on-the-device"></a>在设备上管理用户帐户

Intune 仅支持将应用保护策略部署到每个设备的一个用户帐户。

* 根据所使用的应用，第二个用户可能会在设备上受阻。 但是在所有情况下，只有获取应用保护策略的第一个用户才会受该策略影响。
  * “Microsoft Word”、“Excel”和“PowerPoint”不会阻止第二个用户帐户，但第二个用户帐户不受应用保护策略影响。  

  * 对于 **OneDrive** 和 **Outlook** 应用，只能使用一个工作帐户。 无法为这些应用添加多个工作帐户。 但是，你可以在设备上删除用户并添加其他用户。

* 如果设备在部署应用保护策略之前已有多个用户帐户，则最先部署应用保护策略的帐户由 Intune 应用保护策略进行管理。


阅读以下示例场景以更深入地了解如何处理多个用户帐户。

用户 A 为两家公司（**X 公司**和 **Y 公司**）工作。用户 A 对于每家公司具有&1; 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司****之前**部署应用保护策略。与 **X 公司**关联的帐户会获得应用保护策略，而与 Y 公司关联的帐户不会。如果希望与 Y 公司关联的用户帐户由应用保护策略管理，必须删除与 X 公司关联的用户帐户。

### <a name="add-a-second-account"></a>添加第二个帐户

如果使用 iOS 设备，则在同一设备上尝试添加第二个工作帐户时，可能会看到拦截消息。 随即显示帐户，可从中选择要删除的帐户。

## <a name="next-steps"></a>后续步骤
[Android 应用由应用保护策略托管时会出现的情况](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 创建和部署移动应用管理策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

