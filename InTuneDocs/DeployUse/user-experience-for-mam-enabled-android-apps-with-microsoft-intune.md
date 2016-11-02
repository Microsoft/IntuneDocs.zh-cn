---
title: "用于 MAM 策略的 Android 应用 | Microsoft Intune"
description: "本主题介绍当你的应用由移动应用管理策略托管时会出现的情况。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# Android 应用由 MAM 策略托管时会出现的情况
本主题描述具有 MAM 策略的应用的用户体验。 仅当在工作环境中使用应用（例如使用工作帐户访问应用，或访问存储在公司 OneDrive for Business 位置的文件）时，才应用移动应用管理 (MAM) 策略。
##  访问应用

Android 设备上与 MAM 策略关联的所有应用都需要公司门户应用。

对于未在 Intune 中注册的设备，必须在设备上安装公司门户应用。 但是，用户不必启动或登录到公司门户应用，即可使用由 MAM 策略托管的应用。
Intune 可通过公司门户应用在安全位置共享数据，因此，即使该设备未在 Intune 中注册，也需要使用该应用。


##  使用具有多身份支持的应用

使用应用时，仅在工作环境中应用 MAM 策略仅，因此根据工作或个人环境，应用可能有不同的行为。

对于支持多身份的应用，仅当最终用户在工作环境中使用该应用时，Intune 才应用 MAM 策略。  例如，最终用户访问工作数据时将收到 PIN 提示。  对于 **Outlook 应用**，将在最终用户启动应用时提示其输入 PIN。 对于 **OneDrive 应用**，将在最终用户键入工作帐户时进行提示。  对于 Microsoft **Word**、**PowerPoint*和 **Excel**，将在最终用户访问存储在公司 OneDrive for Business 位置的文档时进行提示。
##  在设备上管理用户帐户

Intune 仅支持对于每个设备，将 MAM 策略部署到一个用户帐户。

* 根据所使用的应用，第二个用户可能会也可能不会在设备上受阻。 但是在所有情况下，只有获取 MAM 策略的第一个用户才会受该策略影响。

  * “Microsoft Word”、“Excel”和“PowerPoint”不会阻止第二个用户帐户，但第二个用户帐户不受 MAM 策略影响。

  * 对于“OneDrive 和 Outlook 应用”，只能使用一个工作帐户。  将阻止在这些应用中添加多个工作帐户。  但是，你可以在设备上删除用户并添加其他用户。


* 如果设备在部署 MAM 策略之前具有现有的多个用户帐户，则 MAM 策略部署到的帐户首先由 Intune MAM 策略管理。


阅读以下示例方案以更深入地了解如何处理多个用户帐户。

用户 A 为两家公司（“X 公司”和“Y 公司”）工资。用户 A 对于每家公司具有一个工作帐户，它们都使用 Intune 来部署 MAM 策略。 **X 公司**在**Y 公司****之前**部署 MAM 策略。与“X 公司”关联的帐户会获得 MAM 策略，而与 Y 公司关联的帐户不会。如果你希望与 Y 公司关联的用户帐户通过 MAM 策略管理，则必须删除与 X 公司关联的用户帐户。
### 添加第二个帐户
####  Android
如果使用 Android 设备，则可能会看到具有删除现有帐户并添加新帐户指令的阻止消息。  若要删除现有帐户，请转到“设置”&gt;“常规”&gt;应用程序管理器”&gt;“公司门户”，然后选择“清除数据”。

![错误消息以及删除操作的指令的屏幕截图](../media/AppManagement/Android_SwitchUser.png)

##  通过 Azure 信息保护应用（以前被称为 Rights Management 共享应用）查看媒体文件
若要在 Android 设备上查看公司 AV、PDF 和图像文件，请使用 [Azure 信息保护应用](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)。

从 Google Play 商店下载此应用。  

支持以下文件类型：

* **音频：**AAC LC、HE-AACv1 (AAC+)、HE-AACv2（增强型 AAC+）、AAC ELD（增强型低延迟 AAC）、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **视频：**H.263、H.264 AVC、MPEG-4 SP、VP8。
* **图像：**jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif，jpeg、pjpeg。
* **文档：**PDF、PPDF

------------
|**pfile**|**text**|
|----|----|
|Pfile 是一种用于受保护文件的通用“包装”格式，它可封装加密内容和 Azure 信息保护许可证，还可用于保护任何文件类型。|即使是在受保护的情况下，也可在应用中打开文本文件（包括 XML 和 CSV 等）进行查看。 文件类型：txt、ptxt、csv、pcsv、log、plog、xml、pxml。|
---------------
## 后续步骤
[iOS 应用由 MAM 策略托管时会出现的情况](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### 另请参阅
[使用 Microsoft Intune 创建和部署移动应用管理策略](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


