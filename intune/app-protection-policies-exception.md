---
title: 应用的数据传输策略例外情况
titleSuffix: Microsoft Intune
description: 为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1910334093a416933912c9cdeedac85e36d66e92
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>如何为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

管理员可以为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况。 例外情况允许专门选择哪些非托管应用可与托管应用来回传输数据。 例外情况列表中包含的非托管应用必须受 IT 信任。 

>[!WARNING] 
> 由你负责更改数据传输例外情况策略。 添加到此策略可允许非托管应用（未由 Intune 托管的应用）访问受托管应用保护的数据。 这种对受保护数据的访问可能会导致数据安全泄漏。 只为组织必须使用的应用添加数据传输例外情况，但不支持 Intune APP（应用程序保护策略）。 此外，仅为你认为不存在数据泄漏风险的应用添加例外情况。

在创建数据传输设置为“仅限托管应用”的 Intune 应用程序保护策略时，此功能适用。 除创建的例外情况外，当数据传输策略设置为“仅限托管应用”时，数据传输仍将仅限于由 Intune 托管的应用。 可以使用协议 (iOS) 或包 (Android) 创建限制。

可以配置此功能，以便启用对 Intune MAM 应用保护策略“限制数据传输”的例外情况。 只有在希望允许将数据传输到不支持 Intune APP 的应用时，才需要此策略。 此策略允许由 Intune 托管的应用程序（数据传输设置设为“仅限托管应用”）基于 URL 协议 (iOS) 或包名称 (Android) 调用非托管应用程序。 Intune 将重要的本机应用程序添加到默认的例外情况列表中。 

## <a name="ios-data-transfer-exceptions"></a>iOS 数据传输例外情况
对于针对 iOS 的策略，可以通过 URL 协议配置数据传输例外情况。 若要添加例外情况，请查看应用开发人员提供的文档，以查找有关支持的 URL 协议的信息。 有关 iOS 数据传输例外情况的其他信息，请参阅 [iOS 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)。

## <a name="android-data-transfer-exceptions"></a>Android 数据传输例外情况
对于针对 Android 的策略，可以通过应用包名称配置数据传输例外情况。 可以查看要为其添加例外情况的应用的 Google Play 商店页，以查找应用包名称。 有关 Android 数据传输例外情况的其他信息，请参阅 [Android 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)。


>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

### <a name="example"></a>示例
通过在 MAM 数据传输策略中添加 Webex 包作为例外情况，可允许直接在 Webex 应用程序中打开托管 Outlook 电子邮件内的 Webex 链接。 其他非托管应用中将继续限制数据传输。

- iOS Webex 示例：若要豁免 Webex 应用，使其允许被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况：<code>wbx</code>。

- Android Webex 示例：若要豁免 Webex 应用，使其允许被 Intune 托管应用调用，必须为以下字符串添加数据传输例外情况：<code>com.cisco.webex.meetings</code>。 

## <a name="next-steps"></a>后续步骤

- [创建和部署应用保护策略](app-protection-policies.md)
- [iOS 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Android 应用保护策略设置 - 数据传输豁免](app-protection-policy-settings-android.md#data-transfer-exemptions)
