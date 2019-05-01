---
title: 在 Microsoft Intune 中管理 Android 企业工作配置文件设备
titleSuffix: ''
description: Microsoft Intune 对 Android 企业工作配置文件设备进行管理，以便在用户将其个人 Android 设备用于工作时提供其他管理功能和隐私。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 305ed5c18ad0e8beeaa47bc644266d4cb19f80e6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61501045"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>使用 Intune 管理 Android 工作配置文件设备

Android 企业版提供了一组注册选项，为用户提供最新且安全的功能。 通过注册 Android 企业工作配置文件，可启用一组功能和服务，用于分隔个人应用和数据与工作应用和数据。 用户将其个人 Android 设备用于工作时，该服务还会提供额外的管理功能和隐私。 

## <a name="supported-devices"></a>支持的设备

Android 企业管理功能依赖于最新 Android 操作系统中的功能。 对于不支持 Android 企业的设备，仍可使用传统 Android 管理。 有关详细信息，请参阅 [Android 企业要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

## <a name="onboarding"></a>载入

注册 Android 企业工作配置文件设备前，必须完成一些载入步骤。 这些步骤在 Intune 租户和托管的 Google Play 之间建立连接。 有关详细信息，请参阅[启用 Android 企业工作配置文件设备的注册](android-work-profile-enroll.md)。

## <a name="work-profile-management"></a>工作配置文件管理

使用 Intune 管理 Android 企业工作配置文件设备时，不会管理整个设备。 管理功能只会影响设备注册期间创建的工作配置文件。 使用 Intune 部署到设备的任何应用都会安装到工作配置文件中。 工作配置文件中的应用图标与设备上的个人应用不同。 设备中 Android 企业部分以外的所有 Android 应用和数据保留为个人，且受最终用户的控制。 用户可将所选任何应用安装到设备的个人端。 管理员可管理和监视工作配置文件范围内的应用和操作。

Intune 提供了一系列内置常规设置，可以在 Android 工作配置文件设备上进行配置。 有关详细信息，请参阅 [Android 工作配置文件设备策略设置](compliance-policy-create-android-for-work.md)。

## <a name="app-publishing-and-distribution"></a>应用发布和分发

托管的 Google Play 是 Android 企业应用分发和管理的必要组成部分。 在工作配置文件中，部署到 Android 企业工作配置文件设备的所有应用，均来自托管的 Google Play 服务。 若要在 Play Store 中管理和部署应用，请使用公司用于 Google 管理的管理员凭据登录到 Google Play 网站。 可以批准用于 Android 企业部署的应用，使其显示在设备的工作配置文件中。 然后，这些应用将同步到 Intune 控制台中，可在控制台中使用 Intune 进行部署和管理。 组织开发的业务线 (LOB) 应用必须使用 Google Android 应用发布控制台发布到托管的 Google Play。 必须在 Android 应用发布控制台中配置业务线应用，以限制对组织的访问权限。

应用安装无需用户交互，且不要求用户允许**从未知源安装**。 若要浏览和安装可选或可用应用，用户可在其设备上浏览 Play for Work 应用商店。 有关详细信息，请参阅[使用 Intune 将应用分配到 Android 企业工作配置文件设备](apps-add-android-for-work.md)。

## <a name="app-configuration"></a>应用配置

Android 企业提供基础结构，用于将应用配置值部署到支持它们的应用。 通过为工作应用指定配置值，确保在用户首次启动该应用时已正确对其进行设置。 要支持应用配置，需要应用开发人员创建自己的 Android 应用，专门支持托管的配置值。 完成此操作后，可使用 Intune 指定和应用这些配置设置。 有关详细信息，请参阅[为受管理的 Android 设备添加应用配置策略](app-configuration-policies-use-android.md)。

## <a name="email-configuration"></a>电子邮件配置

Android 企业不提供默认电子邮件应用或如 iOS 提供的本机电子邮件配置文件对象。 而可以通过将应用配置设置应用到支持它们的电子邮件应用中，来设置电子邮件配置。 Gmail 和 Nine Work 是 Play Store 中的两种 Exchange ActiveSync (EAS) 客户端应用，它们支持使用 Android 企业应用配置进行配置。

在 Gmail 和 Nine Work 应用作为工作应用管理时，Intune 为其提供配置模板。 其他支持应用配置的配置文件的电子邮件应用可使用移动应用配置策略进行配置。

如果对 Android 企业工作配置文件设备使用的是 Exchange ActiveSync 条件访问，请考虑使用 Gmail 或 Nine Work 电子邮件应用。 同样支持 Microsoft Outlook for Android 应用，以及任何通过 ADAL 使用新式验证的其他电子邮件应用。 有关详细信息，请参阅[如何在 Microsoft Intune 中配置电子邮件设置](email-settings-configure.md)。

## <a name="app-protection-policies"></a>应用保护策略

工作配置文件和个人配置文件完全支持所应用的应用保护策略。 可在 Android 应用发布控制台中发布业务线应用，地址为 https://play.google.com/apps/publish。 此控制台包含让应用专用于组织的选项。 有关详细信息，请参阅[在 Intune 中添加适用于 Android 企业工作配置文件设备的设备合规性策略](compliance-policy-create-android-for-work.md)。 有关应用保护策略的一般信息，请参阅[什么是应用保护策略？](app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN 配置文件

VPN 支持类似于 Android VPN 配置文件。 可使用相同的 VPN 提供商和基本配置选项管理 Android 企业，只有两点差别：

-  **限于工作配置文件的 VPN** - VPN 连接仅限于部署到工作配置文件的应用。 仅 Android 企业托管应用可使用 VPN 连接。 设备上的个人应用无法使用托管 VPN 连接。 有关详细信息，请参阅 [Android 企业 VPN 设置](vpn-settings-android.md#android-enterprise-vpn-settings)。

-  **特定于应用的 VPN** - 如果 VPN 提供程序支持以下项，可在 Intune 中配置特定于应用的 VPN：
    - 特定于应用的 VPN 配置
    - 通过 Android 企业应用配置文件配置每个应用 VPN 的功能。
    有关详细信息，请参阅[使用 Microsoft Intune 自定义配置文件为 Android 设备创建每个应用 VPN 配置文件](android-pulse-secure-per-app-vpn.md)。

## <a name="certificate-profiles"></a>证书配置文件

适用于 Android 管理的证书配置文件配置选项在 Android 企业工作配置文件设备也适用。 Android 企业提供增强的证书管理 API。 增强的证书管理提供以下功能：

-  确保用户的证书部署静默且无缝。
-  设备从 Intune 停用并删除了工作配置文件时，确保已删除部署的证书。
-  提供改进的消息传送功能，通知用户 IT 部门通过管理服务部署和配置证书。

有关详细信息，请参阅[在 Microsoft Intune 中为设备配置证书配置文件](certificates-configure.md)。

## <a name="wi-fi-profiles"></a>Wi-Fi 配置文件

设备从 Intune 中停用且删除了工作配置文件时，将删除 Android 企业管理的 Wi-Fi 配置文件。 有关详细信息，请参阅[如何在 Microsoft Intune 中配置 Wi-Fi 设置](wi-fi-settings-configure.md)。

## <a name="next-steps"></a>后续步骤
- [注册 Android 设备](android-enroll.md)
- [使用 Intune 将应用分配到 Android 企业工作配置文件设备](apps-add-android-for-work.md)
