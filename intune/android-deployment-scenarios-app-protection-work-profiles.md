---
title: Microsoft Intune 中的应用保护策略和工作配置文件 - Azure | Microsoft Docs
description: 了解决定在 Microsoft Intune 中为个人或 BYOD Android 企业设备使用应用保护策略或工作配置文件时的差异和优缺点。 比较使用未注册情况下的应用保护策略 (APP-WE) 和 Android 企业工作配置文件的不同和所获得的功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d5814a4aac064394dbd0c7f5902dc3f62459ad1d
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353809"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Intune 中 Android 企业设备上的应用程序保护策略和工作配置文件

在许多组织中，管理员都面临着在不同设备上保护资源和数据的挑战。 其中的一项挑战是保护使用个人 Android 企业设备（也称为自带设备办公 (BYOD)）的用户的资源。 Microsoft Intune 支持两种适用于自带设备办公 (BYOD) 的 Android 部署方案：

- 未注册情况下的应用保护策略 (APP-WE)
- Android 企业工作配置文件

APP-WE 和 Android 工作配置文件部署方案包括以下对 BYOD 环境至关重要的关键功能：

1. **保护和分隔组织管理的数据**：这两种解决方案都是通过对组织管理的数据强制实施数据丢失防护 (DLP) 控制来保护组织数据的。 这些保护可防止受保护的数据意外泄漏，例如最终用户意外地将数据共享到个人应用或帐户。 它们还用于确保访问数据的设备正常且未遭入侵。

2. **最终用户隐私**：APP-WE 和 Android 企业工作配置文件分隔设备上的最终用户内容，以及由移动设备管理 (MDM) 管理员管理的数据。 在这两种情况下，IT 管理员都强制实施策略，例如，对组织管理的应用或标识进行仅 PIN 身份验证。 IT 管理员无法读取、访问或清除由最终用户所有或控制的数据。

为 BYOD 部署选择 APP-WE 还是 Android 企业工作配置文件取决于你的要求和业务需求。 本文旨在提供帮助你进行决策的指南。

## <a name="about-intune-app-protection-policies"></a>关于 Intune 应用保护策略

Intune 应用保护策略 (APP) 是面向用户的数据保护策略。 策略在应用程序级别应用数据丢失防护。 Intune APP 要求应用开发人员在其创建的应用上启用 APP 功能。

可以通过以下几种方式为单独的 Android 应用启用 APP：

1. **本机集成到 Microsoft 第一方应用**：适用于 Android 的 Microsoft Office 应用，以及一系列精选的其他 Microsoft 应用，都随 Intune APP 内置一起提供。 这些 Office 应用（如 Word、OneDrive、Outlook 等）不需要进行任何自定义即可应用策略。 最终用户可以直接从 Google Play 商店安装这些应用。

2. **由开发人员使用 Intune SDK 集成到应用生成**：应用开发人员可以将 Intune SDK 集成到其源代码并重新编译其应用，以支持 Intune APP 策略功能。

3. **使用 Intune App Wrapping Tool 进行包装**：某些客户无需访问源代码即可编译 Android 应用（.APK 文件）。 在没有源代码的情况下，开发人员无法与 Intune SDK 集成。 如果没有 SDK，则开发人员将无法为其应用启用 APP 策略。 开发人员必须修改或重新编码应用才能支持 APP 策略。

    为了提供帮助，Intune 为现有 Android 应用 (APK) 添加了 App Wrapping Tool  工具，并创建了可识别 APP 策略的应用。

    有关此工具的详细信息，请参阅[针对应用保护策略准备业务线应用](apps-prepare-mobile-application-management.md)。

