---
title: "适用于 Windows 电脑的 Endpoint Protection | Microsoft Docs"
description: "使用提供对恶意软件威胁的实时防护的 Endpoint Protection 保障托管计算机的安全。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 6e2658cdfcd0b78a254c375fe39b67f7ef9afad6
ms.lasthandoff: 12/10/2016


---

# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>使用适用于 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows PC 的安全
通提供对恶意软件威胁的实时防护、使恶意软件定义保持最新以及自动扫描计算机的 Endpoint Protection，Microsoft Intune 可帮助保障托管计算机的安全。 Endpoint Protection 还提供可帮助你管理和监视恶意软件攻击的工具。

如果你尚未在计算机上安装 Intune 客户端，请参阅[使用 Microsoft Intune 安装 Windows 电脑客户端](install-the-windows-pc-client-with-microsoft-intune.md)。

使用以下各部分的信息来帮助你配置、部署和监视 Endpoint Protection。

## <a name="choose-when-to-use-endpoint-protection"></a>选择何时使用 Endpoint Protection
IT 管理员的主要工作之一是保持所管理的计算机中没有恶意软件和病毒。 在将 Intune 部署到组织中的 Windows PC 之前，你应通过选择下列选项之一并配置其关联的策略设置来决定如何保护计算机：

|你希望：|Endpoint Protection 策略设置|更多信息|
|--------------|---------------------------------------|--------------------|
|仅当未安装第三方 Endpoint Protection 应用程序时，才使用 Microsoft Intune Endpoint Protection。<br /><br />在未安装第三方 Endpoint Protection 应用程序的所有计算机上，可以使用 Microsoft Intune Endpoint Protection。|安装 Endpoint Protection =“是”<br /><br />启用 Endpoint Protection =“是”<br /><br />安装 Endpoint Protection，即使安装了第三方 Endpoint Protection 应用程序也不例外 =“否”|如果检测到第三方 Endpoint Protection 应用程序，则表明未安装 Microsoft Intune Endpoint Protection，或者此前安装过，但已被卸载。|
|即使安装了第三方 Endpoint Protection 应用程序，仍使用 Microsoft Intune Endpoint Protection。<br /><br />采用此将同时运行 Microsoft Intune Endpoint Protection 和第三方 Endpoint Protection 应用程序。 由于存在潜在的性能问题，不建议采用此配置。 |安装 Endpoint Protection =“是”<br /><br />启用 Endpoint Protection =“是”<br /><br />安装 Endpoint Protection，即使安装了第三方 Endpoint Protection 应用程序也不例外 =“是”|何时使用：<br /><br />- 要切换为使用 Microsoft Intune Endpoint Protection。<br />-   将部署使用 Microsoft Intune Endpoint Protection 的新客户端。<br />- 升级任何将使用 Microsoft Intune Endpoint Protection 的客户端。|
|在没有 Microsoft Intune Endpoint Protection 的情况下使用 Intune 作为替代，你将依赖于第三方 Endpoint Protection 应用程序。|安装 Endpoint Protection =“否”|如果未使用第三方 Endpoint Protection 应用程序，则不建议使用此配置，因为它可能会使组织的计算机面临恶意软件或其他攻击的威胁。<br /><br />未安装 Microsoft Intune Endpoint Protection，如果之前已安装，则已卸载。|
若要从当前 Endpoint Protection 应用程序切换到 Microsoft Intune Endpoint Protection，请执行以下操作：

1.  向那些计算机部署 Intune 客户端软件时，让当前 Endpoint Protection 应用程序一直运行。

2.  确认 Microsoft Intune Endpoint Protection 已安装并且正在帮助保护客户端计算机的安全。

3.  通过以下方法删除第三方端点保护软件：

    -   使用 Intune 软件分发部署第三方 Endpoint Protection 应用程序制造商提供的软件删除工具。 有关详细信息，请参阅[使用 Microsoft Intune 部署应用](deploy-apps.md)。

    -   手动删除第三方 Endpoint Protection 应用程序。

