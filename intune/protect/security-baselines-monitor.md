---
title: 在 Microsoft Intune 中检查安全基线是否成功部署 - Azure | Microsoft Docs
description: 在 Microsoft Intune MDM 中，检查部署到用户和设备的安全基线的错误、冲突和成功状态。 了解如何使用 Intune 中的客户端日志和报告功能排除故障。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b7f14e939e7241cd34c01d73e9af822dea7acdc
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410144"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中监视安全基线和配置文件

Intune 提供了用于监视安全基线的多个选项。 可以监视应用到用户和设备的安全基线配置文件。 还可以监视实际基线，以及与建议值匹配（或不匹配）的任何设备。

本文介绍了这两个监视选项。

[Intune 中的安全基线](../security-baselines.md)详细介绍了 Microsoft Intune 中的安全基线功能。

## <a name="monitor-the-baseline-and-your-devices"></a>监视基线和设备

监视基线时，你根据 Microsoft 的建议深入了解设备的安全状态。 可以在 Intune 控制台的安全基线的“概述”窗格中查看这些见解。  首次分配基线后，最多 24 小时后会显示数据。 之后进行的更改最多六个小时后会显示。

若要查看基线和设备的监视数据，请登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 接下来，选择“终结点安全性”   > “安全基线”  ，然后选择一个基线并查看“概述”  窗格。

“概述”窗格提供两种监视状态的方法  ：

- **设备视图** - 基线的每个状态类别中的设备数量摘要。
- **按类别** - 一个视图，显示基线中的每个类别，并包含每个基线类别的每个状态组的设备百分比。

每个设备由以下状态之一表示，这些状态同时在“设备”视图和“按类别”视图中使用   ：

- **匹配基线** - 基线中的所有设置与建议的设置匹配。
- **不匹配基线** - 基线中至少有一个设置与建议的设置不匹配。
- **错误配置** - 至少一个设置未正确配置。 此状态表示设置处于冲突、错误或挂起状态。
- **不适用** - 至少一个设置不适用且未应用。

### <a name="device-view"></a>设备视图

“概述”窗格显示具有特定基线状态的设备数量的图表型摘要；已分配的 Windows 10 设备的安全基线状态  。

![检查设备状态](./media/security-baselines-monitor/overview.png)

当某设备具有基线中不同类别的不同状态时，该设备由单个状态表示。 用于表示设备的状态按以下优先顺序进行选择：错误配置、不匹配基线、不适用、匹配基线     。

例如，如果某设备有一个设置的类别为“错误配置”，且有一个或多个设置的类别为“不匹配基线”，则该设备的类别为“错误配置”    。

可以单击图表以深入了解和查看各种状态的设备的列表。 然后，可以从该列表中选择设备，查看其详细信息。 例如：

- 选择“设备配置”，然后选择状态为“错误”的配置文件  ：

  ![查看配置文件的状态](./media/security-baselines-monitor/device-configuration-profile-list.png)

- 选择有“错误”状态的配置文件。 此时，系统列出配置文件中的所有设置及其状态。 现在，可以滚动查找导致错误出现的设置：

  ![查看导致错误的设置](./media/security-baselines-monitor/profile-with-error-status.png)

使用此报告查看配置文件中导致问题出现的任何设置。 此外，还能获取部署到设备的策略和配置文件的更多详细信息。

> [!NOTE]
> 如果基线中的属性设置为“未配置”  ，此设置会遭忽略，且不会强制实施任何限制。 此属性不会显示在任何报告中。

### <a name="per-category-view"></a>“按类别”视图

“概述”窗格显示基线的“按类别”图表；按类别显示的安全基线状态  。  此视图显示基线中的每个类别，并标识归入每个类别各个状态的设备的百分比。

![按类别显示的状态视图](./media/security-baselines-monitor/monitor-baseline-per-category.png)

不显示“匹配基线”状态，直到 100% 的设备都报告了该类别的状态  。

可以通过选择列顶部的上下箭头图标，按每个列对按类别显示的视图进行排序。

## <a name="monitor-the-profile"></a>监视配置文件

通过监视配置文件，可以根据基线建议深入了解设备部署状态，而不是安全状态。

1. 在 Intune 中，依次选择“安全基线”  、基线和“已创建的配置文件”  。

2. 选择配置文件。 “概览”  中的图显示分配有此配置文件的设备数和用户数：

   ![查看分配有安全基线配置文件的设备数和用户数](./media/security-baselines-monitor/existing-profile-overview.png)

3. “管理”   > “属性”  下列出了基线中的所有设置。 还可以更改其中任何设置：

   ![查看和更新安全基线配置文件中的设置](./media/security-baselines-monitor/manage-settings.png)

4. 在“监视”  中，可以查看各个设备上配置文件的部署状态、每个用户的状态，以及基线中每个设置的状态：

   ![查看安全基线配置文件的其他监视选项](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>使用每个设置状态排除故障

已部署安全基线，但部署状态显示错误。 下面逐步介绍了对错误进行故障排除。

1. 在 Intune 中，依次选择“安全基线”  、基线和“已创建的配置文件”  。

2. 选择配置文件，在依次转到“监视”   > “每个设置状态”  下。

3. 此时，表中显示所有设置以及每个设置的状态。 选择“错误”  列或“冲突”  列，以查看导致错误出现的设置。

### <a name="mdm-diagnostic-information"></a>MDM 诊断信息

现在，你知道哪个设置有问题。 下一步是确定此设置为什么会导致错误或冲突出现。

Windows 10 设备上内置有 MDM 诊断信息报告。 此报告包含默认值、当前值，不仅会列出策略，还会显示是部署到设备还是部署到用户等。 使用此报告有助于确定设置为什么会导致冲突或错误出现。

1. 在设备上，依次转到“设置”   > “帐户”   > “访问工作或学校”  。

2. 选择帐户，再依次选择“信息”   > “高级诊断报告”   > “生成报告”  。

3. 选择“导出”  ，再打开所生成的文件。

4. 在报告的不同部分中查找错误或冲突设置。

  例如，在“已注册的配置源和目标资源”  部分或“非托管策略”  部分中查找。 这样可能就会知道设置为什么会导致错误或冲突出现。

[在 Windows 10 中诊断 MDM 故障](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)详细介绍了此内置报告。

> [!TIP]
> - 一些设置还列出了 GUID。 可以在本地注册表 (regedit) 中搜索此 GUID 是否是任何设定值。
> - 事件查看器日志可能还包括有问题设置的一些错误信息（依次转到“事件查看器”   > “应用和服务日志”   > “Microsoft”   > “Windows”   > “DeviceManagement-Enterprise-Diagnostics-Provider”   > “管理员”  ）。

## <a name="next-steps"></a>后续步骤

[监视设备配置文件](../configuration/device-profile-monitor.md)和[查看一些常见问题和解决方法](../configuration/device-profile-troubleshoot.md)。
