---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune 提供特定的报表类型以及集中视图（包含一致且及时的数据）。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391937"
---
# <a name="intune-reports"></a>Intune 报表
利用 Microsoft Intune 报表，你可以更有效地主动在整个组织中监视终结点的运行状况和活动，还可以在 Intune 之间提供其他报表数据。 例如，你将能够查看有关设备符合性、设备运行状况和设备趋势的报表。 此外，你还可以创建自定义报表以获取更具体的数据。 

> [!NOTE]
> Intune 报表更改将在一段时间内逐步推出，以帮助你准备并适应新的结构。

报表类型划分为以下主要区域：
- **操作** - 提供及时的目标数据，可帮助你集中精力和采取措施。 管理员、行业专家和支持人员会发现这些报表最有用。
- **组织** - 提供总体视图的更广泛摘要，例如设备管理状态。 经理和管理员会发现这些报表最有用。
- **历史** - 提供一段时间内的模式和趋势。 经理和管理员会发现这些报表最有用。
- **专业** - 允许使用原始数据创建自己的自定义报表。 管理员会发现这些报表最有用。

报表框架提供了一致且更全面的报表体验。 可用报表提供以下功能：
- **搜索和排序** - 无论数据集的大小如何，都可以跨每个列进行搜索和排序。
- **数据分页** – 可以基于分页（逐页或跳转到特定页面）来扫描数据。
- **性能** - 可以快速生成和查看从大型租户创建的报表。
- **导出** – 可快速导出从大型租户生成的报表数据。

### <a name="who-can-access-the-data"></a>谁可以访问数据？

拥有以下权限的用户可以查看日志：

- 全局管理员
- Intune 服务管理员
- 分配到拥有“读取”  权限的 Intune 角色的管理员

## <a name="non-compliant-devices-report-operational"></a>不符合设备报表（操作）
不符合设备报表显示了通常由支持人员或管理员角色用来识别问题并帮助修正问题的数据。 这些报表中找到的数据是即时的，它会调用意外的行为且可操作。 该报表与工作负荷一起提供，从而使不符合设备报表可访问，而无需浏览至活动工作流之外。 此报表提供筛选、搜索、分页和排序功能。 此外，还可以向下钻取以帮助解决问题。

