---
title: 关于 Android for Work
description: Intune 管理 Android for Work，在用户将其 Android 设备用于工作时提供其他管理功能和隐私。
keywords: ''
author: nathbarn
manager: dougeby
ms.date: 03/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: ac83eb71b04e034023d008fa4cdbb960f2c4bedb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020956"
---
# <a name="manage-android-for-work-devices-with-intune"></a>使用 Intune 管理 Android for Work 设备

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Android for Work 是一组 Android 设备功能和服务，它将分隔个人应用和数据与包含工作应用和数据的工作配置文件。 用户将其 Android 设备用于工作时，Android for Work 将提供额外的管理功能和隐私。 Intune 可帮助用户将应用和公司资源部署到 Android for Work 设备，确保将工作和个人信息分开。 部署成功后，他们访问的应用和数据仍单独保留在设备上的 Android for Work 环境中。

## <a name="supported-devices"></a>支持的设备

Android for Work 管理功能依赖于较新 Android 操作系统中的功能。 目前，运行 Android 5.0 Lollipop 及更高版本的设备以及支持工作配置文件的设备支持 Android for Work。 对于不支持 Android for Work 的设备，仍可使用传统 Android 管理。 详细了解 [Android for Work 的要求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)。

## <a name="onboarding"></a>载入

注册 Android for Work 设备前，必须完成一些载入步骤。 这些步骤将在 Intune 租户和 Google Play for Work 服务之前建立连接，这是 Android for Work 应用分发和管理过程中不可或缺的一部分。 详细了解[启用 Android for Work 注册](/intune-classic/deploy-use/set-up-android-for-work)。

## <a name="work-profile-management"></a>工作配置文件管理

使用 Intune 管理 Android for Work 设备时，不会管理整个设备。 管理功能只会影响设备注册期间创建的工作配置文件。 使用 Intune 部署到设备的任何应用都会安装到工作配置文件中。 工作配置文件中的应用图标将显示橙色公文包，以便区分设备上的工作应用和个人应用。 设备中 Android for Work 部分以外的所有 Android 应用和数据保留为个人，且受最终用户的控制。 用户可将任何所选应用安装到设备的个人端，而管理员可管理和监视限于工作配置文件的应用和操作。

Intune 提供了一系列内置常规设置，你可以在 Android for Work 设备上进行配置。 详细了解 [Android for Work 策略设置](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="app-publishing-and-distribution"></a>应用发布和分发

Google Play for Work 服务是 Android for Work 应用分发和管理的必要组成部分。 部署到 Android for Work 设备的所有应用，在工作配置文件中都会显示为来自 Play for Work 服务。 若要在 Play Store 中管理和部署应用，请使用公司用于 Google 管理的管理员凭据登录到 Google Play 网站。 可以批准用于 Android for Work 部署的应用，使其显示在设备的工作配置文件中。 然后，这些应用将同步到 Intune 控制台中，可在控制台中使用 Intune 进行部署和管理。 组织开发的业务线 (LOB) 应用必须使用 Google Android 应用发布控制台发布到 Play for Work。 必须在 Android 应用发布控制台中配置业务线应用，以限制对组织的访问权限。

应用安装无需用户交互，且不要求用户允许**从未知源安装**。 若要浏览和安装可选或可用应用，用户可在其设备上浏览 Play for Work 应用商店。 详细了解[为 Android for Work 部署应用](/intune-classic/deploy-use/android-for-work-apps)。

## <a name="app-configuration"></a>应用配置

Android for Work 提供基础结构，用于将应用配置值部署到支持它们的应用。 通过为工作应用指定配置值，确保在用户首次启动该应用时已正确对其进行设置。 要支持应用配置，需要应用开发人员创建自己的 Android 应用，专门支持托管的配置值。 完成此操作后，可使用 Intune 指定和应用这些配置设置。 详细了解 [Android for Work 应用配置设置](afw-app-configuration-policy.md)。

## <a name="email-configuration"></a>电子邮件配置

Android for Work 不提供默认电子邮件应用或如 iOS 提供的本机电子邮件配置文件对象。 而可以通过将应用配置设置应用到支持它们的电子邮件应用中，来设置电子邮件配置。 Gmail 和 Nine Work 是 Play Store 中的两种 Exchange ActiveSync (EAS) 客户端应用，它们支持使用 Android for Work 应用配置进行配置。

在 Gmail 和 Nine Work 应用作为工作应用管理时，Intune 为其提供配置模板。 其他支持应用配置的配置文件的电子邮件应用可使用移动应用配置策略进行配置。

如果对 Android for Work 设备使用的是 Exchange ActiveSync 条件访问，则必须使用 Gmail 或 Nine Work 电子邮件应用。 同样支持 Microsoft Outlook for Android 应用，以及任何通过 ADAL 使用新式验证的其他电子邮件应用。 详细了解[公司电子邮件的电子邮件配置文件](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。

## <a name="app-protection-policies"></a>应用保护策略

工作配置文件和个人配置文件完全支持所应用的应用保护策略。 可在 Android 应用发布控制台中发布业务线应用，地址为 https://play.google.com/apps/publish。 此控制台包含让应用专用于组织的选项。 详细了解 [Android for Work 合规性策略设置](afw-compliance-policy-settings-in-microsoft-intune.md)。 有关应用防护策略的常规信息，请参阅[应用策略](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。

## <a name="vpn-profiles"></a>VPN 配置文件

VPN 支持类似于 Android VPN 配置文件。 可使用相同的 VPN 提供商和基本配置选项管理 Android for Work，只有两点差别：

-  **限于工作配置文件的 VPN** - VPN 连接仅限于部署到工作配置文件的应用。 仅 Android for Work 托管应用可使用 VPN 连接。 设备上的个人应用无法使用托管 VPN 连接。

-  **特定于应用的 VPN** - 如果 VPN 提供商支持特定于应用的 VPN 配置，并提供通过 Android for Work 应用配置的配置文件配置 per-app VPN 的功能，则可在 Intune 中配置特定于应用的 VPN。 请咨询 VPN 提供商，确定他们是否支持此功能。 详细了解 [VPN 连接配置文件](vpn-connections-in-microsoft-intune.md)。

## <a name="certificate-profiles"></a>证书配置文件

适用于 Android 管理的证书配置文件配置选项在 Android for Work 设备也适用。 Android for Work 提供增强的证书管理 API。 增强的证书管理提供以下功能：

- 确保用户的证书部署静默且无缝。
-  设备从 Intune 停用并删除了工作配置文件时，确保已完全删除部署的证书。
-  提供改进的消息传送功能，通知用户 IT 部门通过管理服务部署和配置证书。

详细了解[证书配置文件](secure-resource-access-with-certificate-profiles.md)。

## <a name="wi-fi-profiles"></a>Wi-Fi 配置文件

设备从 Intune 中停用且删除了工作配置文件时，将删除 Android for Work 管理的 Wi-Fi 配置文件。 详细了解 [Wi-Fi 配置文件](wi-fi-connections-in-microsoft-intune.md)。

## <a name="next-steps"></a>后续步骤
[启用 Android for Work 注册](/intune-classic/deploy-use/set-up-android-for-work)

[为 Android for Work 部署应用](/intune-classic/deploy-use/android-for-work-apps)
