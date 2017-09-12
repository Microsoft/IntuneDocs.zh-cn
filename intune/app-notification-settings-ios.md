---
title: "适用于 iOS 设备的 Intune 应用通知设置"
titlesuffix: Azure portal
description: "了解可用来控制 iOS 设备上的应用通知的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cb9c5b407ce21604a677e207be573428a8728e06
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="intune-app-notifications-settings-for-ios-devices"></a>适用于 iOS 设备的 Intune 应用通知设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

允许你配置在设备上安装的应用如何发送通知。 这些设置支持运行 iOS 9.3 及更高版本的已监督设备。

## <a name="configure-settings"></a>配置设置

1. 在设备功能边栏选项卡上，选择“应用通知(仅已监督设备)”。
2. 在“应用通知”边栏选项卡上，选择“添加”，然后配置以下值：
    - **应用捆绑 ID** - 输入想要配置的应用的**应用捆绑 ID**。 请参阅本主题的稍后部分中介绍的**适用于内置 iOS 应用的捆绑 ID 引用**，了解帮助信息。
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
3. 继续添加所需数量的应用。 完成后，请选择“确定”。
4. 选择“确定”，直到返回到“创建配置文件”边栏选项卡，然后选择“创建”。 


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>内置 iOS 应用的捆绑 ID 引用

此列表显示了一些常见的内置 iOS 应用的捆绑 ID。 若要查找其他应用的捆绑 ID，请联系软件供应商。 

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
|注意|com.apple.mobilenotes|
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

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
