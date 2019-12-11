---
title: 使用 Microsoft Intune 将日志路由到 Azure Monitor - Azure | Microsoft Docs
description: 使用“诊断设置”将 Microsoft Intune 中的审核日志和运行日志发送到 Azure 存储帐户、事件中心或 Log Analytics。 选择所需的数据保留时间，并查看不同规模租户的估算成本。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 95191d64-9895-4f2e-8c5b-f0e85be086d8
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66acf4d8b88097c3262f44493ab72b3900781eed
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504963"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>使用 Intune 将日志数据发送到存储、事件中心或 Log Analytics（预览版）

Microsoft Intune 包含可提供环境信息的内置日志：

- 审核日志  显示 Intune 中发生的各种事件或任务的详细信息。
- 运行日志（预览版）显示了注册成功/失败的用户和设备的详细信息，还显示了不符合条件的设备的详细信息  。
- **设备合规性运行日志（预览版）** 显示了 Intune 中设备合规性的运行报告以及有关非合规性设备的详细信息。

还可以将这些日志发送到 Azure Monitor 服务，包括存储帐户、事件中心和 Log Analytics。 具体而言，你可以：

* 将 Intune 日志存档到 Azure 存储帐户，以保留数据或存档一段指定时间。
* 使用常用的安全信息和事件管理 (SIEM) 工具（如 Splunk 和 QRadar）将 Intune 日志流式传输到 Azure 事件中心，以供分析。
* 通过将 Intune 日志流式传输到事件中心，将日志与你自己的自定义日志解决方案集成。
* 将 Intune 日志发送到 Log Analytics，对已连接数据启用丰富的可视化效果、监视和警报。

这些功能是 Intune中“诊断设置”  的一部分。

本文介绍了如何使用“诊断设置”  将日志数据发送到不同服务，提供了示例和成本估算，并回答了一些常见问题。 启用此功能后，日志将路由到所选的 Azure Monitor 服务。

## <a name="prerequisites"></a>必备条件

若要使用此功能，必须满足以下先决条件：

