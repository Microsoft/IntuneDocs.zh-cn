---
title: 在 Microsoft Intune 中创建 Android Enterprise 符合性策略 - Azure | Microsoft Docs
description: 创建或配置适用于 Android Enterprise 或工作配置文件设备的 Microsoft Intune 设备符合性策略。 选择允许使用已越狱设备、设置可接受的威胁级别、查看 Google Play、输入最低和最高操作系统版本、选择密码要求并允许旁加载应用程序。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1c89257a05ad1aa68ee328253c2e954cb77da47
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229779"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>在 Intune 中添加适用于 Android Enterprise 设备的设备符合性策略

使用 Intune 保护组织的资源时，设备符合性策略是一项关键功能。 在 Intune 中，可以创建规则和设置，设备必须满足这些设置（例如密码长度）才能被视为符合。 如果设备不符合，则可使用[条件访问](conditional-access.md)阻止对数据和资源的访问。 

此外，还可获取设备报表，并针对不符合的情况采取措施，例如向用户发送通知电子邮件。 若要了解有关符合性策略以及所有系统必备组件的详细信息，请参阅[设备符合性入门](device-compliance-get-started.md)。

本文列出的设置可以在运行 Android Enterprise 的设备符合性策略中使用。

## <a name="non-compliance-and-conditional-access"></a>不符合和条件访问

下表说明了将符合性策略与条件访问策略一起使用时如何管理非符合性设置。

--------------------------

|**策略设置**| **Android Enterprise 配置文件** |
| --- | --- |
| **PIN 或密码配置** |  已隔离 |
| **设备加密** |  已隔离 |
| **已越狱或取得 root 权限的设备** | 已隔离（非设置） |
| **电子邮件配置文件** | “不适用” |
| **最低操作系统版本** | 已隔离 |
| **最高操作系统版本** | 已隔离 |
| **Windows 运行状况证明** |“不适用” |

**已修正** = 设备操作系统强制合规性。 例如，强制用户设置 PIN。

**已隔离** = 设备操作系统不会强制执行符合性。 例如，Android 设备不强制用户加密设备。 设备不符合时，系统将进行以下操作：

  - 如果对用户应用了条件访问策略，设备将被阻止。
  - 公司门户会通知用户任何合规性问题。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. 对于“平台”，选择“Android 企业”。 
5. 选择“设置配置”。 按本文所述，依次输入“设备运行状况”、“设备属性”和“系统安全”设置。

## <a name="device-health"></a>Device health

- **取得 root 权限的设备**：选择“阻止”将已取得 Root 权限（已越狱）的设备标记为不符合。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- **要求设备不高于设备威胁级别**：使用此设置将 Lookout MTP 解决方案的风险评估视为合规性的条件。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 要使用此设置，请选择允许的威胁级别：
  - **安全**：此选项是最安全的，意味着设备不能具有任何威胁。 如果设备被检测到具有任一级别的威胁，则会被评估为不符合。
  - **低**：如果设备上仅存在低级威胁，则会被评估为符合要求。 低级以上的任意威胁都将使设备不合规。
  - **中**：若设备上存在的威胁为低级或中级，则将其评为合规。 如果设备被检测到存在高级威胁，则会被确定为不符合要求。
  - **高**：此选项是最不安全的，因为它允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。
- **配置 Google Play Services**：要求安装并启用 Google Play Services 应用程序。 可通过 Google Play Services 进行安全更新，它是已获得认证的 Google 设备上的很多安全功能的基本依赖项。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- **最新的安全提供程序**：要求最新的安全提供程序可以保护设备免受已知的漏洞攻击。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- **SafetyNet 设备证明**：输入必须满足的 [SafetyNet 证明](https://developer.android.com/training/safetynet/attestation.html)级别。 选项包括：
  - **未配置**（默认）：不会评估此设置的符合性或不符合性。
  - 检查基本完整性
  - 检查基本完整性和已认证的设备

#### <a name="threat-scan-on-apps"></a>对应用进行威胁扫描

在 Android Enterprise 设备上，“对应用进行威胁扫描”设置是一种配置策略。 请参阅 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

## <a name="device-properties-settings"></a>设备属性设置

- **最低操作系统版本**：设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级其设备，然后访问公司资源。
- **最高操作系统版本**：设备使用的操作系统版本高于规则中的版本时，会阻止访问公司资源。 然后会要求用户联系其 IT 管理员。除非变更规则以允许该操作系统版本，否则该设备无法访问公司资源。

## <a name="system-security-settings"></a>系统安全设置

### <a name="password"></a>密码

- **需要密码才可解锁移动设备**：要求用户输入密码后才能访问其设备。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 在设备级别应用此设置。 如果只需要在工作配置文件级别要求密码，则使用配置策略。 请参阅 [Android Enterprise 设备配置设置](device-restrictions-android-for-work.md)。
- **最短密码长度**：输入用户密码必须包含的最小位数或最小字符数。
- **所需的密码类型**：选择密码是应仅包含数值字符，还是应混合使用数字和其他字符。 选项包括：
  - 设备默认值
  - **低安全性生物识别**
  - **至少为数字（默认）**
  - 复杂数字
  - **至少为字母**
  - **至少包含字母数字**
  - **至少为字母数字与符号**

- **需要提供密码之前处于非活动状态的最大分钟数**：输入用户必须重新输入密码前的空闲时间。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。
- **密码过期(天)**：选择密码过期之前的天数，然后必须创建一个新密码。
- **阻止重用的曾用密码数**：输入最近使用的不能重用的密码数。 使用此设置限制用户创建以前用过的密码。

### <a name="encryption"></a>加密

- **加密设备上的数据存储**：选择“要求”来加密设备上的数据存储。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。 

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

- **在设备上阻止进行 USB 调试**：选择“阻止”可阻止设备使用 USB 调试功能。 如果选择“未配置”（默认值），则不会评估此设置的符合性或不符合性。

  无需配置此设置，因为已在 Android 工作配置文件设备上禁用 USB 调试。

- **最低安全修补程序级别**：选择设备可具有的最旧的安全修补程序级别。 不满足此修补程序级别的设备将不符合要求。 日期必须以“YYYY-MM-DD”格式输入。

完成后，选择“确定” > “确定”以保存所做更改。

## <a name="actions-for-noncompliance"></a>对不符合设备的操作

选择“针对非符合性的操作”。 默认操作会立即将设备标记为不符合。

可以在设备被标记为不符合时（例如，一天后）更改计划。 此外，还可以配置第二个操作，即在设备不符合时向用户发送电子邮件。

[为不符合要求的设备添加操作](actions-for-noncompliance.md)提供了详细信息，包括为用户创建通知电子邮件。

## <a name="scope-tags"></a>作用域标记

作用域标记是将策略分配给特定组（例如销售、工程、人力资源等）的好方法。 可以将作用域标记添加到符合性策略。 请参阅[使用作用域标记筛选策略](scope-tags.md)。 

## <a name="assign-user-groups"></a>分配用户组

创建策略后，在分配策略之前，它不会执行任何操作。 分配策略： 

1. 选择已配置的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择想要应用此策略的用户组，并选择“保存”向用户部署该策略。

已将策略应用于用户。 需对策略目标用户所用的设备进行符合性评估。

## <a name="next-steps"></a>后续步骤
[为不符合的设备自动发送电子邮件和添加操作](actions-for-noncompliance.md)  
[监视 Intune 设备符合性策略](compliance-policy-monitor.md)  
[适用于 Android 的符合性策略设置](compliance-policy-create-android.md)
