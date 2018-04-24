---
title: 具有应用保护策略的 Android 应用
titlesuffix: Microsoft Intune
description: 了解 Android 应用具有保护策略时会出现的情况。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 450bcd9c807bdfae16e9c2fa1eb813b00444df65
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Android 应用由应用保护策略托管时会出现的情况 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解 Android 应用具有应用保护策略时会出现的情况。 仅当在工作环境中使用应用时，应用保护策略才适用。 例如，使用工作帐户访问应用，或访问公司 OneDrive 位置中存储的文件时。
##  <a name="accessing-apps"></a>访问应用

Android 设备上具有应用保护策略的所有应用都需要公司门户应用。

在所有未在 Intune 中注册的设备上安装公司门户。 用户无需登录公司门户应用即可使用具有应用保护策略的应用。
通过公司门户应用，可在安全位置共享数据。 因此，即使是未注册的设备，也需要公司门户应用。


##  <a name="using-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

应用保护策略仅在用户尝试访问工作相关数据时生效。  如果用户访问供个人使用的应用，可能会看到不同的行为。

某些应用支持多身份。 在这种情况下，Intune 仅在用户访问工作数据时才应用应用保护策略。  例如，用户可能会收到 PIN 提示。  在 Outlook 应用中，用户启动应用时会出现提示。 在 OneDrive 应用中，用户键入工作帐户时会出现提示。  在 Microsoft Word、PowerPoint 和 Excel 中，用户访问公司 OneDrive 文档时会出现提示。
##  <a name="managing-user-accounts-on-the-device"></a>在设备上管理用户帐户

Intune 支持将应用保护策略部署到每个设备的一个用户帐户。

* 根据所使用的应用，第二个用户可能会也可能不会在设备上受阻。 但是在所有情况下，只有获取应用保护策略的第一个用户才会受该策略影响。

  * Microsoft Word、Excel 和 PowerPoint 不会阻止其他用户帐户的访问。 但是，该用户帐户不会受应用保护策略影响。

  * 对于“OneDrive 和 Outlook 应用”，只能使用一个工作帐户。  将阻止在这些应用中添加多个工作帐户。  但是，可以删除设备中的一个用户，然后向该设备添加其他用户。


* 在部署应用保护策略之前，一个设备可以有多个现有用户帐户。 在这种情况下，应用保护策略部署到的第一个帐户由 Intune 应用保护策略托管。


阅读以下示例场景，了解 Intune 如何处理多用户帐户。

用户 A 为两家公司（X 公司和 Y 公司）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司****之前**部署应用保护策略。与“X 公司”关联的帐户会获得应用保护策略，而与 Y 公司关联的帐户不会。如果希望应用保护策略托管 Y 公司用户帐户，用户 A 必须删除 X 公司用户帐户。
### <a name="adding-a-second-account"></a>添加第二个帐户
####  <a name="android"></a>Android
系统可能会提示删除现有帐户并添加新帐户。  要删除现有帐户，请转到“设置”&gt;“常规”&gt;“应用程序管理器”&gt;“公司门户”。然后选择“清除数据”。

![错误消息以及删除操作的指令的屏幕截图](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>通过 Azure 信息保护应用（以前被称为 Rights Management 共享应用）查看媒体文件
若要在 Android 设备上查看公司 AV、PDF 和图像文件，请使用 [Azure 信息保护应用](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)。

从 Google Play 商店下载此应用。  

支持以下文件类型：

* **音频：**AAC LC、HE-AACv1 (AAC+)、HE-AACv2（增强型 AAC+）、AAC ELD（增强型低延迟 AAC）、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **视频：**H.263、H.264 AVC、MPEG-4 SP、VP8。
* **图像：**jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif，jpeg、pjpeg。
* **文档：**PDF、PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>文本</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile 是一种用于受保护文件的通用“包装器”格式。 它可封装加密内容和 Azure 信息保护许可证。 它可以用于保护任何文件类型。 | 即使是在受保护的情况下，也可在应用中打开文本文件（包括 XML 和 CSV 等）进行查看。 文件类型：txt、ptxt、csv、pcsv、log、plog、xml、pxml。 |

---------------
## <a name="next-steps"></a>后续步骤
[iOS 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 创建和部署应用保护策略](app-protection-policies.md)