* Azure 订阅：如果没有 Azure 订阅，可以[注册免费试用版](https://azure.microsoft.com/free/)。
* 在 Azure 中有 Microsoft Intune 环境（租户）
* 用户担任 Intune 租户的全局管理员  或 Intune 服务管理员  角色。

需要以下服务之一（具体视要将审核日志数据路由到哪里而异）：

* 拥有 ListKeys  权限的 [Azure 存储帐户](https://docs.microsoft.com/azure/storage/common/storage-account-overview)。 建议使用常规存储帐户，而不是 blob 存储帐户。 有关存储定价信息，请参阅 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/calculator/?service=storage)。 
* 与第三方解决方案集成的 [Azure 事件中心命名空间](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace)。
* 用于将日志发送到 Log Analytics 的 [Azure Log Analytics 工作区](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)。

## <a name="send-logs-to-azure-monitor"></a>将日志发送到 Azure Monitor

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“监视”  下的“诊断设置”  。 第一次打开它时，需要启用它。 否则，请添加设置。

    ![在 Intune 中启用“诊断设置”以将日志发送到 Azure Monitor](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. 输入以下属性：

    - **名称**：输入诊断设置的名称。 此设置包括你输入的所有属性。 例如，输入 `Route audit logs to storage account`。
    - **存档到存储帐户**：将日志数据保存到 Azure 存储帐户。 若要保存或存档数据，请使用此选项。

        1. 选中此选项，再选择“配置”  。 
        2. 选择列表中的现有存储帐户，再单击“确定”  。

    - **流式传输到事件中心**：将日志流式传输到 Azure 事件中心。 若要使用 SIEM 工具（如 Splunk 和 QRadar）分析日志数据，请选中此选项。

        1. 选中此选项，再选择“配置”  。 
        2. 选择列表中的现有事件中心命名空间和策略，再单击“确定”  。

    - **发送到 Log Analytics**：将数据发送到 Azure Log Analytics。 若要对日志使用可视化效果、监视和警报，请选中此选项。

        1. 选中此选项，再选择“配置”  。 
        2. 新建工作区，并输入工作区详细信息。 或者，选择列表中的现有工作区，再单击“确定”  。

            [Azure Log Analytics 工作区](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)详细介绍了这些设置。

    - “日志”   > “审核日志”  ：选中此选项可以将 [Intune 审核日志](../monitor-audit-logs.md)发送到存储帐户、事件中心或 Log Analytics。 审核日志显示每个在 Intune 中带来更改的任务的历史记录，其中包括谁在何时执行了任务。

      如果选择使用存储帐户，还要输入所需的数据保留天数（保留期）。 若要永久保留数据，请将“保留期(天数)”  设置为“`0`”（零）。

    - “日志”   > “运行日志”  ：运行日志（预览版）显示了用户和设备在 Intune 中的注册状态（成功/失败），还有不符合条件的设备的详细信息。 选中此选项可以将注册日志发送到存储帐户、事件中心或 Log Analytics。

      如果选择使用存储帐户，还要输入所需的数据保留天数（保留期）。 若要永久保留数据，请将“保留期(天数)”  设置为“`0`”（零）。

      > [!NOTE]
      > 运行日志目前处于预览阶段。 若要提供反馈（包括运行日志中所含的信息），请转到 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback)。

    - **LOG** > **DeviceComplianceOrg**：设备合规性运行日志（预览版）显示了 Intune 中设备合规性的运行报告以及有关非合规性设备的详细信息。 选中此选项可以将合规性日志发送到存储帐户、事件中心或 Log Analytics。

      如果选择使用存储帐户，还要输入所需的数据保留天数（保留期）。 若要永久保留数据，请将“保留期(天数)”  设置为“`0`”（零）。
 
      > [!NOTE]
      > 设备合规性运行日志以预览版提供。 若要提供反馈（包括报告中所含的信息），请转到 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback)。

    完成后，设置如下所示： 

    ![将 Intune 审核日志发送到 Azure 存储帐户的示例图像](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. 单击“保存”以保存更改  。 此时，设置显示在列表中。 创建完成后，可以依次选择“编辑设置”   > “保存”  来更改设置。

## <a name="use-audit-logs-throughout-intune"></a>在整个 Intune 中使用审核日志

还可在 Intune 的注册、符合性、配置、设备和客户端应用等其他部分中导出审核日志。

例如，在使用设备符合性时导出审核日志：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备符合性” > “监视” > “审核日志”    ：

    ![选择审核日志，将 Intune 数据路由到 Azure Monitor 存储、事件中心或分析](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. 选择“导出数据设置”  。 如果未启用，可打开“诊断设置”  。 还可选择将日志发送到的位置，如[将日志发送到 Azure monitor](#send-logs-to-azure-monitor)（本文）中所述。

## <a name="cost-considerations"></a>成本注意事项

如果已有 Microsoft Intune 许可证，必须还要有 Azure 订阅，才能设置存储帐户和事件中心。 Azure 订阅通常是免费的。 不过，需要付费才能使用 Azure 资源，这包括用于存档的存储帐户和用于流式传输的事件中心。 数据量和成本因租户规模大小而异。

### <a name="storage-size-for-activity-logs"></a>活动日志的存储大小

每个审核日志事件占用大约 2KB 的数据存储。 对于拥有 100,000 个用户的租户，每天可能会发生大约 150 万个事件。 因此，每天可能需要大约 3GB 的数据存储。 由于写入操作通常每五分钟批量发生一次，因此每月应该可以执行大约 9,000 次写入操作。

下表显示了因租户规模大小而异的成本估算。 此外，它还包括美国西部的通用 v2 存储帐户，用于保留数据至少一年。 若要估算预期的日志数据量，请使用 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/details/storage/blobs/)。

**包含 100,000 个用户的审核日志**

| | |
|---|---|
|每天事件数| 150 万|
|估计的每月数据量| 90GB|
|估计的每月成本（美元）| $1.93|
|估计的每年成本（美元）| $23.12|

**包含 1,000 个用户的审核日志**

| | |
|---|---|
|每天事件数| 15,000|
|估计的每月数据量| 900 MB|
|估计的每月成本（美元）| $0.02|
|估计的每年成本（美元）| $0.24|

### <a name="event-hub-messages-for-activity-logs"></a>活动日志的事件中心消息

事件通常每五分钟批量处理一次，并作为这个时间范围内所有事件的一条消息发送。 事件中心消息的大小上限为 256KB。 如果时间范围内所有消息的总大小超过此值，则会发送多条消息。

例如，对于超过 100,000 个用户的大租户，每秒通常发生大约 18 个事件。 这相当于每五分钟发生 5,400 个事件（300 秒 × 18 个事件）。 每个事件的审核日志大约为 2KB。 这就相当于 10.8MB 数据。 因此，在五分钟时间间隔内，有 43 条消息发送到事件中心。

下表包含美国西部基本事件中心的每月估算成本，具体视事件数据量而异。 若要估算预期的日志数据量，请使用[事件中心定价计算器](https://azure.microsoft.com/pricing/details/event-hubs/)。

**包含 100,000 个用户的审核日志**

| | |
|---|---|
|每秒事件数| 18|
|每五分钟发生的事件数| 5,400|
|每个时间间隔内的数据量| 10.8MB|
|每个时间间隔内的消息数| 43|
|每月的消息数| 371,520|
|估计的每月成本（美元）| $10.83|

**包含 1,000 个用户的审核日志**

| | |
|---|---|
|每秒事件数|0.1 |
|每五分钟发生的事件数| 52|
|每个时间间隔内的数据量|104KB |
|每个时间间隔内的消息数|1 |
|每月的消息数|8,640 |
|估计的每月成本（美元）|$10.80 |

### <a name="log-analytics-cost-considerations"></a>Log Analytics 成本考虑因素

若要查看与管理 Log Analytics 工作区相关的成本，请参阅[通过控制 Log Analytics 中的数据量和保留期来管理成本](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)。

## <a name="frequently-asked-questions"></a>常见问题

查看常见问题解答，并了解 Azure Monitor 中 Intune 日志的所有已知问题。

### <a name="which-logs-are-included"></a>包含哪些日志？

使用此功能可以路由审核日志和运行日志（预览版）。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>操作执行后，相应的日志何时出现在事件中心内？

日志通常在操作执行后的几分钟内出现在事件中心内。 [什么是 Azure 事件中心？](https://docs.microsoft.com/azure/event-hubs/)提供了详细信息。

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>操作执行后，相应的日志何时出现在存储帐户中？

对于 Azure 存储帐户，延迟时间介于操作执行后的 5 分钟和 15 分钟之间。

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>如果管理员更改诊断设置的保留期，会发生什么情况？

新的保留策略应用于在更改后收集的日志。 在策略更改前收集的日志不受影响。

### <a name="how-much-does-it-cost-to-store-my-data"></a>存储数据的成本是多少？

存储成本具体视日志大小和选择的保留期而定。 有关租户的估算成本（视生成的日志量而定）列表，请参阅（本文中的）[活动日志的存储大小](#storage-size-for-activity-logs)。

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>将数据流式传输到事件中心的成本是多少？

流式传输成本具体视每分钟收到的消息数而定。 若要详细了解如何计算成本和根据消息数估算成本，请参阅（本文中的）[活动日志的事件中心消息](#event-hub-messages-for-activity-logs)。

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>如何将 Intune 审核日志与我的 SIEM 系统集成？

结合使用 Azure Monitor 与事件中心，将日志流式传输到 SIEM 系统。 首先，[将日志流式传输到事件中心](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)。 然后，通过已配置的事件中心[设置 SIEM 工具](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub)。 

### <a name="what-siem-tools-are-currently-supported"></a>目前支持哪些 SIEM 工具？

目前，[Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk)、QRadar 和 [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory)（打开新网站）支持 Azure Monitor。 若要详细了解连接器工作原理，请参阅[将 Azure 监视数据流式传输到事件中心以供外部工具使用](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)。

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>我能否在不使用外部 SIEM 工具的情况下访问事件中心内的数据？

是。 若要从自定义应用访问这些日志，可使用[事件中心 API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph)。

### <a name="what-data-is-stored"></a>存储什么数据？

Intune 不存储通过管道发送的任何数据。 Intune 将数据路由到租户授权的 Azure Monitor 管道。 有关详细信息，请参阅 [Azure Monitor 概述](https://docs.microsoft.com/azure/azure-monitor/overview)。

## <a name="next-steps"></a>后续步骤

* [将活动日志存档到存储帐户](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [将活动日志路由到事件中心](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [将活动日志与 Log Analytics 集成](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
