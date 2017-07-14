---
title: "具有应用保护策略的 Android 应用"
description: "本主题描述应用由应用保护策略托管时会出现的情况。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 030e17a9f28a9476c82e89d4dd26151a2d3cb953
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2017
---
# Android 应用由应用保护策略托管时会出现的情况
<a id="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

本主题描述具有应用保护策略的应用的用户体验。 仅在工作环境中使用应用时，应用保护策略才适用：例如，用户使用工作帐户访问应用，或访问公司 OneDrive 企业版位置存储的文件时。
##  访问应用
<a id="access-apps" class="xliff"></a>

Android 设备上与应用保护策略关联的所有应用都需要公司门户应用。

对于未在 Intune 中注册的设备，必须在设备上安装公司门户应用。 但是，用户不必启动或登录到公司门户应用，即可使用由应用保护策略托管的应用。

公司门户应用是 Intune 共享安全位置中的数据的一种方法。 因此，即使未在 Intune 中注册设备，与应用保护策略关联的所有应用也需要公司门户应用。


##  使用具有多身份支持的应用
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

应用保护策略仅用于工作环境。 因此，应用的行为可能有所不同，具体取决于是工作环境还是个人环境。

例如，用户访问工作数据时会遇到 PIN 提示。 对于 **Outlook 应用**，在用户启动应用时提示他们输入 PIN。 对于 **OneDrive 应用**，在用户键入工作帐户时提示他们输入 PIN。 对于 Microsoft **Word**、**PowerPoint** 和 **Excel**，在用户访问存储在公司 OneDrive for Business 位置的文档时提示他们输入 PIN。

##  在设备上管理用户帐户
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

Intune 仅支持将应用保护策略部署到每个设备的一个用户帐户。

* 根据所使用的应用，第二个用户可能会在设备上受阻。 但是在所有情况下，只有获取应用保护策略的第一个用户才会受该策略影响。

  * Microsoft Word、Excel 和 PowerPoint 不会阻止第二个用户帐户，但第二个用户帐户不受应用保护策略影响。

  * 对于 **OneDrive** 和 **Outlook** 应用，只能使用一个工作帐户。  无法为这些应用添加多个工作帐户。  但是，你可以在设备上删除用户并添加其他用户。


* 如果设备在部署应用保护策略之前已有多个用户帐户，则最先部署应用保护策略的帐户由 Intune 应用保护策略进行管理。


阅读以下示例场景以更深入地了解如何处理多个用户帐户。

用户 A 为两家公司（**X 公司**和 **Y 公司**）工作。用户 A 对于每家公司具有 1 个工作帐户，它们都使用 Intune 来部署应用保护策略。 **X 公司**在 **Y 公司****之前**部署应用保护策略。与 **X 公司**关联的帐户会获得应用保护策略，而与 Y 公司关联的帐户不会。如果希望与 Y 公司关联的用户帐户由应用保护策略管理，必须删除与 X 公司关联的用户帐户。
### 添加第二个帐户
<a id="add-a-second-account" class="xliff"></a>
####  Android
<a id="android" class="xliff"></a>
如果使用 Android 设备，则可能会看到具有删除现有帐户并添加新帐户指令的阻止消息。  若要删除现有帐户，请转到“设置”&gt;“常规”&gt;应用程序管理器”&gt;“公司门户”， 然后选择“清除数据”。

![错误消息以及删除操作的指令的屏幕截图](./media/Android_SwitchUser.png)

##  使用 Azure 信息保护应用查看媒体文件
<a id="view-media-files-with-the-azure-information-protection-app" class="xliff"></a>
若要在 Android 设备上查看公司 AV、PDF 和图像文件，请使用 [Azure 信息保护应用](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)（以前称为 Rights Management 共享应用）。

从 Google Play 商店下载此应用。  

支持以下文件类型：

* **音频：**AAC LC、HE-AACv1 (AAC+)、HE-AACv2（增强型 AAC+）、AAC ELD（增强型低延迟 AAC）、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **视频：**H.263、H.264 AVC、MPEG-4 SP、VP8。
* **图像：**.jpg、.pjpg、.png、.ppng、.bmp、.pbmp、.gif、.pgif，.jpeg、.pjpeg。
* **文档：**PDF、PPDF


|**pfile**|**文本**|
|----|----|
|Pfile 是一种用于受保护文件的通用“包装”格式，它可封装加密内容和 Azure 信息保护许可证。 它可以用于保护任何文件类型。|即使是在受保护的情况下，也可在应用中打开文本文件（包括 XML 和 CSV 等）进行查看。 文件类型：.txt、.ptxt、.csv、.pcsv、.log、.plog、.xml、.pxml。|

## 后续步骤
<a id="next-steps" class="xliff"></a>
[iOS 应用由应用保护策略托管时会出现的情况](end-user-mam-apps-ios.md)
