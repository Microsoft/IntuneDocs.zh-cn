---
title: 将移动威胁防御应用添加到未注册的设备
titleSuffix: Microsoft Intune
description: 由设备用户将移动威胁防御应用添加到未注册的设备。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794454"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>将移动威胁防御应用添加到未注册的设备

默认情况下，在将 Intune 应用保护策略与移动威胁防御结合使用时，Intune 会指导最终用户在其设备上安装并登录到所有必需的应用，以启用与相关服务的连接。

最终用户需要 Microsoft Authenticator (iOS) 以注册其设备，还需要移动威胁防御（Android 和 iOS）以便在其移动设备中发现威胁时接收通知，并接收有关修复威胁的指导。

也可以使用 Intune 添加和部署 Microsoft Authenticator 以及移动威胁防御 (MTD) 应用。

> [!NOTE] 
> 本文适用于支持应用保护策略的所有移动威胁防御合作伙伴：Better Mobile (Android)、Zimperium (iOS)、Lookout for Work (Android/iOS)。
> 
> 对于未注册的设备，不需要 iOS 应用配置策略来设置通过 Intune 使用的适用于 iOS 的移动威胁防御应用。  。 这是与 Intune 已注册设备的关键差别。 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>通过 Intune 配置适用于 iOS 的 Microsoft Authenticator（可选）
将 Intune 应用保护策略用于移动威胁防御时，Intune 将指导最终用户安装、登录并将其设备注册到 Microsoft Authenticator (iOS)。

但是，如果想要通过 Intune 公司门户向最终用户提供应用，请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md) 的相关说明。 完成“配置应用信息”部分时，请使用此 [Microsoft Authenticator - iOS 应用商店 URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8)  。 最后，请不要忘记[通过 Intune 将应用分配到组](../apps/apps-deploy.md)。

> [!NOTE] 
> 对于 iOS 设备，需要 [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)，这样用户便可让 Azure AD 检查自己的标识。 Intune 公司门户在 Android 设备上以中转站的方式工作，以便用户能够让 Azure AD 检查自己的标识。

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>通过 Intune 提供移动威胁防御应用（可选）
将 Intune 应用保护策略用于移动威胁防御时，Intune 将指导最终用户安装并登录到所需的移动威胁防御客户端应用。 

但是，如果你想要通过 Intune 公司门户向最终用户提供该应用，则可以在 [Azure 门户](https://portal.azure.com/)中执行以下步骤。 请务必熟悉以下过程：

- [将应用添加到 Intune](../apps/apps-add.md)。
- [使用 Intune 分配应用](../apps/apps-deploy.md)。

### <a name="making-lookout-for-work-available-to-end-users"></a>为最终用户提供 Lookout for Work
- **Outlook Web Access (OWA)**  
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 完成“配置应用信息”部分时，请使用此 [Lookout for Work - Play Store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise)  。

- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 完成“配置应用信息”部分时，请使用此 [Lookout for Work - iOS App Store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8)  。

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>为最终用户提供 Zimperium
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - 请参阅[将 iOS 应用商店应用添加到 Microsoft Intune](../apps/store-apps-ios.md)，查看相关说明。 完成“配置应用信息”部分时，请使用此 [Zimperium - App Store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8)  。
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>为最终用户提供 Better Mobile 
- **Outlook Web Access (OWA)**
  - 请参阅[将 Android 应用商店应用添加到 Microsoft Intune](../apps/store-apps-android.md)，查看相关操作说明。 完成“配置应用信息”部分时，请使用此 [Active Shield - Play Store URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise)  。
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>后续步骤  

- [在 Intune 中为未注册的设备启用移动威胁防御连接器](~/protect/mtd-enable-unenrolled-devices.md)

