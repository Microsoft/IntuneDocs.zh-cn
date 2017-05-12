---
title: "配置 Windows Update for Business 设置 - Intune | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何在 Intune 中配置 Windows Update for Business 设置，以控制 Windows 10 设备的更新。"
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08f659cf-715e-4e10-9ab2-1bac3c6f2366
ms.reviewer: coryfe
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: e825d47860924de1350299c8998d958ed68c0418
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-configure-windows-update-for-business-settings-with-microsoft-intune"></a>如何使用 Microsoft Intune 配置 Windows Update for Business 设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>简介
Windows 即服务是为 Windows 10 提供更新的新方式。 从 Windows 10 开始，任何新的功能更新和质量更新都将包含所有此前更新的内容。 这意味着，只要安装了最新更新，你的 Windows 10 设备将完全保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

借助 Windows Update for Business 可以简化更新管理体验，不需要批准设备组的单个更新。 通过配置更新推出策略仍可以管理环境中的风险，并且 Windows 更新将确保在适当的时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。使用 Intune 来配置和管理 **Windows 10 更新通道**。 更新通道包含一组设置，可配置何时以及如何安装 Windows 10 更新。 例如，可以配置以下内容：

- **Windows 10 服务分支**：选择是否要让设备组接收来自 Current Branch 或 Current Branch for Business 的更新。  
- **延期设置**：配置更新延期设置，以延迟设备组的更新安装。 然后，你将有一个阶段性的更新部署，以便随时查看进度。
- **暂停**：如果在更新部署期间的任何时间点发现问题，则推迟安装更新。
- **维护窗口**：配置可以安装更新的时间。
- **更新类型**：选择要安装的更新类型。 例如，质量更新、功能更新或驱动程序。
- **安装行为**：这将配置更新的安装方式。 例如，设备是否在安装后自动重新启动？
- **对等下载**：可以指定是否配置对等下载。 如果已配置，当设备完成下载更新时，其他设备可以从该设备下载更新。 这将加快下载过程。