> [!NOTE]
> Intune 将不会自动卸载第三方 Endpoint Protection 应用程序。

## <a name="configure-microsoft-intune-endpoint-protection"></a>配置 Microsoft Intune Endpoint Protection
使用以下步骤可帮助你配置适用于 Microsoft Intune 的 Endpoint Protection。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“**策略**” > “**添加策略**”。

2.  展开“计算机管理”，然后选择“Microsoft Intune 代理设置”。 选择“创建并部署自定义策略”，为 Endpoint Protection 设置指定策略。 然后选择“创建策略”按钮。

你可以使用建议的设置，或对设置进行自定义。 如果需要有关如何创建和部署策略的详细信息，请参阅[使用 Microsoft Intune 计算机客户端的常见 Windows PC 管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)主题。

  ![Endpoint Protection 设置](./media/pol-sa-pc-endpoint-policy.png)

你可以在“策略”工作区的“所有策略”页上查看部署的 Endpoint Protection 策略。

## <a name="specify-endpoint-protection-service-settings"></a>指定 Endpoint Protection 服务设置

|策略设置|详细信息|
|------------------|--------------------|
|**安装 Endpoint Protection**|设置为“是”即可在被管理的计算机上安装 Endpoint Protection。 如果在安装期间检测到第三方 Endpoint Protection 应用程序，则将不安装 Endpoint Protection，除非将**即使安装了第三方 Endpoint Protection 应用程序，也安装 Endpoint Protection** 设置为“是”。 **注意：**Intune Endpoint Protection 已默认安装在托管计算机上。 如果不希望在收管理的计算机上安装 Endpoint Protection，则必须将此策略显式设置为“否”。 如果之前安装了 Endpoint Protection，且该策略已更新为“否”，则 Endpoint Protection 客户端将卸载。<br />建议的值： **是**|
|**即使安装了第三方 Endpoint Protection 应用程序，仍要安装 Endpoint Protection**|设置为“是”后，即使检测到第三方 Endpoint Protection 应用程序也能安装 Microsoft Intune Endpoint Protection。<br /><br />建议的值： **是**|
|**启用 Endpoint Protection**|设置为“是”可在具有 Endpoint Protection 客户端的计算机上启用 Microsoft Intune Endpoint Protection。<br /><br />如果设置为“否”，并且安装了 Microsoft Intune Endpoint Protection，则不向用户显示 Endpoint Protection 客户端用户界面，并且所有保护功能处于非活动状态。<br /><br />建议的值： **是**|
|**禁用客户端 UI**|设置为“是”即可向用户隐藏 Microsoft Intune Endpoint Protection 客户端用户界面（重启客户端计算机后才能生效）。<br /><br />建议的值： **否**|
|**即使安装了第三方 Endpoint Protection 应用程序，仍要安装 Endpoint Protection**|设置为“是”后，即使检测到第三方 Endpoint Protection 应用程序也能强制安装 Microsoft Intune Endpoint Protection。<br /><br />建议的值： **否**|
|**在修正恶意软件之前创建系统还原点**|设置为“是”  以在任何恶意软件修正开始之前创建 Windows 系统还原点。<br /><br />建议的值： **是**|
|**跟踪已解决的恶意软件(天)**|让 Endpoint Protection 跟踪解决的恶意软件一段指定的时间，以便你能够手动检查以前感染的计算机。<br /><br />可以指定从 0 到 30 天的值。<br /><br />建议的值： **7 天**|
如果将“安装 Endpoint Protection”和“启用 Endpoint Protection”设置的策略值设置为“是”，并将“即使安装了第三方 Endpoint Protection 应用程序，仍安装 Endpoint Protection”的策略值设置为“否”，则 Microsoft Intune Endpoint Protection 将会检测是否安装了其他 Endpoint Protection 应用程序。 这意味着不会安装 Endpoint Protection（若已安装则将其卸载）。 但是，Microsoft Intune Endpoint Protection 会报告 Intune 中其他 Endpoint Protection 应用程序的运行状况。

  当潜在威胁（如病毒和间谍软件）试图在电脑上进行安装或运行时，Microsoft Security Essentials 可通过实时保护发出提醒。 出现这种情况时，你会在任务栏右侧的通知区域中看到一条消息。

