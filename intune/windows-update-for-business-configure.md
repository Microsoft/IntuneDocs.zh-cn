---
title: "在 Intune 中配置 Windows Update for Business 设置"
titleSuffix: Azure portal
description: "了解如何在 Intune 中配置 Windows Update for Business 设置，以控制 Windows 10 设备的更新。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: 1a7d047de1faa019eb137516ef75d64657e22e5a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2018
---
# <a name="manage-software-updates"></a>管理软件更新

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows 即服务是更新 Windows 10 设备的方法。 在 Windows 10 中，新的功能更新和质量更新包含了所有此前更新的内容。 这意味着，只要安装了最新更新，你的 Windows 10 设备就会保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

借助 Windows Update for Business 可以简化更新管理体验，不需要批准设备组的单个更新。 通过配置更新推出策略仍可以管理环境中的风险，并且 Windows 更新可确保在适当的时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。 使用 Intune 配置和管理 Windows 10 更新通道。 更新通道包含一组设置，可配置何时以及如何安装 Windows 10 更新。 例如，可以配置以下内容：

- **Windows 10 维护服务频道**：选择是希望设备组从半年频道（定向）还是从半年频道接收更新。  
- **延期设置**：配置更新延期设置，以延迟设备组的更新安装。 通过此设置可获得一个阶段性的更新部署，以便随时查看进度。
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
    - [Windows Holographic for Business](#windows-holographic-for-business-support)

 不支持运行 Windows 10 移动版的设备。

- 在 Windows 设备上，“**反馈和诊断**” > “**诊断和使用情况数据**”必须至少设置为“**基本**”。

    ![诊断和使用情况数据的 Windows 设置](./media/telemetry-basic.png)

    你可以手动配置此设置，也可以使用适用于 Windows 10 及更高版本的 Intune 设备限制配置文件。 为此，请将“**常规**” > “**诊断数据提交**”设置至少配置为“**基本**”。 有关设备配置文件的详细信息，请参阅[如何配置设备限制设置](device-restrictions-configure.md)。

- 在 Intune 管理控制台中，有四个设置可控制软件更新行为。 这些设置是 Windows 10 桌面设备和移动设备的常规配置策略的一部分：
    - **允许自动更新**
    - **允许预发布功能**
    - **计划安装日期**
    - **计划安装时间**

  经典门户在设备配置文件中也有数量有限的其他 Windows 10 更新设置。 在迁移到 Azure 门户时，如果在 Intune 管理控制台中配置了其中任何设置，强烈建议执行以下操作：

1. 使用所需的设置在 Azure 门户中创建 Windows 10 更新通道。 Azure 门户不支持“**允许预发布的功能**”设置，因为它不再适用于最新的 Windows 10 版本。 创建更新通道时，可以配置其他三项设置，以及其他 Windows 10 更新设置。

  > [!NOTE]
  > 迁移后，在经典门户中创建的 Windows 10 更新设置不会显示在 Azure 门户中。 但是，可继续应用这些设置。 如果已迁移上述任意设置，并在 Azure 门户中编辑已迁移的策略，则这些设置将从策略中删除。

2. 删除经典门户中的更新设置。 迁移到 Azure 门户并将相同设置添加到更新通道后，必须删除经典门户中的设置，以避免任何潜在的策略冲突。 例如，使用不同的值配置相同的设置时，会发生难以察觉的冲突，因为经典门户中配置的设置不会显示在 Azure 门户中。

## <a name="how-to-create-and-assign-update-rings"></a>如何创建并分配更新通道

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**软件更新**”。
4. 在“**软件更新**”边栏选项卡上，选择“**管理**” > “**Windows 10 更新通道**”。
5. 在显示更新通道列表的边栏选项卡上，选择“**创建**”。
6. 在“**创建更新通道**边栏选项卡上，提供更新通道的名称和可选描述，然后选择“**设置**”。
7. 在“**设置**”边栏选项卡上，配置以下信息：
    - **维护服务频道**：设置供设备接收 Windows 更新的频道（半年频道（定向）或半年频道）。
    - **Microsoft 更新**：选择是否从 Microsoft更新扫描应用更新。
    - **Windows 驱动程序**：选择是否在更新期间排除 Windows 更新驱动程序。
    - **自动更新行为**：选择如何管理自动更新行为以扫描、下载和安装更新。 有关详细信息，请参阅[更新/允许自动更新](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate)。
    - **质量更新延迟期(天)** - 指定质量更新延迟的天数。 自质量更新发布起，你最晚应在 30 天内接收这些质量更新。  

    质量更新通常是对现有 Windows 功能的修复和改进，且通常在每月的第一个星期二发布，但也可由 Microsoft 随时发布。 你可以定义在质量更新发布后，是否延迟接收质量更新（以及延迟多长时间）。
    - **功能更新延迟期(天)** - 指定功能更新延迟的天数。 自功能更新发布起，你最晚应在 180 天内接收这些功能更新。

    功能更新通常是 Windows 的新功能。 将维护服务频道设置为半年频道（定向）或半年频道后，可以在 Windows 更新上定义在 Microsoft 发布功能更新后，是否延迟接收功能更新（以及延迟多长时间）。

    例如，如果将维护服务频道设置为半年频道（定向），将延迟期设置为 30 天：假设功能更新 X 将于一月以半年频道（定向）形式在 Windows 更新上公开发布。 设备将在 2 月（即 30 天后）才收到更新。

    **如果将维护服务频道设置为半年频道，将延迟期设置为 30 天**：假设功能更新 X 将于一月以半年频道形式在 Windows 更新上公开发布。 功能更新 X 将在四个月后（即 4 月份）发布到半年频道。 设备将在此半年频道发布后的 30 天后接收此功能更新，并将在 5 月进行更新。

    - **传递优化** - 选择设备下载 Windows 更新的方式。 有关详细信息，请参阅 [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)。
1. 完成后，单击“**确定**”，然后在“**创建更新通道**”边栏选项卡上单击“**创建**”。

新的更新通道显示在更新通道列表中。

1. 要分配通道，请在更新通道列表中选择一个通道，然后在“<*通道名称*>”选项卡上选择“**分配**”。
2. 在下一个选项卡上，选取“**选择组**”，然后选择要向其分配此通道的组。
3. 完成后，选取“**选择**”以完成分配。

## <a name="update-compliance-reporting"></a>更新一致性报告
可以在 Intune 中查看更新符合性，或在 Operations Management Suite (OMS) 中使用名为“更新符合性”的免费解决方案。

### <a name="review-update-compliance-in-intune"></a>在 Intune 中查看更新符合性 
<!-- 1352223 -->
通过策略报告，查看已配置的 Windows 10 更新通道的部署状态。 
1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**软件更新**”。
4. 在“软件更新”边栏选项卡上，选择“概述”。 可在此处查看有关已分配的任意更新通道状态的一般信息。
5. 打开以下报告之一： 
     
   **对于所有部署通道：**
   1. 在“软件更新” > “Windows 10 更新通道”边栏选项卡上。 
   2. 在“监视”部分，选择“每个更新通道的部署状态”。
                   
   **对于特定部署通道：** 
   1. 在“软件更新” > “Windows 10 更新通道”边栏选项卡中，选择要查看的部署通道。
   2. 在“监视”部分，从下列报表中进行选择以查看有关更新通道的更详细信息：
      - 针对设备的更新通道部署
      - 针对用户的更新通道部署
      - 每设置部署状态

### <a name="review-update-compliance-using-oms"></a>使用 OMS 查看更新符合性
你可以通过在 Operations Management Suite (OMS) 中使用名为“更新一致性”的免费解决方案来监视 Windows 10 更新推出。 有关详细信息，请参阅[使用更新一致性监视 Windows 更新](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 使用此解决方案时，可以将商业 ID 部署到要报告更新一致性的任何 Intune 托管的 Windows 10 设备上。

在 Intune 控制台中，可以使用自定义策略的 OMA-URI 设置来配置商业 ID。 有关详细信息，请参阅 [Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。   

用于配置商业 ID 的 OMA-URI（区分大小写）路径为：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

例如，你可以在“**添加或编辑 OMA-URI 设置**”中使用以下值：

- **设置名称**：Windows Analytics 商业ID
- **设置说明**：为 Windows Analytics 解决方案配置商业 ID
- **数据类型**：字符串
- **OMA-URI**（区分大小写）：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **值**：<*使用 OMS 工作空间中的 Windows 遥测选项卡上显示的 GUID* >

![诊断和使用情况数据的 Windows 设置](./media/commID.png)

## <a name="how-to-pause-updates"></a>如何暂停更新
从暂停更新的时间算起，设备暂停接收功能更新或质量更新的期限最长为 35 天。 超过最长期限后，暂停功能将自动过期，设备将扫描 Windows 更新以获取适用的更新。 执行此扫描后，你可以再次暂停更新。
1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**软件更新**”。
4. 在“**软件更新**”边栏选项卡上，选择“**管理**” > “**Windows 10 更新通道**”。
5. 在显示更新通道列表的边栏选项卡上，选择要暂停的通道，然后选择“**...**” > “**暂停质量**”> 或“**暂停功能**”，具体取决于要暂停的更新类型。

> [!IMPORTANT]
> 发出暂停命令时，设备在下次检查服务时会收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。
> 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支持

Windows Holographic for Business 支持以下设置：

- 自动更新行为
- Microsoft 产品更新
- 服务频道