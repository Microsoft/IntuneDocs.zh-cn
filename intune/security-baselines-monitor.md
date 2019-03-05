---
title: 在 Microsoft Intune 中检查安全基线是否成功部署 - Azure | Microsoft Docs
description: 在 Microsoft Intune MDM 中，检查部署到用户和设备的安全基线的错误、冲突和成功状态。 了解如何使用 Intune 中的客户端日志和报告功能排除故障。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b853d42efc247f6080cc4ed6ad8b4943b85b3215
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230816"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>在 Microsoft Intune 中监视安全基线和配置文件

使用安全基线时，有不同的监视选项可用。 可以监视应用到用户和设备的安全基线配置文件。 还可以监视实际基线，以及与建议值匹配（或不匹配）的任何设备。

本文介绍了这两个监视选项。

[Intune 中的安全基线](security-baselines.md)详细介绍了 Microsoft Intune 中的安全基线功能。

## <a name="monitor-the-baseline-and-your-devices"></a>监视基线和设备

监视基线时，你根据 Microsoft 的建议深入了解设备的安全状态。

> [!NOTE]
> 在基线首次分配后，报告最多可能需要 24 小时才能更新。 此后，报告最多可能需要 6 小时才能更新。

1. 在 [Azure 门户](https://portal.azure.com/)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 依次选择“安全基线(预览版)”和基线。
3. “概览”中的图显示有多少台设备受选定基线影响，以及不同的状态：

    ![检查设备状态](./media/security-baselines-monitor/overview.png)

    图中显示以下状态：

    - **与基线匹配**：基线中的所有设置与建议的设置匹配。
    - **与基线不匹配**：基线中至少有一个设置与建议的设置不匹配。
    - **错误配置**：至少一个设置未正确配置。 此状态表示设置处于冲突、错误或挂起状态。
    - **不适用**：至少一个设置不适用且未应用。

4. 选择设备数字不是零的状态之一。 例如，选择“错误配置”状态。

5. 此时，系统列出有此状态的所有设备。 选择特定设备可以获取更多详细信息。 

    在下面的示例中，依次选择“设备配置”和有“错误”状态的配置文件：

    ![检查设备状态](./media/security-baselines-monitor/device-configuration-profile-list.png)

    选择有“错误”状态的配置文件。 此时，系统列出配置文件中的所有设置及其状态。 现在，可以滚动查找导致错误出现的设置：

    ![查看导致错误的设置](./media/security-baselines-monitor/profile-with-error-status.png)

使用此报告查看配置文件中导致问题出现的任何设置。 此外，还能获取部署到设备的策略和配置文件的更多详细信息。

> [!NOTE]
> 如果基线中的属性设置为“未配置”，此设置会遭忽略，且不会强制实施任何限制。 此属性不会显示在任何报告中。

## <a name="monitor-the-profile"></a>监视配置文件

通过监视配置文件，可以根据基线建议深入了解设备部署状态，而不是安全状态。

1. 在 Intune 中，依次选择“安全基线”、基线和“已创建的配置文件”。

2. 选择配置文件。 “概览”中的图显示分配有此配置文件的设备数和用户数：

    ![查看分配有安全基线配置文件的设备数和用户数](./media/security-baselines-monitor/existing-profile-overview.png)

3. “管理” > “属性”下列出了基线中的所有设置。 还可以更改其中任何设置：

    ![查看和更新安全基线配置文件中的设置](./media/security-baselines-monitor/manage-settings.png)

4. 在“监视”中，可以查看各个设备上配置文件的部署状态、每个用户的状态，以及基线中每个设置的状态：

    ![查看安全基线配置文件的其他监视选项](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>使用每个设置状态排除故障

已部署安全基线，但部署状态显示错误。 下面逐步介绍了对错误进行故障排除。

1. 在 Intune 中，依次选择“安全基线”、基线和“已创建的配置文件”。
2. 选择配置文件，在依次转到“监视” > “每个设置状态”下。
3. 此时，表中显示所有设置以及每个设置的状态。 选择“错误”列或“冲突”列，以查看导致错误出现的设置。

### <a name="mdm-diagnostic-information"></a>MDM 诊断信息

现在，你知道哪个设置有问题。 下一步是确定此设置为什么会导致错误或冲突出现。 

Windows 10 设备上内置有 MDM 诊断信息报告。 此报告包含默认值、当前值，不仅会列出策略，还会显示是部署到设备还是部署到用户等。 使用此报告有助于确定设置为什么会导致冲突或错误出现。

1. 在设备上，依次转到“设置” > “帐户” > “访问工作或学校”。
2. 选择帐户，再依次选择“信息” > “高级诊断报告” > “生成报告”。
3. 选择“导出”，再打开所生成的文件。
4. 在报告的不同部分中查找错误或冲突设置。

  例如，在“已注册的配置源和目标资源”部分或“非托管策略”部分中查找。 这样可能就会知道设置为什么会导致错误或冲突出现。

[在 Windows 10 中诊断 MDM 故障](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)详细介绍了此内置报告。

> [!TIP]
> - 一些设置还列出了 GUID。 可以在本地注册表 (regedit) 中搜索此 GUID 是否是任何设定值。
> - 事件查看器日志可能还包括有问题设置的一些错误信息（依次转到“事件查看器” > “应用和服务日志” > “Microsoft” > “Windows” > “DeviceManagement-Enterprise-Diagnostics-Provider” > “管理员”）。

## <a name="next-steps"></a>后续步骤

[监视设备配置文件](device-profile-monitor.md)和[查看一些常见问题和解决方法](device-profile-troubleshoot.md)。
