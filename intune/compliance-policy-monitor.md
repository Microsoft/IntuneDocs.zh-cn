---
title: 在 Microsoft Intune 中监视设备符合性策略 - Azure | Microsoft Docs
description: 使用设备符合性仪表板监视整体设备符合性，查看报表，并查看基于策略和基于设置的设备符合性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e26de8691e78e4b35e8618c48f38c7972af233f8
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977297"
---
# <a name="monitor-intune-device-compliance-policies"></a>监视 Intune 设备符合性策略

符合性报告有助于审查设备符合性以及排查组织中与符合性相关的问题。 使用这些报告，可以查看以下信息：

- 设备的总体符合性状态
- 单个设置的符合性状态
- 单个策略的符合性状态
- 向下钻取到单个设备，查看影响设备的特定设置和策略

## <a name="open-the-compliance-dashboard"></a>打开符合性仪表板

打开“Intune 设备符合性仪表板”：

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。

2. 选择“设备符合性” > 概述。 “设备符合性仪表板”随即打开。

> [!IMPORTANT]
> 设备必须注册到 Intune 才能接收设备符合性策略。

## <a name="dashboard-overview"></a>仪表板概述

仪表板打开后，可获取所有符合性报告的概述。 在这些报告中，可以查看和检查：

- 设备的总体符合性
- 基于策略的设备符合性
- 基于设置的设备符合性
- 设备保护状态
- 威胁代理状态

![仪表板图像显示设备符合性仪表板和不同报告](./media/compliance-policy-monitor/idc-1.png)

如果深入了解此报告，还可以看到应用于特定设备的任何特定符合性策略和设置，包括每个设置的符合性状态。

### <a name="device-compliance-status-report"></a>设备符合性状态报告

此图表显示所有已注册 Intune 的设备的符合性状态。 设备符合性状态保存在两个不同的数据库中：Intune 和 Azure Active Directory。 

> [!IMPORTANT]
> Intune 对设备上的所有符合性评估遵循设备签入计划。 [详细了解设备签入计划](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)。

不同的设备符合性策略状态的说明：

- **符合**：设备已成功应用一个或多个设备符合性策略设置。

- **在宽限期内：** 设备成为一个或多个设备符合性策略设置的目标。 但是，用户尚未应用策略。 这意味着设备不符合要求，但处于管理员定义的宽限期内。

  - 详细了解[针对不符合设备的操作](actions-for-noncompliance.md)。

- **未评估**：新注册设备的初始状态。 或者，设备未分配有任何符合性策略，并且没有用于检查符合性的触发器。

- **不符合：** 设备无法应用一个或多个设备符合性策略设置。 或者，用户未遵守策略。

- **设备未同步：** 设备无法报告自己的设备符合性策略状态，原因为下列之一：

  - **未知**：由于其他原因，设备处于脱机状态，或无法与 Intune 或 Azure AD 通信。

  - **错误**：设备无法与 Intune 和 Azure AD 通信，并收到注明原因的错误消息。

> [!IMPORTANT]
> 已注册到 Intune 但未由任何设备符合性策略指定的设备包含在位于“符合性”存储桶下的此报告中。

#### <a name="drill-down-for-more-details"></a>向下钻取，了解详细信息

在“设备符合性状态”图表中，选择一个状态。 例如，选择“不符合”状态：

![选择“不符合”状态](./media/compliance-policy-monitor/select-not-compliant-status.png)

可看到处于该状态的设备的详细信息，包括操作系统平台、上次签入日期等。 

![仪表板图像显示处于该特定状态的设备的详细信息](./media/compliance-policy-monitor/drill-down-details.png)

如果想要查看某一特定用户拥有的所有设备，还可以通过键入该用户的电子邮件来筛选图表报告。

#### <a name="filter-and-columns"></a>筛选器和列

![选择“筛选器和列”，更改图表中的结果](./media/compliance-policy-monitor/filter-columns.png)

选择“筛选器”按钮时，将打开筛选器弹出窗口，其中包括符合性状态、已越狱的设备等多个选项。 应用筛选器以更新结果。

使用“列”属性添加或删除图表输出中的列。 例如，“用户主体名称”可能显示在设备上注册的电子邮件地址。 应用列以更新结果。

#### <a name="device-details"></a>设备详细信息

在图表中，选择某一特定设备，然后选择“设备符合性”：

