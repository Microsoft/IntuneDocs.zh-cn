---
title: Microsoft Intune 中的设备符合性策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中：开始使用设备符合性策略，状态和严重性级别概述，使用 InGracePeriod 状态，使用条件访问，处理不具有分配策略的设备，以及 Azure 门户和经典门户中的符合性的差别
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0aa98774f25bf290391225c6ccae56a3859c22
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570411"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>在 Microsoft Intune 中创建符合性策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

  - Android
  - Android Enterprise
  - iOS
  - macOS（预览）
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- 在 Intune 中注册设备（用于查看符合性状态）

- 向一个用户设备注册，或在没有主要用户的情况下注册。 不支持向多个用户注册设备。

## <a name="create-the-policy"></a>创建策略

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备符合性”。 有下列选项：

    - **概述**：显示摘要以及符合策略的设备数、未评估的设备数等。 另外，还列出了策略以及策略中的各项设置。 [监视 Intune 设备符合性策略](compliance-policy-monitor.md)提供了一些有用的信息。
    - **管理**：创建设备策略，向不符合策略的设备发送[通知](quickstart-send-notification.md)，并启用[网络隔离](use-network-locations.md)。
    - **监视**：在设置和策略级别检查设备的符合性状态。 [监视 Intune 设备符合性策略](compliance-policy-monitor.md)是不错的资源。 此外还查看日志并检查设备的威胁代理状态。
    - **设置**：使用[内置的符合性策略](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)，启用 [Windows Defender 高级威胁防护 (ATP)](advanced-threat-protection.md)，添加[移动威胁防御连接器](mobile-threat-defense.md)，并使用 [Jamf](conditional-access-integrate-jamf.md)。

3. 选择“策略” > “创建策略”。 输入以下属性：

    - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，策略名称最好为“将已越狱的 iOS 设备标记为不符合策略”。
    - **说明**：输入策略的说明。 此设置是可选的，但建议进行。
    - **平台**：选择设备平台。 选项包括：  

       - **Outlook Web Access (OWA)**
       - **Android 企业**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更高版本**
       - **Windows 10 及更高版本**

    - **设置**：下面的文章列出并介绍了每个平台的设置：

        - [Outlook Web Access (OWA)](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1、Windows 8.1 及更高版本](compliance-policy-create-windows-8-1.md)
        - [Windows 10 及更高版本](compliance-policy-create-windows.md)

4. 完成后，选择“确定” > “创建”，保存所做更改。 此时，策略创建完成，并出现在列表中。 接下来，向组分配策略。

## <a name="assign-user-groups"></a>分配用户组

创建策略后，下一步是向组分配策略：

1. 选择已创建的策略。 现有策略位于“设备符合性” > “策略”中。
2. 选择策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
3. 选择“所选组”查看 Azure AD 安全组。 选择想要应用此策略的用户组，然后选择“保存”向用户部署该策略。

此时，已将策略应用于用户。 需对策略目标用户所用的设备进行符合性评估。

### <a name="evaluate-how-many-users-are-targeted"></a>评估所面向的用户数

分配策略后，还可以评估受影响的用户数。 此功能计算用户数，不计算设备数。

1. 在 Intune 中，选择“设备符合性” > “策略”。
2. 选择一个策略，然后依次选择“分配” > “评估”。 随即出现一条消息，显示此策略所面向的用户数。

如果“评估”按钮呈灰显状态，请确保策略已分配到一个或多个组。

## <a name="actions-for-noncompliance"></a>对不符合设备的操作

对于不满足符合性策略要求的设备，可添加要自动应用的一系列操作。 可以在设备被标记为不符合时（例如，一天后）更改计划。 此外，还可以配置第二个操作，即在设备不符合时向用户发送电子邮件。

[为不符合要求的设备添加操作](actions-for-noncompliance.md)提供了详细信息，包括为用户创建通知电子邮件。

例如，使用“位置”功能，并在符合性策略中添加位置。 选择至少一个位置时，将应用针对不符合的默认操作。 如果设备未连接到所选位置，则会被立即视为不符合要求。 可以为用户提供宽限期（例如，一天）。

## <a name="scope-tags"></a>作用域标记

作用域标记非常适合用于筛选策略并将其分配给特定组（例如，“销售”、“HR”、“所有 US-NC”员工等）。 添加设置后，还可以向符合性策略添加作用域标记。 [使用作用域标记筛选策略](scope-tags.md)是不错的资源。

## <a name="refresh-cycle-times"></a>刷新周期时间

检查符合性时，Intune 使用的刷新周期与配置文件相同。 通常情况下，刷新周期时间为：

| 平台 | 刷新周期|
| --- | --- |
| iOS | 每 6 小时一次 |
| macOS | 每 6 小时一次 |
| Android | 每 8 小时一次 |
| 注册为设备的 Windows 10 PC | 每 8 小时一次 |
| Windows Phone | 每 8 小时一次 |
| Windows 8.1 | 每 8 小时一次 |

如果设备是最近注册的，则会增加运行符合性签入的频率：

| 平台 | 频率 |
| --- | --- |
| iOS | 6 小时内每 15 分钟一次，之后每 6 小时一次 |  
| macOS | 6 小时内每 15 分钟一次，之后每 6 小时一次 | 
| Android | 15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| 注册为设备的 Windows 10 PC | 30 分钟内每 3 分钟一次，之后每 8 小时一次 | 
| Windows Phone | 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| Windows 8.1 | 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 

用户可以随时打开公司门户应用，并同步设备以立即检查策略。

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