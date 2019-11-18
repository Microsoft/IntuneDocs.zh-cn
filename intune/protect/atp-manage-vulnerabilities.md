---
title: 使用 Intune 修正 Microsoft Defender ATP 发现的漏洞 - Azure | Microsoft Docs
description: 查看如何在 Intune 控制台中管理属于 Microsoft Defender 高级威胁防护 (ATP) 的威胁和漏洞管理中的安全任务。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a9529f5b3047a8d4ca2a1e9c22d2c4427761078c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754901"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>使用 Intune 修正由 Microsoft Defender ATP 标识的漏洞

将 Intune 与 Microsoft Defender 高级威胁防护 (ATP) 集成时，可以充分利用 ATP 威胁和漏洞管理 (TVM) 并使用 Intune 修正由 TVM 标识的终结点漏洞。 此集成带来了基于风险的方法来发现漏洞并对其设置优先级，可缩短整个环境的修正响应时间。

[威胁和漏洞管理](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt)属于 [Microsoft Defender 高级威胁防护](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)。

## <a name="how-integration-works"></a>集成的工作原理

将 Intune 连接到 Microsoft Defender 高级威胁防护后，ATP 会从托管设备中收到威胁和漏洞的详细信息。

在 Microsoft Defender 安全中心控制台中，ATP 安全管理员可查看有关终结点漏洞的数据。 然后，管理员使用单击来创建用于标记需修正的易受攻击的设备的安全任务。 安全任务会立即传递到 Intune 控制台，Intune 管理员可以在其中查看它们。 安全任务标识漏洞类型、优先级、状态和用于修正漏洞的步骤。 Intune 管理员选择接受或拒绝该任务。

接受任务后，Intune 管理员会通过 Intune 使用作为安全任务的一部分提供的指导修正漏洞。

修正的常见操作包括：

- **阻止**应用程序运行
- **部署**操作系统更新，从而缓解漏洞。
- **修改**注册表值。
- **禁用**或**启用**某个配置，从而影响漏洞。
- **需要引起注意**警告管理员有关无合适建议的威胁。

示例工作流：

- 在 Microsoft Defender ATP 中，发现了名为 Contoso Media Player v4 的应用的漏洞，管理员会创建一个安全任务来更新该应用。 Contoso Media Player 是使用 Intune 部署的非托管应用。

  此安全任务显示在 Intune 控制台中，状态为“挂起”：

  ![在 Intune 控制台中查看安全任务的列表](./media/atp-manage-vulnerabilities/temp-security-tasks.png)

- Intune 管理员选择该安全任务以查看有关该任务的详细信息。  然后，管理员选择“接受”  ，这样会将 Intune 和 ATP 中的状态更新为“已接受”  。

  ![接受或拒绝安全任务](./media/atp-manage-vulnerabilities/temp-accept-task.png)

- 然后，管理员根据提供的指导修正任务。 指导因所需的修正类型而异。 修正指导（如果有）包括可在 Intune 中打开配置的相关窗格的链接。

  由于此示例中的媒体播放器不是托管应用，因此 Intune 只能提供文本说明。 如果应用已托管，则 Intune 可以提供下载更新版本的说明，并提供用于打开应用部署的链接，以便更新的文件可以添加到部署。

- 完成修正后，Intune 管理员将打开安全任务并选择“完成任务”  。  修正状态已针对 Intune 进行了更新，安全管理员在 ATP 中确认了修改后的漏洞状态。

## <a name="prerequisites"></a>必备条件  

**订阅**：

- Microsoft Intune  
- Microsoft Defender 高级威胁防护（[注册免费试用](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink)。）

**ATP 的 Intune 配置**：

- 配置与 Microsoft Defender ATP 的服务间连接。
- 将配置文件类型为 Microsoft Defender ATP（Windows 10 桌面版）  的设备配置策略部署到具有由 ATP 评估出来的风险的设备。

  有关如何将 Intune 设置为使用 ATP 的信息，请参阅[使用 Intune 中的条件访问强制执行 Microsoft Defender ATP 的符合性](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)。

## <a name="work-with-security-tasks"></a>使用安全任务

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“终结点安全”   > “安全任务”  。

3. 从列表中选择一项任务以打开显示有关该安全任务的其他详细信息的资源窗口。

   查看安全任务资源窗口时，可以选择其他链接：

   - 托管应用 - 查看易受攻击的应用。 多个应用中出现漏洞时，你会看到筛选后的应用列表。
   - 设备 - 查看易受攻击的设备  的列表，你可以在其中链接到具有该设备上的漏洞的更多详细信息的条目。
   - 请求者 - 使用该链接将邮件发送给提交了此安全任务的管理员。
   - 说明 - 打开安全任务时读取由请求者提交的自定义消息。

4. 选择“接受”  或“拒绝”  将通知发送到 ATP 以执行计划的操作。 接受或拒绝任务后，可以提交发送到 ATP 的说明。

5. 接受任务后，重新打开安全任务（如果已关闭），然后按照修正详细信息修正漏洞。 安全任务详细信息中 ATP 提供的说明因所涉及的漏洞而异。

   可以这样做时，修正说明包括可在 Intune 控制台中打开相关配置对象的链接。

6. 完成修正步骤后，打开安全任务并选择“完成任务”  。  此操作将更新 Intune 和 ATP 中的安全任务状态。

修正成功后，根据已修正设备中的新信，ATP 中的风险危险性分数可能会下降。

## <a name="next-steps"></a>后续步骤
了解有关 Intune 和 [Microsoft Defender ATP](advanced-threat-protection.md) 的详细信息。

查看 Intune [移动威胁防御](mobile-threat-defense.md)。

查看 Microsoft Defender ATP 中的[威胁和漏洞管理仪表板](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights)。
