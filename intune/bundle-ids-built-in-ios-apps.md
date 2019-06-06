---
title: Microsoft Intune 中内置应用的 iOS 程序包 ID - Azure | Microsoft Docs
titleSuffix: ''
description: 请参阅内置 iOS 应用的程序包 ID 列表。 使用这些程序包 ID，可以显示允许 Microsoft Intune 中的设备配置文件和策略中的应用。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ff5b411f14fef4ad294b0dd8b265680fd67df08
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402765"
---
# <a name="bundle-ids-for-built-in-ios-apps-you-can-use-in-intune"></a>可以在 Intune 中使用的内置 iOS 应用的程序包 ID

在 iOS 设备上配置功能时，还可以在 iOS 设备上添加内置应用。 本文列出了一些常见内置 iOS 应用的程序包 ID。 若要查找其他应用的捆绑 ID，请联系软件供应商。 请参阅 Apple [iOS 捆绑包 ID](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web)列表（打开 Apple 网站）。

## <a name="bundle-ids"></a>程序包 ID

| 捆绑 ID                   | 应用名称     | 发布者 |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | 计算器   | Apple     |
| com.apple.mobilecal         | 日历     | Apple     |
| com.apple.camera            | 照相机       | Apple     |
| com.apple.mobiletimer       | 时钟        | Apple     |
| com.apple.compass           | 指南针      | Apple     |
| com.apple.MobileAddressBook | 联系人     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | 文件        | Apple     |
| com.apple.mobileme.fmf1     | 查找好友 | Apple     |
| com.apple.mobileme.fmip1    | 查找 iPhone  | Apple     |
| com.apple.gamecenter        | 游戏中心  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | 运行状况       | Apple     |
| com.apple.Home              | 住宅         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes 商店 | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | 映射         | Apple     |
| com.apple.MobileSMS         | 消息     | Apple     |
| com.apple.Music             | 音乐        | Apple     |
| com.apple.news              | 新闻         | Apple     |
| com.apple.mobilenotes       | 注意        | Apple     |
| com.apple.Numbers           | 数字      | Apple     |
| com.apple.Pages             | 页面        | Apple     |
| com.apple.mobilephone       | 电话        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | 照片       | Apple     |
| com.apple.podcasts          | 播客     | Apple     |
| com.apple.reminders         | 提醒    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | 设置     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | 股票       | Apple     |
| com.apple.tips              | 提示         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | 视频       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | 电子钱包       | Apple     |
| com.apple.Bridge            | 观看        | Apple     |
| com.apple.weather           | 天气      | Apple     |

## <a name="next-steps"></a>后续步骤

这些程序包 ID 用于配置[设备功能](ios-device-features-settings.md)以及[允许或限制 iOS 设备上的某些设置](device-restrictions-ios.md)。