### <a name="specify-real-time-protection-settings"></a>指定实时保护设置

|策略设置|详细信息|
|------------------|--------------------|
|**启用实时保护**|启用对所访问的所有文件和应用程序的监视和扫描。 在任何恶意文件和应用程序能够在计算机上运行之前，此设置还会阻止这些文件和应用程序。<br /><br />建议的值： **是**|
|**扫描所有下载**|启用对从 Internet 下载到计算机的所有文件和附件的扫描。<br /><br />建议的值： **是**|
|**监视计算机上的文件和程序活动**|启用对计算机上的传入文件和传出文件以及程序活动的监视。 利用此设置，Endpoint Protection 可监视文件和程序何时开始运行，并将它们所执行的任何操作或针对它们执行的操作的相关信息通知你。<br /><br />建议的值： **是**|
|**受监视的文件**|允许选择只监视传入文件、传出文件或所有文件。<br /><br />建议的值： **监视所有文件**|
|**启用行为监视**|确保 Microsoft Intune Endpoint Protection 可检查客户端计算机上特定模式的可疑活动。<br /><br />建议的值： **是**|
|**启用网络检查系统**|在客户端计算机上启用网络检查系统 (NIS)。 NIS 使用 [Microsoft Malware Protection Center（Microsoft 恶意软件防护中心）](http://go.microsoft.com/fwlink/?LinkId=234249) 中的已知漏洞签名来帮助检测和阻止恶意网络流量。<br /><br />建议的值： **是**|

  ![Endpoint Protection 的实时设置](./media/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>指定扫描计划设置

|策略设置|更多信息|
|------------------|--------------------|
|**计划每日一次快速扫描**|计划对计算机上的常用文件和重要系统文件每天进行一次快速扫描。 此快速扫描对性能的影响最小。<br /><br />建议的值： **是**|
|**如果错过两次连续的扫描，则运行快速扫描**|配置 Endpoint Protection 以在计算机错过两次连续快速扫描的情况下自动运行快速扫描。<br /><br />建议的值： **是**|
|**计划完全扫描**|配置对本地计算机硬盘上的所有文件和资源进行完全扫描。 此扫描可能需要一些时间，并可能会影响计算机性能（具体时间取决于扫描的文件和资源的数目）。<br /><br />建议的值： **否**|
|**如果错过两次连续的完全扫描，则运行完全扫描**|配置 Endpoint Protection 以在计算机错过两次连续扫描的情况下自动运行完全扫描。<br /><br />建议的值：未配置|

### <a name="specify-scan-options-settings"></a>指定扫描选项设置

|策略设置|详细信息|
|------------------|--------------------|
|**在安装 Endpoint Protection 后运行完全扫描**|设置为“是”Endpoint Protection 在计算机上安装之后自动运行一次完全系统扫描。 此扫描仅在计算机空闲时运行，以最大程度减小对用户工作效率的影响。<br /><br />建议的值： **是**|
|**需要在删除恶意软件后执行后续操作时自动运行完全扫描**|设置为“是”以让 Endpoint Protection 在恶意软件删除之后在计算机上自动运行一次完全系统扫描，以帮助确认其他文件未受影响。<br /><br />建议的值： **是**|
|**仅在计算机空闲时才开始计划的扫描**|设置为“是”  以在计算机处于使用状态时防止计划扫描开始，以避免对用户工作效率造成任何损失。<br /><br />建议的值： **是**|
|**在开始扫描之前检查最新的恶意软件定义**|设置为“是”以让 Endpoint Protection 在开始在计算机上扫描之前自动检查是否有最新的恶意软件定义。<br /><br />建议的值： **是**|
|**扫描存档文件**|设置为“是”以将 Endpoint Protection 配置为在计算机上的存档文件（如 .zip 或 .cab 文件）中扫描恶意软件。<br /><br />建议的值： **否**|
|**扫描电子邮件**|设置为“是”以将 Endpoint Protection 配置为当电子邮件到达计算机上时对其进行扫描。<br /><br />建议的值： **是**|
|**扫描从网络共享文件夹中打开的文件**|设置为“是”以将 Endpoint Protection 配置为对从网络上的共享文件夹中打开的文件进行扫描。 这些通常是使用通用命名约定 (UNC) 路径访问的文件。 启用此功能可能会导致具有只读访问权限的用户遇到问题，因为他们无法删除恶意软件。<br /><br />建议的值： **否**|
|**扫描映射的网络驱动器**|设置为“是”以将 Endpoint Protection 配置对映射的网络驱动器上的文件进行扫描。 启用此功能可能会导致具有只读访问权限的用户遇到问题，因为他们无法删除恶意软件。<br /><br />建议的值： **否**|
|**扫描可移动驱动器**|设置为“是”以将 Endpoint Protection 配置为当你在计算机上运行完全扫描时在可移动驱动器（如 USB 闪存驱动器）上扫描恶意软件和不需要的软件。<br /><br />建议的值： **是**|
|**在扫描期间限制 CPU 使用率**|设置在计算机上进行计划扫描期间可使用的最大 CPU 使用率百分比。 可以将此值设置为 1% 到 100%。<br /><br />建议的值： **50%**|

### <a name="choose-default-actions-settings"></a>选择默认操作设置

“选择 Endpoint Protection 处理以下警报级别的恶意软件的方式”设置指定在检测到各种警报级别的恶意软件时 Endpoint Protection 采取的默认操作。 对于每个警报级别，你可以删除恶意软件、将其隔离，或者采取 Microsoft 建议的操作。

建议值：“建议的操作”，可确保 Endpoint Protection 推荐操作。   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>决定是否选择排除的文件和文件夹设置

“在运行扫描或使用实时保护时要排除的文件和文件夹”设置在运行扫描时或在计算机上使用实时保护时排除特定文件或文件夹。

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>决定是否选择排除的进程设置

“在运行扫描或使用实时保护时要排除的进程”让你能在计算机上运行扫描或使用实时保护时排除特定的进程。 只能排除具有下列扩展名的文件：**.exe**、**.com** 或 **.scr**。

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>决定是否选择排除的文件类型设置

“在运行扫描或使用实时保护时要排除的文件扩展名”设置让你能在计算机上运行扫描或使用实时保护时排除特定的文件扩展名。

### <a name="specify-microsoft-active-protection-service-settings"></a>指定 Microsoft Active Protection Service 设置
Microsoft Active Protection Service 是一个可帮助你决定如何应对潜在威胁的在线社区。 该社区还可帮助防止新的恶意软件感染的传播。 可以通过选择“是”来“加入 Microsoft Active Protection Service”，然后指定“成员资格级别”：
  - “基本”- 将有关检测到的恶意软件的基本信息发送到 Microsoft。 这包括软件来自何处、你实施的或 Endpoint Protection 自动实施的操作，以及这些操作是否成功等。
  - “高级”- 将有关恶意软件、间谍软件和可能不需要的软件的详细信息发送到 Microsoft。 这包括软件的位置、文件名、软件如何工作和它如何影响计算机等信息。

还可以**接收基于 Microsoft Active Protection Service 报表的动态定义**。

## <a name="choose-management-tasks-for-endpoint-protection"></a>选择 Endpoint Protection 的管理任务
下列任务可帮助你在运行 Endpoint Protection 的被管理的计算机上执行各种管理任务：
 - 更新恶意软件定义
  - Intune 控制台 - 从“组”工作区中，选择要更新的计算机。 选择“远程任务”&gt;更新恶意软件定义”。
  - 被管理的计算机 - 从 Windows 通知区域中启动 Endpoint Protection 客户端软件。 选择“更新”选项卡，然后选择“更新”。
 - 运行恶意软件扫描：
  - Intune 控制台 - 从“组”工作区中，选择要扫描的计算机。 选择“运行完全恶意软件扫描”或“运行快速恶意软件扫描”。
  - 被管理的计算机 - 从 Windows 通知区域中启动 Endpoint Protection 客户端软件。 选择“快速”、“完全”或“自定义”，然后选择“立即扫描”。

可通过选择 Intune 控制台右下角的“远程任务”链接来查看远程任务的状态。 “远程任务状态”当前远程任务、任务状态、设备名称以及报告的任何错误。 还可提供适用的故障排除信息链接。

## <a name="monitor-endpoint-protection"></a>监视 Endpoint Protection
通过监视计算机上的恶意软件状态 **保护** 工作区 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)。 此工作区包含两页：
 - “Protection 概要”以链接的形式显示重要问题，你可以选择这些链接来了解详细信息。 可能显示的问题包括：
  - “需要跟进的恶意软件实例” – 单击链接以查看恶意软件问题的列表，包括为解决问题所需采取的跟进操作。 你可以进一步探索此列表，查看哪些计算机受到影响。
  - “具有需要跟进的恶意软件的计算机” – 单击链接以查看具有未解决的恶意软件问题的所有计算机，以及为解决问题所需采取的跟进操作。
  - “不受保护的设备”– 单击链接以查看由于未安装软件或存在错误而未受任何 Endpoint Protection 软件保护的计算机。 选择一台计算机以查看更多详细信息。
  - “正在运行另一个 Endpoint Protection 应用程序的设备”– 单击链接以查看正在运行第三方 Endpoint Protection 应用程序的计算机。
 - “所有恶意软件” - 显示在计算机上找到的所有活动恶意软件的列表。 可以探索此列表，查看受某个特定恶意软件影响的所有计算机，或者你可以选择下列任务之一：
  - “查看属性”– 打开包含所选恶意软件详细信息的页面。
  - “了解此恶意软件”– 打开 Microsoft 恶意软件防护中心中包含恶意软件详细信息的主题。

> [!IMPORTANT]
> 直到已安装客户端，并管理至少一台计算机客户端，“保护”工作区才会显示在管理控制台中。

  ![监视 Endpoint Protection](./media/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>如何在计算机上查看恶意软件的最近检测路径
Intune 可以在设备上显示多达 10 个最近检测到的恶意软件实例的路径。 **“最近检测路径”** 默认处于禁用状态。 启用此视图：

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，选择“组” > “所有设备” > “恶意软件”。

2.  右键单击列标题。 将显示可用列的列表。

3.  在列表中选择“最近检测路径”复选框。 将出现“最近检测路径”列，并显示在设备上监视的多达 10 个最近的恶意软件实例。

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>在计算机上运行恶意软件扫描或更新恶意软件定义
Intune 可以在安装有 Intune 客户端的远程托管电脑上使用 Endpoint Protection 或 Windows Defender 运行完整或快速的恶意软件扫描。

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，转到“组” > 概述” > 所有设备” > “所有计算机”，然后选择你的目标计算机。

2. 选择“远程任务”下拉列表，然后选择要在远程计算机上运行的任务。




## <a name="need-more-help"></a>需要更多帮助？
有关更多帮助和支持，请参阅 [Microsoft Intune 中的 Endpoint Protection 疑难解答](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune)。

### <a name="see-also"></a>另请参阅
[保护 Windows 电脑的策略](policies-to-protect-windows-pcs-in-microsoft-intune.md)

