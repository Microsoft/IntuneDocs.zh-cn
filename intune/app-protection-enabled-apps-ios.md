---
title: 具有应用保护策略的 iOS 应用
titlesuffix: Microsoft Intune
description: 了解 iOS 应用具有保护策略时会出现的情况。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 667d5df5d53a9248137274cf7abe5b7fde5bf8bb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181932"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 应用由应用保护策略管理时会出现的情况

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解具有应用保护策略的 iOS 应用的用户体验。 仅当在工作环境中使用应用时，应用保护策略才适用。 例如，使用工作帐户访问应用，或访问公司 OneDrive 位置中存储的文件时。
##  <a name="accessing-apps"></a>访问应用

如果设备**未在 Intune 中注册**，则用户首次使用应用时需要重启该应用。  必须重启才能将应用保护策略应用到该应用。 以下屏幕截图使用 Skype 应用对此进行解释：


![显示 PIN 提示的 iOS 设备的屏幕截图](./media/ios-pin-prompt.png)

对于**在 Intune 中注册并托管**的设备，用户可看到一条消息，提示应用目前已托管：

![iOS 设备的屏幕截图，其中 PIN 提示显示“由公司托管”消息](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

应用保护策略仅在用户尝试访问工作相关数据时生效。 如果用户尝试访问供个人使用的应用，可能会看到不同的行为。 此策略也不适用于尚未保存的新内容。 只有将新内容保存到公司位置（如 SharePoint 或 OneDrive for Business）后，才会将其视为公司信息。

对于支持多身份的应用，Intune 仅在用户访问工作数据时才应用应用保护策略。  例如，用户可能会收到 PIN 提示。  在 Outlook 应用中，用户启动应用时会出现提示。 在 OneDrive 应用中，用户键入工作帐户时会出现提示。  在 Microsoft Word、PowerPoint 和 Excel 中，用户访问公司 OneDrive 文档时会出现提示。
##  <a name="managing-user-accounts-on-the-device"></a>在设备上管理用户帐户

Intune 仅支持对于每个设备，将应用保护策略部署到一个用户帐户。

* 根据所使用的应用，第二个用户可能会也可能不会在设备上受阻。 但是在所有情况下，只有获取应用保护策略的第一个用户才会受该策略影响。
  * Microsoft Word、Excel 和 PowerPoint 不会阻止其他用户帐户的访问。 但是，该用户帐户不会受应用保护策略影响。

  * 对于“OneDrive 和 Outlook 应用”，只能使用一个工作帐户。  将阻止在这些应用中添加多个工作帐户。  但是，可以删除设备中的一个用户，然后向该设备添加其他用户。

* 在部署应用保护策略之前，一个设备可以拥有多个现有用户帐户。 在这种情况下，应用保护策略部署到的第一个帐户由 Intune 应用保护策略托管。


阅读以下示例场景，了解 Intune 如何处理多用户帐户。

用户 A 为两家公司（X 公司和 Y 公司）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司** **之前**部署应用保护策略。与**X 公司**关联的帐户会获得应用保护策略，而与 Y 公司关联的帐户不会。如果希望应用保护策略托管 Y 公司用户帐户，用户 A 必须删除 X 公司用户帐户。
### <a name="adding-a-second-account"></a>添加第二个帐户

如果使用 iOS 设备，则在同一设备上尝试添加第二个工作帐户时，可能会看到拦截消息。  随即显示帐户，可从中选择要删除的帐户。

![包含阻止消息以及“是”和“否”选项的对话框的屏幕截图](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>后续步骤
[Android 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 创建和部署应用保护策略](app-protection-policies.md)
