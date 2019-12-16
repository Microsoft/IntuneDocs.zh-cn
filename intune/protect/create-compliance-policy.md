---
title: 在 Microsoft Intune 中创建设备符合性策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中：创建设备符合性策略，状态和严重性级别概述，使用 InGracePeriod 状态，使用条件访问，处理不具有分配策略的设备，以及 Azure 门户和经典门户中的符合性的差别
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba6b8fb66d25af3833e55eebc12e8b6df2fb5ba5
ms.sourcegitcommit: 66e284fe092e19c1da72b4b770e45bf25ac7910c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74860224"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>在 Microsoft Intune 中创建符合性策略

使用 Intune 保护组织的资源时，设备符合性策略是一项关键功能。 在 Intune 中，可以创建规则和设置，设备必须满足这些设置（例如最低操作系统版本）才能被视为符合策略。 如果设备不符合，则可使用[条件访问](conditional-access.md)阻止对数据和资源的访问。

此外，还可针对不符合的情况采取措施，例如向用户发送通知电子邮件。 有关符合性策略的作用以及使用方式的概述，请参阅[设备符合性入门](device-compliance-get-started.md)。

本文：

- 列出了创建符合性策略的先决条件和步骤。
- 介绍如何将策略分配给用户和设备组。
- 介绍其他功能，包括用于“筛选”策略的作用域标记，以及可对不符合策略的设备采取的措施。
- 列出设备接收策略更新时的签入刷新周期时间。

## <a name="before-you-begin"></a>在开始之前

若要使用设备符合性策略，请务必：

- 使用以下订阅：

  - Intune
  - 如果使用条件访问，则需要 Azure Active Directory (AD) Premium 版本。 [Azure Active Directory 定价](https://azure.microsoft.com/pricing/details/active-directory/)列出了购买不同版本可获得的功能。 Intune 符合性不需要 Azure AD。

- 使用支持的平台：

  - Android 设备管理员
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- 在 Intune 中注册设备（用于查看符合性状态）

- 向一个用户设备注册，或在没有主要用户的情况下注册。 不支持向多个用户注册设备。

## <a name="create-the-policy"></a>创建策略

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “符合性策略”   > “创建策略”  。

3. 指定以下属性：

   - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，策略名称最好为“将已越狱的 iOS 设备标记为不符合策略”  。

   - **说明**：输入策略的说明。 此设置是可选的，但建议进行。

   - **平台**：选择设备平台。 选项包括：
     - **Android 设备管理员**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 及更高版本**
     - **Windows 10 及更高版本**

     对于 Android Enterprise，必须选择“配置文件类型”   ：
     - **设备所有者**
     - **工作配置文件**

   - **设置**：下面的文章列出并介绍了每个平台的设置：
     - [Android 设备管理员](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1、Windows 8.1 及更高版本](compliance-policy-create-windows-8-1.md)
     - [Windows 10 及更高版本](compliance-policy-create-windows.md)  

   - **位置** *（Android 设备管理员）* ：在策略中，可根据设备位置强制执行符合性。 从现有位置进行选择。 尚无位置？ 在 Intune 中[使用的位置（网络围墙）](use-network-locations.md)提供一些指导。  

   - **对不合规设备的操作**：对于不满足符合性策略要求的设备，可添加要自动应用的一系列操作。 可以在设备被标记为不符合时（例如，一天后）更改计划。 此外，还可以配置第二个操作，即在设备不符合时向用户发送电子邮件。

     [为不符合要求的设备添加操作](actions-for-noncompliance.md)提供了详细信息，包括为用户创建通知电子邮件。

     例如，使用“位置”功能，并在符合性策略中添加位置。 选择至少一个位置时，将应用针对不符合的默认操作。 如果设备未连接到所选位置，则会被立即视为不符合要求。 可以为用户提供宽限期（例如，一天）。

   - **作用域（标记）** ：作用域标记非常适合用于将策略筛选到特定组（例如 `US-NC IT Team` 或 `JohnGlenn_ITDepartment`）。 添加设置后，还可以向符合性策略添加作用域标记。 [使用作用域标记筛选策略](../fundamentals/scope-tags.md)是不错的资源。

4. 完成后，选择“确定” > “创建”，保存所做更改   。 此时，策略创建完成，并出现在列表中。 接下来，向组分配策略。

## <a name="assign-the-policy"></a>分配策略

创建策略后，下一步是向组分配策略：

1. 选择已创建的策略。 现有策略位于“设备” > “符合性策略” > “策略”中    。

2. 选择策略  > “分配”   。 可以包括或排除 Azure Active Directory (AD) 安全组。

3. 选择“所选组”  查看 Azure AD 安全组。 先选择要应用此策略的组，再选择“保存”，以部署此策略  。

当策略所面向的用户或设备使用 Intune 签入时，会对其进行评估以确定是否满足符合性要求。

### <a name="evaluate-how-many-users-are-targeted"></a>评估所面向的用户数

分配策略后，还可以评估  受影响的用户数。 此功能计算用户数，不计算设备数。

1. 在 Intune 中，选择“设备”   > “符合性策略”   > “策略”  。

2. 选择策略  > “分配” > “评估”    。 随即出现一条消息，显示此策略所面向的用户数。

如果“评估”按钮呈灰显状态，请确保策略已分配到一个或多个组  。

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>刷新周期时间

Intune 使用不同的刷新周期来检查符合性策略的更新。 如果设备是最近注册的，则会增加运行签入的频率。 [策略和配置文件刷新周期](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)列出了估计的刷新时间。

用户可以随时打开公司门户应用，并同步设备以立即检查策略更新。

### <a name="assign-an-ingraceperiod-status"></a>分配 InGracePeriod 状态

符合性策略的 InGracePeriod 状态是一个值。 该值由设备的宽限期和设备针对该符合性策略的实际状态共同确定。

具体而言，如果设备的已分配符合性策略为“不符合”状态，且：

- 设备未分配到宽限期，则符合性策略的指定值为“不符合”
- 设备具有已到期的宽限期，则符合性策略的指定值为“不符合”
- 设备具有将来的宽限期，则符合性策略的指定值为“InGracePeriod”

下表概述了这些情况：

|实际符合性状态|指定的宽限期的值|有效符合性状态|
|---------|---------|---------|
|不符合 |未指定宽限期 |不符合 |
|不符合 |过去的日期|不符合|
|不符合 |将来的日期|InGracePeriod|

有关监视设备符合性策略的详细信息，请参阅[监视 Intune 设备符合性策略](compliance-policy-monitor.md)。

### <a name="assign-a-resulting-compliance-policy-status"></a>分配生成的符合性策略状态

如果设备具有多个符合性策略，且该设备分配到的两个或多个符合性策略的符合性状态各不相同，则系统会分配单个生成的符合性状态。 此分配基于向每个符合性状态指定的概念严重性级别。 每个符合性状态均包含以下严重性级别：

|状态  |严重性  |
|---------|---------|
|Unknown     |1|
|不适用     |2|
|是否满足条件|3|
|InGracePeriod|4|
|不符合|5|
|错误|6|

设备具有多个符合性策略时，系统会为该设备分配所有策略中的最高严重性级别。

例如，某台设备分配有三个符合性策略：一个处于“未知”状态（严重性 = 1），一个处于“符合”状态（严重性 = 3），还有一个处于 InGracePeriod 状态（严重性 = 4）。 InGracePeriod 状态具有最高的严重性级别。 因此，所有三个策略都处于 InGracePeriod 符合性状态。

## <a name="next-steps"></a>后续步骤

[监视策略](compliance-policy-monitor.md)。
