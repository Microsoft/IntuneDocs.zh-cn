---
title: Microsoft Intune 中的 Android Enterprise 设备设置 - Azure | Microsoft Docs
description: 请参阅在 Microsoft Intune 中设置 Android 企业设备的符合性时可以使用的所有设置的列表。 设置密码规则，选择最小值或最大操作系统版本、 限制特定的应用程序，防止重复使用密码和的详细信息。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16db0acab84a1095c40e9a92648c75c2581187cd
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423554"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>将设备标记为符合或不符合使用 Intune 的 android 企业版设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出并描述可在 Intune 中 Android 企业版设备配置的不同的符合性设置。 作为你的移动设备管理 (MDM) 解决方案的一部分，使用这些设置以取得 root 权限 （已越狱） 将设备标记为不符合，将设置允许的威胁级别，启用 Google Play Protect，和的详细信息。

此功能适用于：

- Android Enterprise

作为 Intune 管理员，使用这些符合性设置来帮助保护组织资源。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 对于“平台”，选择“Android 企业”。

## <a name="device-health"></a>Device health

- **取得 Root 权限的设备**：选择“阻止”将已取得 Root 权限（已越狱）的设备标记为不符合。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- 要求设备不高于设备威胁级别：使用此设置将 Lookout MTP 解决方案的风险评估视为符合性条件。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 要使用此设置，请选择允许的威胁级别：
  - **安全**：此选项是最安全的，意味着设备不能具有任何威胁。 如果设备被检测到具有任一级别的威胁，则会被评估为不符合。
  - **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - **中**：若设备设备上存在的威胁为低级或中级，则将其评为合规。 如果设备被检测到存在高级威胁，则会被确定为不符合要求。
  - 高：此选项是最不安全的，因为它允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。

### <a name="google-play-protect"></a>Google Play 保护

- **配置 Google Play Services**：要求安装并启用 Google Play Services 应用。 可通过 Google Play Services 进行安全更新，它是已获得认证的 Google 设备上的很多安全功能的基本依赖项。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- **最新的安全提供程序**：要求最新的安全提供程序可以保护设备免受已知漏洞的攻击。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- SafetyNet 设备证明：输入必须满足的 [SafetyNet 证明](https://developer.android.com/training/safetynet/attestation.html)级别。 选项包括：
  - **未配置（默认值）**：不会评估此设置的符合性或不符合性。
  - 检查基本完整性
  - 检查基本完整性和已认证的设备

> [!NOTE]
> Android 企业版设备上**对应用进行威胁扫描**是设备配置策略。 使用配置策略，管理员可以启用的设备上的设置。 请参阅 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

## <a name="device-properties-settings"></a>设备属性设置

- 最低操作系统版本：设备不满足最低 OS 版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- 最高操作系统版本：设备使用的操作系统版本高于规则中的版本时，会阻止访问公司资源。 然后会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备无法访问公司资源。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- 需要密码才可解锁移动设备：要求用户在访问其设备之前输入密码。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 在设备级别应用此设置。 如果只需要在工作配置文件级别要求密码，则使用配置策略。 请参阅 [Android Enterprise 设备配置设置](device-restrictions-android-for-work.md)。
- **最短密码长度**：输入用户密码必须包含的最小位数或最小字符数。
- **所需密码类型**：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符。 选项包括：
  - 设备默认值
  - **低安全性生物识别**
  - **至少为数字（默认）**
  - 复杂数字
  - **至少为字母**
  - **至少包含字母数字**
  - **至少为字母数字与符号**

- **要求提供密码之前的非活动最大分钟数**：输入用户必须重新输入其密码前的空闲时间。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- 密码过期(天)：选择密码过期之前的天数，然后必须创建一个新密码。
- 要防止重用的以前的密码数：输入最近用过的不能重用的密码数。 使用此设置限制用户创建以前用过的密码。

### <a name="encryption"></a>加密

- **设备上的数据存储加密**：选择“需要”加密设备上的数据存储。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 

  不必配置此设置，因为 Android 工作配置文件设备会强制进行加密。

### <a name="device-security"></a>设备安全

- **阻止来自未知源的应用**：选择此选项可阻止启用了“安全”>“未知源”源的设备（在 Android 4.0 - Android 7.x 上受支持；在 Android 8.0 及更高版本上不受支持）。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。

  若要旁加载应用，必须允许未知源。 如果没有旁加载 Android 应用，请将此功能设置为“阻止”以启用此符合性策略。 

  > [!IMPORTANT]
  > 旁加载应用程序需要启用“阻止来自未知源的应用”设置。 仅未在设备上旁加载 Android 应用时，才强制执行此符合性策略。

  无需配置此设置，因为 Android 工作配置文件设备始终限制来自未知源的安装。

- **公司门户应用运行时完整性**：选择“要求”以确认公司门户应用满足以下所有要求：

  - 已安装默认运行时环境
  - 已正确签名
  - 未处于调试模式
  - 已从已知源安装

  如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。

- **在设备上阻止 USB 调试**：选择“阻止”可阻止设备使用 USB 调试功能。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。

  无需配置此设置，因为已在 Android 工作配置文件设备上禁用 USB 调试。

- 最低安全修补程序级别：选择设备可具有的最旧的安全修补程序级别。 不满足此修补程序级别的设备将不符合要求。 日期必须以“YYYY-MM-DD”格式输入。

选择“确定” > “创建”以保存所做的更改。

## <a name="next-steps"></a>后续步骤

- [添加适用于不符合要求的设备操作](actions-for-noncompliance.md)并[使用筛选器策略的作用域标记](scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- [适用于 Android 设备的合规性策略设置](compliance-policy-create-android.md)