创建更新铃声后，将其分配到设备组。 通过使用更新通道，你可以创建反映业务需求的更新策略。 有关详细信息，请参阅[使用 Windows Update for Business 更新管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

## <a name="before-you-start"></a>开始之前

- 要更新 Windows 10 电脑，它们必须至少运行安装了 Windows 周年更新的 Windows 10 专业版。

- Windows 更新支持以下 Windows 10 版本：
    - Windows 10
    - Windows 10 协同版（适用于 Surface Hub 设备）

 不支持运行 Windows 10 移动版和 Windows 10 全息版的设备。

- 在 Windows 设备上，“**反馈和诊断**” > “**诊断和使用情况数据**”必须至少设置为“**基本**”。

    ![诊断和使用情况数据的 Windows 设置](./media/telemetry-basic.png)

    你可以手动配置此设置，也可以使用适用于 Windows 10 及更高版本的 Intune 设备限制配置文件。 为此，请将“**常规**” > “**诊断数据提交**”设置至少配置为“**基本**”。 有关设备配置文件的详细信息，请参阅[如何配置设备限制设置](how-to-configure-device-restrictions.md)。

- 在经典 Intune 管理控制台中，有四个可控制软件更新行为的设置。 这些设置是 Windows 10 桌面设备和移动设备的常规配置策略的一部分：
    - **允许自动更新**
    - **允许预发布功能**
    - **计划安装日期**
    - **计划安装时间**

  经典控制台在设备配置文件中还具有数量有限的其他 Windows 10 更新设置。 在迁移到 Azure 门户时，如果在经典 Intune 管理控制台中配置了任意这些设置，强烈建议你执行以下操作：

1. 使用所需的设置在 Azure 门户中创建 Windows 10 更新通道。 Azure 门户不支持“**允许预发布的功能**”设置，因为它不再适用于最新的 Windows 10 版本。 创建更新通道时，可以配置其他三项设置，以及其他 Windows 10 更新设置。

  > [!NOTE]
  > 迁移后，在经典控制台中创建的 Windows 10 更新设置不会显示在 Azure 门户中。 但是，可继续应用这些设置。 如果你已迁移任意这些设置并从 Azure 门户编辑迁移的策略，这些设置将从该策略中删除。

2. 删除经典控制台中的更新设置。 迁移到 Azure 门户并将相同设置添加到更新通道后，必须删除经典门户中的设置，以避免任何潜在的策略冲突。 例如，使用不同的值配置相同的设置会导致冲突，并且没有可以了解这种情况的简单方法，因为在经典控制台中配置的设置不会显示在 Azure 门户中。

## <a name="how-to-create-and-assign-update-rings"></a>如何创建并分配更新通道

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**软件更新**”。
4. 在“**软件更新**”边栏选项卡上，选择“**管理**” > “**Windows 10 更新通道**”。
5. 在显示更新通道列表的边栏选项卡上，选择“**创建**”。
6. 在“**创建更新通道**边栏选项卡上，提供更新通道的名称和可选描述，然后选择“**设置**”。
7. 在“**设置**”边栏选项卡上，配置以下信息：
    - **服务分支**：设置设备将接收 Windows 更新的分支（Current Branch 或 Current Branch for Business）。
    - **Microsoft 更新**：选择是否从 Microsoft更新扫描应用更新。
    -  **Windows 驱动程序**：选择是否在更新期间排除 Windows 更新驱动程序。
    - **自动更新行为**：选择如何管理自动更新行为以扫描、下载和安装更新。 有关详细信息，请参阅[更新/允许自动更新](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate)。
    - **质量更新延期期限（天）** - 指定质量更新延期的天数。 自质量更新发布起，你最晚应在 30 天内接收这些质量更新。  

      质量更新通常是对现有 Windows 功能的修复和改进，且通常在每月的第一个星期二发布，但也可由 Microsoft 随时发布。 你可以定义在质量更新发布后，是否延迟接收质量更新（以及延迟多长时间）。
    - **功能更新延期期限（天）** - 指定功能更新延期的天数。 自功能更新发布起，你最晚应在 180 天内接收这些功能更新。

    功能更新通常是 Windows 的新功能。 配置“**服务分支**”设置（**CB** 或 **CBB**）后，你可以在 Windows 更新上定义在 Microsoft 发布功能更新后，是否延迟接收功能更新（以及延迟多长时间）。

    例如：  
    **如果服务分支设置为 CB 并且延期期限为 30 天**：假设功能更新 X 在一月份作为 CB 在 Windows 更新上首次公开提供。 设备将在 2 月（即 30 天后）才收到更新。

    **如果服务分支设置为 CBB 并且延期期限为 30 天**：假设功能更新 X 在一月份作为 CB 在 Windows 更新上首次公开提供。 功能更新 X 将在四个月后（即 4 月份）发布到 CBB。 设备将在此 CBB 发布后的 30 天后接收此功能更新，并将在 5 月更新。

    - **传递优化** - 选择设备下载 Windows 更新的方式。 有关详细信息，请参阅 [DeliveryOptimization/DEDownloadMode](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#deliveryoptimization-dodownloadmode)。
8. 完成后，单击“**确定**”，然后在“**创建更新通道**”边栏选项卡上单击“**创建**”。

新的更新通道显示在更新通道列表中。

1. 要分配通道，请在更新通道列表中选择一个通道，然后在“<*通道名称*>”选项卡上选择“**分配**”。
2. 在下一个选项卡上，选取“**选择组**”，然后选择要向其分配此通道的组。
3. 完成后，选取“**选择**”以完成分配。



## <a name="update-compliance-reporting"></a>更新一致性报告
你可以通过在 Operations Management Suite (OMS) 中使用名为“更新一致性”的免费解决方案来监视 Windows 10 更新推出。 有关详细信息，请参阅[使用更新一致性监视 Windows 更新](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 使用此解决方案时，可以将商业 ID 部署到要报告更新一致性的任何 Intune 托管的 Windows 10 设备上。

在 Intune 控制台中，可以使用自定义策略的 OMA-URI 设置来配置商业 ID。 有关详细信息，请参阅 [Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)。   

用于配置商业 ID 的 OMA-URI（区分大小写）路径为：./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

例如，你可以在“**添加或编辑 OMA-URI 设置**”中使用以下值：

- **设置名称**：Windows Analytics 商业ID
- **设置说明**：为 Windows Analytics 解决方案配置商业 ID
- **数据类型**：字符串
- **OMA-URI**（区分大小写）：./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **值**：<*使用 OMS 工作空间中的 Windows 遥测选项卡上显示的 GUID* >

![诊断和使用情况数据的 Windows 设置](./media/commID.png)

<!--
1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Software Updates**.
4. On the **Software Updates** blade, choose **Overview**. From here you can see general information about the status of any update rings you assigned.
4. On the **Windows 10 Updates** blade, choose **Monitor** > **Update ring deployment for devices**, **Update ring deployment for users**, or **Per-setting deployment state** to view more detailed information about update ring assignments.
-->





## <a name="how-to-pause-updates"></a>如何暂停更新
从暂停更新的时间算起，设备暂停接收功能更新或质量更新的期限最长为 35 天。 超过最长期限后，暂停功能将自动过期，设备将扫描 Windows 更新以获取适用的更新。 执行此扫描后，你可以再次暂停更新。
1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**软件更新**”。
4. 在“**软件更新**”边栏选项卡上，选择“**管理**” > “**Windows 10 更新通道**”。
5. 在显示更新通道列表的边栏选项卡上，选择要暂停的通道，然后选择“**...**” > “**暂停质量**”> 或“**暂停功能**”，具体取决于要暂停的更新类型。

> [!IMPORTANT]
> 发出暂停命令时，设备在下次检查服务时会收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。
> 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

