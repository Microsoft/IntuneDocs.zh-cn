---
title: 具有应用保护策略的 Android 应用
description: 本主题描述应用由应用保护策略托管时会出现的情况。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3e479ae9e3cd2caf6b893cb75f9af8fde2340f0c
ms.sourcegitcommit: d786eb18147a12fbc8cb97a157467f88591f1bc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37133980"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Android 应用由应用保护策略托管时会出现的情况

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

本文介绍启用了应用保护策略的应用的用户体验。 仅在工作环境中使用应用时，应用保护策略才适用：例如，用户使用工作帐户访问应用，或访问 OneDrive for Business 位置存储的文件时。

##  <a name="access-apps"></a>访问应用

Android 设备上与应用保护策略关联的所有应用都需要公司门户应用。

对于未在 Intune 中注册的设备，必须在设备上安装公司门户应用。 但是，用户不必启动或登录到公司门户应用，即可使用由应用保护策略托管的应用。

公司门户应用是 Intune 共享安全位置中的数据的一种方法。 因此，即使未在 Intune 中注册设备，与应用保护策略关联的所有应用也需要公司门户应用。


##  <a name="use-apps-with-multi-identity-support"></a>使用具有多身份支持的应用

应用保护策略仅用于工作环境。 因此，应用的行为可能有所不同，具体取决于是工作环境还是个人环境。

例如，用户访问工作数据时会遇到 PIN 提示。 对于 **Outlook 应用**，在用户启动应用时提示他们输入 PIN。 对于 **OneDrive 应用**，在用户键入工作帐户时提示他们输入 PIN。 对于 Microsoft **Word**、**PowerPoint** 和 **Excel**，在用户访问存储在公司 OneDrive for Business 位置的文档时提示他们输入 PIN。

##  <a name="manage-user-accounts-on-the-device"></a>在设备上管理用户帐户

多标识应用程序允许用户添加多个帐户。  Intune 应用仅支持一个托管帐户。  Intune 应用不限制非托管帐户的数量。

当应用程序中存在托管帐户时：
*   如果用户尝试添加第二个托管帐户，则需要选择要使用的托管帐户。  另一个帐户则被删除。
*   如果 IT 管理员将一个策略添加到第二个现有帐户，用户需要选择要使用的托管帐户。  另一个帐户则被删除。

阅读以下示例场景以更深入地了解如何处理多个用户帐户。

用户 A 为两家公司（**X 公司**和 **Y 公司**）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司****之前**部署应用保护策略。与 X 公司关联的帐户会获得应用保护策略，而与 Y 公司关联的帐户不会。如果希望与 Y 公司关联的用户帐户由应用保护策略管理，必须删除与 X 公司关联的用户帐户，并添加与 Y 公司关联的帐户。
### <a name="add-a-second-account"></a>添加第二个帐户
####  <a name="android"></a>Android
如果使用 Android 设备，则可能会看到具有删除现有帐户并添加新帐户指令的阻止消息。  若要删除现有帐户，请转到“设置”&gt;“常规”&gt;应用程序管理器”&gt;“公司门户”， 然后选择“清除数据”。

![错误消息以及删除操作的指令的屏幕截图](./media/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>使用 Azure 信息保护应用查看媒体文件
若要在 Android 设备上查看公司 AV、PDF 和图像文件，请使用 [Azure 信息保护应用](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)（以前称为 Rights Management 共享应用）。

从 Google Play 商店下载此应用。  

支持以下文件类型：

* **音频：** AAC LC、HE-AACv1 (AAC+)、HE-AACv2（增强型 AAC+）、AAC ELD（增强型低延迟 AAC）、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **视频：** H.263、H.264 AVC、MPEG-4 SP、VP8。
* **图像：**.jpg、.pjpg、.png、.ppng、.bmp、.pbmp、.gif、.pgif，.jpeg、.pjpeg。
* **文档：** PDF、PPDF


|**pfile**|
|----|
|Pfile 是一种用于受保护文件的通用“包装”格式，它可封装加密内容和 Azure 信息保护许可证。 它可以用于保护任何文件类型。|

## <a name="next-steps"></a>后续步骤
[iOS 应用由应用保护策略托管时会出现的情况](end-user-mam-apps-ios.md)
