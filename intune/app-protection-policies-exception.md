---
title: 应用的数据传输策略例外情况
titleSuffix: Microsoft Intune
description: 为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 34174568570700e0b15d5bce1bb0bf239251b577
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039148"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>如何为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

管理员可以为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况。 例外情况允许专门选择哪些非托管应用可与托管应用来回传输数据。 例外情况列表中包含的非托管应用必须受 IT 信任。 

>[!WARNING] 
> 由你负责更改数据传输例外情况策略。 添加到此策略可允许非托管应用（未由 Intune 托管的应用）访问受托管应用保护的数据。 这种对受保护数据的访问可能会导致数据安全泄漏。 只为组织必须使用的应用添加数据传输例外情况，但不支持 Intune APP（应用程序保护策略）。 此外，仅为你认为不存在数据泄漏风险的应用添加例外情况。

在 Intune 应用程序保护策略中，将“允许应用向其他应用传输数据”设置为“策略托管应用”意味着应用只能向 Intune 托管的应用传输数据。 如果需要允许向不支持 Intune 应用的特定应用传输数据，可使用“选择要免除的应用”来创建此策略的例外情况。 免除操作允许由 Intune 管理的应用程序基于 URL 协议 (iOS) 或包名称 (Android) 来调用非托管应用程序。 默认情况下，Intune 将重要的本机应用程序添加到例外情况列表中。 

> [!NOTE]
> 修改或添加数据传输策略例外不会影响其他应用保护策略，例如剪切、复制和粘贴限制。 

## <a name="ios-data-transfer-exceptions"></a>iOS 数据传输例外情况
对于针对 iOS 的策略，可以通过 URL 协议配置数据传输例外情况。 若要添加例外情况，请查看应用开发人员提供的文档，以查找有关支持的 URL 协议的信息。 有关 iOS 数据传输例外情况的其他信息，请参阅 [iOS 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)。

> [!NOTE]
> Microsoft 不提供手动查找 URL 协议来创建第三方应用程序例外情况的方法。 

## <a name="android-data-transfer-exceptions"></a>Android 数据传输例外情况
对于针对 Android 的策略，可以通过应用包名称配置数据传输例外情况。 可以查看要为其添加例外情况的应用的 Google Play 商店页，以查找应用包名称。 有关 Android 数据传输例外情况的其他信息，请参阅 [Android 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)。


>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

### <a name="example"></a>示例
通过在 MAM 数据传输策略中添加 Webex 包作为例外情况，可允许直接在 Webex 应用程序中打开托管 Outlook 电子邮件内的 Webex 链接。 其他非托管应用中将继续限制数据传输。

- iOS Webex 示例：若要豁免 Webex 应用，使其允许被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况：<code>wbx</code>
    
 - iOS 地图示例：若要豁免本机地图应用，使其允许被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况：<code>maps</code>

- Android Webex 示例：若要豁免 Webex 应用，使其允许被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况：<code>com.cisco.webex.meetings</code>
    
- Android SMS 示例：若要豁免本机 SMS 应用，以允许其在不同的消息传送应用和 Android 设备中被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况： 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>后续步骤

- [创建和部署应用保护策略](app-protection-policies.md)
- [iOS 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)