若要查看使用 APP 启用的应用的列表，请参阅[使用一组丰富的移动应用程序保护策略的托管应用](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

## <a name="deployment-scenarios"></a>部署方案

本部分介绍 APP-WE 和 Android 企业工作配置文件部署方案的重要特征。

### <a name="app-we"></a>APP-WE

APP-WE（未注册情况下的应用保护策略）部署定义应用（而不是设备）上的策略。 在此方案中，设备通常不是由 MDM 机构（例如 Intune）注册或管理的。 若要保护应用并访问组织数据，管理员使用 APP 可管理的应用并向这些应用应用数据保护策略。

此功能适用于：

- Android 4.4 和更高版本

> [!TIP]
> 有关详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

APP-WE 方案适用于想在其设备上使用小型组织占用而不想在 MDM 中注册的最终用户。 作为管理员，你仍然需要保护数据。 这些设备不受管理。 所以，常见的 MDM 任务和功能（如 WiFi、设备 VPN 和证书管理）不属于此部署方案。

### <a name="android-enterprise-work-profiles"></a>Android 企业工作配置文件

工作配置文件是核心 Android 企业部署方案和唯一面向 BYOD 用例的方案。 工作配置文件是在 Android 操作系统级别创建的单独分区，可由 Intune 进行管理。

此功能适用于：

- 使用 Google 移动服务的 Android 5.0 和更高版本的设备

工作配置文件包括以下功能：

- **传统的 MDM 功能**：在任何 Android 企业方案中都提供重要的 MDM 功能，如使用托管的 Google Play 的应用生命周期管理。 托管的 Google Play 提供可靠的安装和更新应用的体验，无需进行任何用户干预。 IT 部门也可以将应用配置设置推送到组织应用。 此外，它也不要求最终用户允许来自未知源的安装。 工作配置文件中提供了其他常见的 MDM 活动（如部署证书、配置 WiFi/VPN 和设置设备密码）。

- **针对工作配置文件边界的 DLP**：和 APP-WE 一样，IT 部门可以强制实施数据保护策略。 对于工作配置文件，可在工作配置文件级别（而不是应用级别）强制实施 DLP 策略。 例如，复制/粘贴保护是由应用于应用的 APP 设置或由工作配置文件强制实施的。 将应用部署到工作配置文件时，管理员可以通过在 APP 级别禁用此策略来暂停工作配置文件的复制/粘贴保护。

## <a name="tips-to-optimize-the-work-profile-experience"></a>优化工作配置文件体验的提示

### <a name="when-to-use-app-within-work-profiles"></a>何时可在工作配置文件中使用 APP

Intune APP 和工作配置文件是相互补充的技术，可以一起使用，也可以单独使用。 从体系结构上来说，这两种解决方案都是在不同的层强制实施策略：在单独的应用层强制实施 APP，而在配置文件层强制实施工作配置文件。 将使用 APP 策略托管的应用部署到工作配置文件中的应用是有效和受支持的方案。 是使用应用、工作配置文件还是将两者结合使用取决于你的 DLP 要求。

如果一个配置文件无法满足组织的数据保护要求，则工作配置文件和 APP 通过提供其他覆盖范围来补充各自的设置。 例如，工作配置文件不会在本机提供控制以限制将应用保存到不受信任的云存储位置。 而 APP 包含此功能。 你可以决定仅由工作配置文件提供 DLP 就足够了，并选择不使用 APP。 或者你可能需要这两者结合提供保护。

### <a name="suppress-app-policy-for-work-profiles"></a>取消工作配置文件的 APP 策略

你可能需要支持具有多个设备（APP-WE 方案中的未托管设备和使用工作配置文件的托管设备）的单个用户。

例如，你要求最终用户在打开工作应用时输入 PIN。 根据设备的不同，PIN 功能由 APP 或工作配置文件处理。 对于 APP-WE 设备，PIN 启动行为由 APP 强制实施。 对于工作配置文件设备，可以使用由操作系统强制实施的设备或工作配置文件 PIN。 若要完成此方案，请配置 APP 设置，以便在向工作配置文件部署应用时  不会应用这些 APP 设置。 如果不按此方法对其进行配置，则最终用户会再次在 APP 层收到设备发送的要求输入 PIN 的提示。

### <a name="control-multi-identity-behavior-in-work-profiles"></a>控制工作配置文件中的多标识行为

Office 应用程序（如 Outlook 和 OneDrive）具有“多标识”行为。 在应用程序的一个实例中，最终用户可以将连接添加到多个不同的帐户或云存储位置。 在应用程序内，可将从这些位置检索的数据进行分隔或合并。 此外，用户可以在个人标识 (user@outlook.com) 和组织标识 (user@contoso.com) 之间进行上下文切换。

在使用工作配置文件时，你可能想要禁用此多标识行为。 禁用该行为时，工作配置文件中应用的标记实例只能使用组织标识进行配置。 使用“允许的帐户”应用配置设置来支持 Office Android 应用。

有关详细信息，请参阅[部署 Outlook for iOS 和 Outlook for Android 应用配置设置](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)。

## <a name="when-to-use-intune-app"></a>何时使用 Intune APP

在多个企业移动方案中，均建议最好使用 Intune APP。

### <a name="older-devices-running-android-44-51-are-being-used"></a>正在使用运行 Android 4.4 5.1 的较旧设备

官方宣称，使用 Google 移动服务的任何 Android 设备 5.0 或更高版本都支持工作配置文件，并且都有资格使用这种方式进行管理。 但是，某些 OEM 的 Android 5.0 和 5.1 设备不支持工作配置文件。

如果使用的是不支持工作配置文件的版本，为了确保对设备上的组织数据使用 DLP，则必须使用 Intune APP 功能。

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>MDM、注册和 Google 服务均可用

出于不同的原因，某些客户不需要任何形式的设备管理（包括工作配置文件管理）：

- 法律和责任原因
- 为保持用户体验的一致性
- Android 设备环境高度多样化
- 没有与 Google 服务的任何连接，进行工作配置文件管理需要此连接。

例如，在中国的客户或在中国拥有用户的客户不能使用 Android 设备管理，因为 Google 服务已被阻止。 在这种情况下，请使用 Intune APP 进行 DLP。

## <a name="summary"></a>“摘要”

使用 Intune 时，APP-WE 和 Android 企业工作配置文件都可用于 Android BYOD 程序。 选择 APP-WE 还是工作配置文件取决于业务和使用情况要求。 总之，如果需要在托管设备上使用 MDM 活动（例如证书部署、应用推送等），则使用工作配置文件。 如果不想或不能管理设备且使用仅启用了 Intune APP 的应用，则使用 APP-WE。

## <a name="next-steps"></a>后续步骤
[开始使用应用保护策略](app-protection-policy.md)或[注册设备](android-enroll.md)。