![选择某一特定设备，然后选择“设备符合性”，查看应用的符合性策略](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

这将提供有关应用于该设备的设备符合性策略设置的详细信息。 选择该特定策略时，它将显示策略中的所有设置。

### <a name="devices-without-compliance-policy"></a>没有符合性策略的设备
在“设备符合性” > “概述”中，此报告还标识出了未分配有任何符合性策略的设备：

![查看没有任何符合性策略的设备](./media/compliance-policy-monitor/devices-without-policies.png)

选中该磁贴时，它将显示没有任何符合性策略的所有设备。 此外，它还将显示设备用户、策略部署状态和设备模型。

#### <a name="what-you-need-to-know"></a>需要了解的信息

- 使用“将未分配有任何符合性策略的设备标记为”安全设置，请务必标识不具有符合性策略的设备。 然后才能为这些设备分配至少一个符合性策略。

  可以在 Intune 门户中配置安全性设置。 选择“设备符合性” > “符合性策略设置”。 然后将“将未分配有任何符合性策略的设备标记为”设置为“符合”或“不符合”。 

  有关详细信息，请参阅 [Intune 服务中的安全性增强功能](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/)。

- 该报告中不会显示分配有任何类型的符合性策略的用户，无论是何设备平台。 例如，如果你向使用 Android 设备的某位用户分配了一个 Windows 符合性策略，则该设备不会出现在此报告中。 但 Intune 会将该 Android 设备视为不符合。 为避免出现问题，我们建议你为每个设备平台创建对应的策略，并将这些策略部署给所有用户。

### <a name="per-policy-device-compliance-report"></a>基于策略的设备符合性报告

“设备符合性” > “策略符合性”报告显示策略，以及符合和不符合的设备数。 

![查看策略列表以及符合和不符合该策略的设备数列表](./media/compliance-policy-monitor/idc-8.png)

选择特定策略时，可以看到该符合性策略针对的每个设备的“符合性状态”、“用户的电子邮件别名”、“设备模型”及“位置”。

## <a name="setting-compliance-report"></a>设置符合性报告

“设备符合性” > “设置符合性”报告显示每个符合性设置以及处于各符合性状态的设备总数。 它显示所有符合性策略中的所有设备符合性策略设置、应用策略设置的平台及不符合的设备数。

![查看不同策略中所有设置的列表](./media/compliance-policy-monitor/idc-10.png)

选择特定设置时，可以看到该设置针对的每个设备的“符合性状态”、“用户的电子邮件别名”、“设备模型”及“位置”。

> [!NOTE]
> 加入 Azure AD 的 Windows 10 设备可能显示系统帐户为不符合用户。 这是预期行为，不会影响设备的整体符合性。 

## <a name="view-status-of-device-policies"></a>查看设备策略的状态

可按平台来检查策略的不同状态。 例如，你有一个 macOS 符合性策略。 想要查看受此策略影响的设备，并了解是否存在冲突或故障。

此功能包含在设备状态报告中：

1. 选择“设备符合性” > “策略”。 随即会显示一个策略列表，包括平台（如果分配了策略）以及更多详细信息。
2. 选择一个策略 >“概述”。 在此视图中，策略分配包括以下状态：

    - 已成功：策略已应用
    - 错误：无法应用策略。 此消息通常与链接到错误说明的错误代码一起显示。 
    - 冲突：两个设置应用于同一设备，Intune 无法解决冲突。 管理员应进行审核。
    - 挂起：设备尚未使用 Intune 签入，无法接收策略。 
    - 不适用：设备无法接收策略。 例如，策略更新了 iOS 11.1 的特定设置，但设备使用的是 iOS 10。 

3. 若要查看使用此策略的设备的详细信息，请选择其中一种状态。 例如，选择“已成功”。 在下一个窗口中，将列出特定设备的详细信息，包括设备名称和部署状态。

## <a name="how-intune-resolves-policy-conflicts"></a>Intune 如何解决策略冲突
多个 Intune 策略应用到设备时可能会发生策略冲突。 如果策略设置重叠，Intune 将使用以下规则解决所有冲突：

- 如果冲突的设置来自 Intune 配置策略和合规性策略，那么合规性策略中的设置优先于配置策略中的设置。 即使配置策略中的设置更安全，也会发生这种情况。

- 如果部署了多个符合性策略，Intune 将使用其中最安全的策略。
