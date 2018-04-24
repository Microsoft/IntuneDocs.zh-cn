---
title: 创建适用于 iOS 设备的应用通知 - Microsoft Intune - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加或创建适用于 iOS 设备的应用通知。 选择用于发送通知、在锁屏界面上配置通知设置、启用声音、选择警报类型和添加标记的应用。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43068163c15c0588a8a6ef745d5b191f4547a94d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>在 iOS 设备的 Intune 中配置应用通知设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

配置 iOS 设备上安装的应用发送通知的方式。 这些设置支持运行 iOS 9.3 及更高版本的已监督设备。

## <a name="add-the-app-notification"></a>添加应用通知

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 在 iOS 或 macOS 配置文件中选择“设备功能”。 [iOS 或 macOS 设备功能](device-features-configure.md)列出了配置文件的创建步骤。
3. 选择“应用通知(仅限监督的设备)”，然后选择“添加”：![在 Intune 的 iOS 或 macOS 配置文件中添加应用通知](./media/ios-macos-app-notifications.png)
4. 输入以下属性：

   - **应用捆绑 ID** - 输入要配置的应用的“应用捆绑 ID”。 相关帮助，可参考本文中的**适用于内置 iOS 应用的捆绑 ID 引用**。
   - **应用名称** - 输入要配置的应用的名称。 该名称不在此设备上显示，并用于帮助你识别列表中的应用。
   - **发行者** - 输入要配置的应用的发行者。 发布者名称不在此设备上显示，仅用于帮助识别列表中的应用。
   - **通知** - 启用或禁用应用向设备发送通知。 如果禁用此设置，还将禁用以下设置。
     - **在通知中心中显示** - 启用此设置以允许应用在设备通知中心中显示通知。
     - **在锁定屏幕中显示** - 启用此设置以在设备锁定屏幕上看到应用的通知。
     - **警报类型** - 选择希望从解除锁定设备看到的通知类型：
       - **无** - 不显示任何通知。
       - **横幅** - 呈现通知的简要显示的横幅。
       - **模式** - 显示通知，并且用户必须先手动消除通知，才能继续使用设备。
     - **应用图标上的徽章** - 启用此设置可将一个徽章添加到应用图标，以指示应用发送通知。
     - **声音** - 启用此设置可在通知送达时播放声音。

5. 继续添加所需数量的应用。 应用添加完毕后，选择“确定”。
6. 选择“创建”以保存配置文件。

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>内置 iOS 应用的捆绑 ID 引用

下表显示了一些常见的内置 iOS 应用的捆绑 ID。 要查找其他应用的捆绑 ID，请与软件供应商联系。

|||
|-|-|
|应用程序名称|BundleID|
|App Store|com.apple.AppStore|
|计算器|com.apple.calculator|
|日历|com.apple.mobilecal|
|照相机|com.apple.camera|
|时钟|com.apple.mobiletimer|
|指南针|com.apple.compass|
|联系人|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|查找好友|com.apple.mobileme.fmf1|
|查找 iPhone|com.apple.mobileme.fmip1|
|游戏中心|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|运行状况|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes 商店|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|映射|com.apple.Maps|
|消息|com.apple.MobileSMS|
|音乐|com.apple.Music|
|新闻|com.apple.news|
|注释|com.apple.mobilenotes|
|数字|com.apple.Numbers|
|页面|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|照片|com.apple.mobileslideshow|
|播客|com.apple.podcasts|
|提醒|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|设置|com.apple.Preferences|
|股票|com.apple.stocks|
|提示|com.apple.tips|
|视频|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|电子钱包|com.apple.Passbook|
|观看|com.apple.Bridge|
|天气|com.apple.weather|

## <a name="next-steps"></a>后续步骤

将设备配置文件分配到所选的组。 相关步骤，请参见[如何分配设备配置文件](device-profile-assign.md)。