---
title: Android 用户如何获取其应用
description: 使 Android 应用可供最终用户使用的方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 960c440372613fed2c92ce00c604d97e1f122e8f
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71239818"
---
# <a name="how-your-android-users-get-their-apps"></a>Android 用户如何获取其应用

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

使用本文可了解 Android 最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。 该信息可能因设备类型（本机 Android 设备或 Samsung Knox 标准版设备）而异。

## <a name="native-non-samsung-knox-standard-android-devices"></a>本机（非 Samsung Knox 标准）Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 此时将出现一条通知，用户需要点击该通知以开始安装。 安装成功后，通知即会消失。 | 用户在公司门户中点击应用，并转到 Play Store 中的应用页。 他们可以在那里开始安装。|
| Required apps      | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击通知以开始安装。 安装成功后，通知即会消失。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页。 他们可以在那里开始安装。 安装成功后，通知即会消失。 |

最终用户需要允许来自未知源的安装才能安装 [LOB 应用](lob-apps-android.md)。 此设置通常位于两个位置：

* **Android 7.1.2 及更低版本**：“设置” > “安全性” > “未知源”
* **Android 8.0 及更高版本**：“设置” > “应用和通知” > “特殊应用访问” > “安装未知应用” > “公司门户” > “允许来自此源”

在这种情况下，公司门户应用将通知最终用户，并将最终用户直接引导至相应设置。 

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox 标准版 Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 应用安装无需进一步的用户干预。 | 用户在公司门户中点击应用，并转到 Play Store 中的应用页。 他们可以在那里开始安装。|
| Required apps      | 应用安装无需任何用户干预。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页。 他们可以在那里开始安装。 安装成功后，通知即会消失。 |

应用可以是托管应用，也可以是非托管应用，如下所述。 托管应用的过程对于所有类型的 Android 设备都是相同的。

**托管应用** - 这些是通过策略管理的应用。 它们已由 Intune“包装”或通过 Intune App SDK 生成。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 这些不是通过策略管理的应用。 它们未由 Intune 包装或不包含 Intune App SDK。 应用程序策略不能应用于这些应用。

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>带有 Zebra Mobility Extensions 的 Zebra 设备

Intune 使用 Zebra Mobility Extensions (MX) 工具包以无提示方式在设备管理员管理的 Zebra 设备上安装应用。 此功能可让你在无需用户干预的情况下在 Zebra 设备上部署和更新应用。 如果设备上的 MX 版本为 4.2 或更早版本，则不会以无提示方式安装应用。 有关详细信息，请参阅 Zebra 网站上的[完整 MX 功能矩阵](http://techdocs.zebra.com/mx/compatibility/)。

必须从设备上的公共位置安装部署到 Zebra 设备的 LOB 应用。 如果其他应用和服务还有权访问设备上的公共存储，则可以访问 .apk 应用包。 通常，此访问在应用下载完成后和安装开始之间显示的一个小窗口。 此窗口可能导致计时攻击。 例如，可以在此窗口中更改 .apk 包。 Intune 最大程度地减少了 .apk 在公共存储中花费的时间，并且不允许安装未签名的应用。 为了尽量降低安全风险，请确保上传的 .apk 文件不包含敏感信息。

## <a name="see-also"></a>另请参阅

[使用 Microsoft Intune 添加应用](apps-add.md)

[iOS 用户如何获取其应用](end-user-apps-ios.md)

[Windows 用户如何获取其应用](end-user-apps-windows.md)