你可以使用以下步骤查看“不符合设备”  报表：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备符合性”   > “不符合设备”  。

    ![不符合设备报表](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>设备符合性报表（组织）
设备符合性报表在本质上是广泛的，可提供更传统的数据报表视图来标识聚合指标。 此报表旨在处理大型数据集，以获取完整的设备符合性图。 例如，设备符合性的设备符合性报表显示了设备的所有符合性状态，以提供更广泛的数据视图，不管数据集的大小如何。 除了便捷直观地可视化了聚合指标，此报表还显示了记录的完整明细。 可以通过应用筛选器并选择“生成报表”按钮来生成此报表。 这将刷新数据以显示最新状态，并且能够查看构成聚合数据的各个记录。 类似于新框架中的大多数报表，可以对这些记录进行排序和搜索，以专注于所需的信息。 

若要查看生成的设备状态报表，可以执行以下步骤：
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“报表”  以查看报表摘要。
3. 选择“设备符合性”  。
4. 选择“符合性状态”  、“OS”  和“所有权”  筛选器以优化报表。
5. 单击“生成报表”  （或再次单击“生成”  ）以检索当前数据。

    ![设备符合性报表](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > 此设备符合性  报表提供了上次生成报告时的时间戳。 

有关信息，请参阅[使用 Intune 中的条件访问强制执行 Microsoft Defender ATP 的符合性](~/protect/advanced-threat-protection.md)。

## <a name="reports-summary"></a>报表摘要 

设备符合性报表可作为“报表”  工作负荷中的摘要报表。 执行以下步骤来查看设备符合性报表：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“报表”  以查看报表摘要。

    ![Intune 报表摘要](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>设备符合性趋势报表（历史）
管理员和架构师更有可能使用设备符合性趋势报表来确定设备符合性的长期趋势。 显示一段时间内的聚合数据，可用于做出未来投资决策、推动过程改进或提示调查任何异常。 还可以应用筛选器来查看特定趋势。 此报表提供的数据是当前租户状态的快照（近乎实时）。 

设备符合性趋势的设备符合性趋势报表可显示一段时间内的设备符合性状态趋势。 你可以确定符合性高峰发生的位置，并相应地集中时间和精力。

你可以使用以下步骤查看“趋势”  报表：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“报表”   > “趋势”  ，以查看 60 天内的设备符合性趋势。

    ![Intune 趋势报表](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure Monitor 集成报表（专业）
你可以自定义自己的报表以获取所需数据。 可使用 [Log Analytics](reports.md#log-analytics) 和 [Azure Monitor 工作簿](reports.md#workbooks)通过 [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) 获取报表中的数据。 通过这些解决方案，可以创建自定义查询、配置警报，并使仪表板以所需方式显示设备符合性数据。 此外，你还可以将活动日志保留在你的 Azure 存储帐户中，使用[安全信息和事件管理 (SIEM) 工具](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)将活动日志与报表集成，并将报表关联到 Azure AD 活动日志。 除了导入仪表板以满足自定义报表需求外，还可以使用 Azure Monitor 工作簿。

> [!NOTE]
> 复杂的报表功能需要 Azure 订阅。

此专业报表示例将设备所有权数据与自定义报表中的平台注册数据相关联。 然后，可以在 Azure Active Directory 门户中的现有仪表板上显示此自定义报表。

你可以使用以下步骤创建和查看自定义报表：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“报表”   > “诊断设置”  以添加[诊断设置](reports.md#diagnostic-settings)。

    ![Intune 报表摘要](./media/intune-reports/intune-reports-04.png)

3. 单击“添加诊断设置”  以显示“诊断设置”  窗格。 
4. 在“名称”  中添加诊断设置的名称。 
5. 选择“发送到 Log Analytics”  和“DeviceComplianceOrg”  设置。

    ![Intune 报表摘要](./media/intune-reports/intune-reports-04a.png)

6. 单击 **“保存”** 。
7. 接下来，选择“Log analytics”  ，使用 [Log Analytics](reports.md#log-analytics) 创建并运行新的日志查询。

   ![Log Analytics - 日志查询](./media/intune-reports/intune-reports-05.png)

8. 选择“工作簿”  以使用 [Azure Monitor 工作簿](reports.md#workbooks)创建或打开交互式报表。

   ![工作簿 - 交互式报表](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>诊断设置
每个 Azure 资源都需要其自己的诊断设置。 诊断设置为资源定义以下内容：

- 发送到设置中所定义目标的日志和指标数据类别。 不同资源类型的可用类别将有所不同。
- 用于发送日志的一个或多个目标。 当前目标包括 Log Analytics 工作区、事件中心和 Azure 存储。
- 存储在 Azure 存储中的数据的保留策略。

单个诊断设置可以定义每一个目标。 如果要将数据发送到多个特定目标类型（例如，两个不同的 Log Analytics 工作区），请创建多个设置。 每个资源最多可以有 5 个诊断设置。

有关诊断设置的详细信息，请参阅[创建诊断设置以收集 Azure 中的平台日志和指标](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings)。

### <a name="log-analytics"></a>日志分析
Log Analytics 是 Azure 门户中的主要工具，用于写入日志查询并以交互方式分析查询结果。 即使 Azure Monitor 的其他位置使用了日志查询，通常也可以首先使用 Log Analytics 来写入和测试查询。 有关使用 Log Analytics 和创建日志查询的详细信息，请参阅 [Azure Monitor 中的日志查询概述](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)。 

### <a name="workbooks"></a>工作簿
工作簿将文本、分析查询、Azure 指标和参数合并到丰富的交互式报表中。 工作簿可供有权访问同一 Azure 资源的任何其他团队成员编辑。 有关工作簿的详细信息，请参阅 [Azure Monitor 工作簿](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)。 此外，你还可以使用和参与制作工作簿模板。 有关详细信息，请参阅 [Azure Monitor 工作簿模板](https://go.microsoft.com/fwlink/?linkid=867045)。

## <a name="next-steps"></a>后续步骤

详细了解以下技术：
- [博客 - Microsoft Intune 报表框架](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [什么是 Log Analytics？](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [日志查询](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Azure Monitor Log Analytics 入门](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor 工作簿](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [安全信息和事件管理 (SIEM) 工具](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
