---
title: Microsoft Intune 中的 iOS 设备符合性设置 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中为 iOS 设备设置符合性时可以使用的所有设置的列表。 需要使用电子邮件，检查越狱或取得 root 权限的设备，设置允许的最小和最大操作系统，设置任何密码限制（包括密码长度和设备非活动性），限制应用等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b83b764af415349b287df2a09f9b4c355734c28
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810236"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>使用 Intune 将设备标记为符合或不符合的 iOS 设置

本文列出并描述了在 Intune 中可针对 iOS 设备配置的不同符合性设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置来要求使用电子邮件，将获得 root 权限的（已越狱）设备标记为不符合要求，设置允许的威胁级别，将密码设置为过期等。

此功能适用于：

- iOS
- iPadOS

作为 Intune 管理员，请使用这些符合性设置来帮助保护组织资源。 若要详细了解符合性策略及其作用，请参阅[设备符合性入门](device-compliance-get-started.md)。

## <a name="before-you-begin"></a>在开始之前

[创建合规性策略](create-compliance-policy.md#create-the-policy)。 对于“平台”  ，请选择“iOS/iPadOS”  。

## <a name="email"></a>Email

- **要求移动设备具有托管的电子邮件配置文件**：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。
  - **必需** - 不具备由 Intune 托管的电子邮件配置文件的设备将被视为不符合要求。 如果设备未正确设定目标，或者如果用户在设备上手动设置电子邮件帐户，则设备没有托管的电子邮件配置文件。

  在以下情况中，设备被视为不符合要求：  
  - 电子邮件配置文件分配到符合性策略所针对用户组之外的用户组。
  - 用户已在设备上设置了电子邮件帐户，且该帐户与部署到该设备的 Intune 电子邮件配置文件相匹配。 Intune 无法覆盖用户配置的配置文件，并且 Intune 无法管理它。 为了符合要求，最终用户必须删除现有的电子邮件设置。 然后，Intune 可以安装托管的电子邮件配置文件。  

有关电子邮件配置文件的详细信息，请参阅[通过 Intune 使用电子邮件配置文件配置对组织电子邮件的访问权限](../configuration/email-settings-configure.md)。

## <a name="device-health"></a>设备运行状况

- **已越狱设备**：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。
  - **阻止** - 将已取得 Root 权限（已越狱）的设备标记为不符合。  

- **要求设备不高于设备威胁级别**（iOS 8.0 及更高版本）：   
  使用此设置将风险评估视为符合性的条件。 选择允许的威胁级别：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。
  - **安全** - 此选项是最安全的，意味着设备不能具有任何威胁。 如果检测到设备具有任一级别的威胁，则会评估为不符合要求。
  - **低** - 若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
  - **中** - 若设备上存在的威胁为低级或中级，则将其评为合规。 如果检测到设备存在高级威胁，则确定其不符合要求。
  - **高** - 此选项是最不安全的，因为它允许所有威胁级别。 如果将此解决方案仅用作报告目的，则可能有用。

## <a name="device-properties"></a>设备属性

### <a name="operating-system-version"></a>操作系统版本  

- **所需的最低操作系统** *（iOS 8.0 及更高版本）* ：  
  设备不满足最低操作系统版本要求时，它将被报告为不符合要求。 将显示一个链接，链接中包含有关如何升级的信息。 最终用户可以选择升级自己的设备。 此后，他们可访问组织资源。

- **允许的最高操作系统版本** *（iOS 8.0 及更高版本）* ：  
  当设备使用的操作系统版本高于输入的版本时，将阻止对组织资源的访问。 系统会要求最终用户联系其 IT 管理员。 除非将规则更改为允许操作系统版本，否则设备无法访问组织资源。

- **最低操作系统内部版本** *（iOS 8.0 及更高版本）* ：  
  当 Apple 发布安全更新时，通常会更新内部版本号，而非操作系统版本。 使用此功能可在设备上输入允许的最低内部版本号。

- **最高操作系统内部版本** *（iOS 8.0 及更高版本）* ：  
  当 Apple 发布安全更新时，通常会更新内部版本号，而非操作系统版本。 使用此功能可在设备上输入允许的最高内部版本号。

## <a name="system-security"></a>系统安全

### <a name="password"></a>密码

> [!NOTE]
> 符合性或配置策略应用到 iOS 设备后，系统会每 15 分钟提示用户一次，要求设置密码。 系统会持续提示用户，直到用户设置密码。 为 iOS 设备设置密码时，加密过程将自动启动。 在禁用密码之前，设备一直保持加密状态。

- **需要密码才可解锁移动设备**：  
  - **未配置**（默认）- 不会评估此设置的符合性和不符合性  。  
  - **必需** - 用户必须输入密码后才能访问其设备。 使用密码的 iOS 设备已加密。

- **简单密码**：  
  - **未配置**（*默认*）-用户可以创建简单的密码，例如**1234**或**1111**。
  - **阻止** - 用户无法创建简单密码，如 1234 或 1111。   

- **最短密码长度**：  
  输入密码必须包含的最小位数或最小字符数。  

- **所需的密码类型**：  
  选择密码是应仅包含数值字符，还是应混合使用数字和其他字符（字母数字）   。

- **密码中的非字母数字字符数**：  
  输入密码中必须包含的最小特殊字符（如 `&`、`#`、`%`、`!` 等）数。 

  设置的数字越大，要求用户创建的密码越复杂。

- **屏幕锁定后要求输入密码前的最大分钟数**（iOS 8.0 及更高版本  ）：  
  指定在用户必须输入密码才能访问设备之前锁定屏幕后的时间。 选项包括*未配置* *的默认值，以及*从*1 分钟*到*4 小时*的默认值。

- **屏幕锁定前的最大非活动分钟数**：  
  输入设备锁定屏幕之前的空闲时间。 选项包括*未配置* *的默认值，以及*从*1 分钟*到*15 分钟*的默认值。

- **密码过期(天)** ：  
  选择密码过期之前的天数，然后必须创建一个新密码。 

- **阻止重用的曾用密码数**（iOS 8.0 及更高版本）：    
  输入之前使用但无法使用的密码的数量。

### <a name="device-security"></a>设备安全

- **受限制的应用**：  
  可以通过将应用的程序包 ID 添加到策略中来限制应用。 如果某一设备已安装该应用，此设备将标记为不符合要求的设备。

  - **应用名称** - 输入一个用户友好名称，帮助识别捆绑 ID。
  - **应用程序包 ID** - 输入应用提供程序分配的唯一捆绑标识符。 若要查找捆绑 ID，请参阅 [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app)（如何查找 iOS 应用的捆绑 ID）（打开另一个 Microsoft 网页）。  

## <a name="next-steps"></a>后续步骤

- [为不符合要求的设备添加操作](actions-for-noncompliance.md)并[使用范围标记来筛选策略](../fundamentals/scope-tags.md)。
- [监视符合性策略](compliance-policy-monitor.md)。
- 请参阅[适用于 macOS 设备的符合性策略设置](compliance-policy-create-mac-os.md)。
