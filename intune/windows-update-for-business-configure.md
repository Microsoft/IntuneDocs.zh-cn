---
title: 在 Microsoft Intune 中配置适用于企业的 Windows 更新 - Azure | Microsoft Docs
description: 在 Windows 10 设备上，使用 Microsoft Intune 更新配置文件中的软件更新设置，以在适用于企业的 Windows 更新中创建更新通道、查看符合性和暂停更新。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 5/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: fd63fb2023b4712a3ad49838f87f5b7cc8320954
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744884"
---
# <a name="manage-software-updates-in-intune"></a>在 Intune 中管理软件更新

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 即服务是更新 Windows 10 设备的方法。 在 Windows 10 中，新的功能更新和质量更新包含了所有此前更新的内容。 只要安装了最新更新，你的 Windows 10 设备就会保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

使用适用于企业的 Windows 更新可以简化更新管理体验。 你不必批准面向设备组的各个更新。 可通过配置更新推出策略来管理环境中的风险。 Windows 更新可确保在适当时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。 使用 Intune 配置和管理 Windows 10 更新通道。 更新通道包含一组设置，用于配置 Windows 10 更新的安装时间和安装方法。 例如，可以配置以下设置：

- **Windows 10 服务频道**：选择希望设备组从其接收更新的服务通道。 可用通道如下： 
  - 半年频道
  - 半年频道（定向）
  - Windows 预览体验计划 - 快
  - Windows 预览体验计划 - 慢
  - 发布 Windows 预览体验计划 
      
  有关可用服务频道的详细信息，请参阅 [Windows 即服务概述](https://docs.microsoft.com/en-us/windows/deployment/update/waas-overview#servicing-channels)。
- **延期设置**：配置更新延期设置，以延迟设备组的更新安装。 使用这些设置可分阶段推出更新，以便随时查看进度。
- **暂停**：如果在更新部署期间的任何时间点发现问题，则推迟安装更新。
- **维护窗口**：配置可以安装更新的时间。
- **更新类型**：选择要安装的更新类型。 例如，质量更新、功能更新或驱动程序。
- **安装行为**：配置更新的安装方式。 例如，设备是否在安装后自动重新启动？
- **对等下载**：选择此项可配置对等下载。 如果已配置，当设备完成下载更新时，其他设备可以从该设备下载更新。 此设置可加快下载过程。

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

    你可以手动配置此设置，也可以使用适用于 Windows 10 及更高版本的 Intune 设备限制配置文件。 为此，请将“**常规**” > “**诊断数据提交**”设置至少配置为“**基本**”。 有关设备配置文件的详细信息，请参阅[配置设备限制设置](device-restrictions-configure.md)。

- 在 Intune 管理控制台中，有四个设置可控制软件更新行为。 这些设置是 Windows 10 桌面设备和移动设备的常规配置策略的一部分：
  - **允许自动更新**
  - **允许预发布功能**
  - **计划安装日期**
  - **计划安装时间**

  Azure 经典门户在设备配置文件中也有一定数量的其他 Windows 10 更新设置。 如果在迁移到 Azure 门户时配置了其中的任何设置，强烈建议执行以下操作：

1. 使用所需的设置在 Azure 门户中创建 Windows 10 更新通道。 Azure 门户不支持“**允许预发布的功能**”设置，因为它不再适用于最新的 Windows 10 版本。 创建更新通道时，可以配置其他三项设置，以及其他 Windows 10 更新设置。

   > [!NOTE]
   > 迁移后，在经典门户中创建的 Windows 10 更新设置不会显示在 Azure 门户中。 但会应用这些设置。 如果迁移上述任意设置，并在 Azure 门户中编辑已迁移的策略，则这些设置将从策略中删除。

2. 删除经典门户中的更新设置。 迁移到 Azure 门户并将相同设置添加到更新通道后，必须删除经典门户中的设置，以避免任何潜在的策略冲突。 例如，为同一设置配置不同值时，将会出现冲突。 了解此情况并不容易，因为在经典门户中配置的设置不会显示在 Azure 门户中。

## <a name="create-and-assign-update-rings"></a>创建和分配更新通道

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“软件更新” > “Windows 10 更新通道” > “创建”。
4. 输入名称和说明（可选），然后选择“配置”。
5. 在“设置”中，输入以下信息：

   - **服务频道**：设置设备接收 Windows 更新的频道。
   - **Microsoft 产品更新**：选择从 Microsoft 更新扫描应用更新。
   - **Windows 驱动程序**：选择在更新期间排除 Windows 更新驱动程序。
   - **自动更新行为**：选择安装自动更新的方式和重启的时间。 有关详细信息，请参阅[更新/允许自动更新](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate)。
     - **自动更新频率**：如果对更新行为选择“在计划时间自动安装和重启”，则会显示此设置。 使用此设置计划安装更新的时间，包括星期、天和时间。

   - **重启检查**：默认启用。 重启设备时，会出现一些检查项，包括检查活跃用户、电池剩余电量和正在运行的游戏等。 要在重启设备时跳过这些检查，请选择“跳过”。

   - **质量更新延迟期(天)**：输入质量更新延迟的天数。 自质量更新发布起，最晚应在 30 天内接收这些质量更新。

     质量更新通常是对现有 Windows 功能的修复和改进，且通常在每月的第一个星期二发布。 但也可能由 Microsoft 随时发布。 你可以定义是否在 Windows 更新上提供质量更新后推迟接收更新以及推迟时长。

   - **功能更新延迟期(天)**：输入功能更新延迟的天数。 自功能更新发布起，最晚应在 180 天内接收这些功能更新。

     功能更新通常是 Windows 的新功能。 配置“服务频道”设置后，可以定义是否在 Windows 更新上提供功能更新后推迟接收更新以及推迟时长。

     例如，如果将服务频道设置为半年频道（定向），将延迟期设置为 30 天：假设功能更新 X 将于一月以半年频道（定向）形式首次在 Windows 更新上公开发布。 设备将在二月（即 30 天后）才收到更新。

     如果将服务频道设置为半年频道，将延迟期设置为 30 天：假设功能更新 X 将于一月以半年频道形式首次在 Windows 更新上公开发布。 功能更新 X 将在四个月后（即 4 月份）发布到半年频道。 设备将在此半年频道发布后的 30 天后接收此功能更新，并将在 5 月进行更新。

   - **传递优化下载模式**：选择设备下载 Windows 更新的方式。 有关详细信息，请参阅 [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode)。

6. 完成后，选择“确定”。 在“创建更新频道”中，选择“创建”。

新的更新通道显示在更新通道列表中。

1. 要分配通道，请在更新通道列表中选择一个通道，然后在“<*通道名称*>”选项卡上选择“**分配**”。
2. 在下一个选项卡上，选择“选择要包含的组”，然后选择要向其分配此通道的组。
3. 完成后，选取“**选择**”以完成分配。

## <a name="update-compliance-reporting"></a>更新一致性报告
可以在 Intune 中查看更新符合性，或在 Operations Management Suite (OMS) 中使用名为“更新符合性”的免费解决方案。

### <a name="review-update-compliance-in-intune"></a>在 Intune 中查看更新符合性 
<!-- 1352223 -->
通过策略报告，查看已配置的 Windows 10 更新通道的部署状态。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“软件更新” > “概述”。 可查看有关已分配的任意更新通道状态的一般信息。
4. 打开以下报告之一：

   **对于所有部署通道**：  
   1. 在“软件更新” > “Windows 10 更新通道”上
   2. 在“监视”部分，选择“每个更新通道的部署状态”。

   **对于特定部署通道**：  
   1. 在“软件更新” > “Windows 10 更新通道”中，选择要查看的部署通道。
   2. 在“监视”部分，从下列报表中进行选择以查看有关更新通道的更详细信息：
      - **设备状态**
      - **用户状态**

### <a name="review-update-compliance-using-oms"></a>使用 OMS 查看更新符合性
你可以通过在 Operations Management Suite (OMS) 中使用名为“更新一致性”的免费解决方案来监视 Windows 10 更新推出。 有关详细信息，请参阅[使用更新一致性监视 Windows 更新](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 使用此解决方案时，可以将商业 ID 部署到要报告更新一致性的任何 Intune 托管的 Windows 10 设备上。

在 Intune 控制台中，可以使用自定义策略的 OMA-URI 设置来配置商业 ID。 有关详细信息，请参阅 [Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。   

用于配置商业 ID 的 OMA-URI（区分大小写）路径为：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

例如，你可以在“**添加或编辑 OMA-URI 设置**”中使用以下值：

- **设置名称**：Windows Analytics 商业ID
- **设置说明**：为 Windows Analytics 解决方案配置商业 ID
- **OMA-URI**（区分大小写）：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **数据类型**：字符串
- **值**：<*使用 OMS 工作空间中的 Windows 遥测选项卡上显示的 GUID* >

![OMA-URI 设置 - 编辑行](./media/commID-edit.png)

> [!NOTE]
> 有关 MS DM 服务器的详细信息，请参阅 [DMClient 配置服务提供程序 (CSP)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)。

## <a name="pause-updates"></a>暂停更新
从暂停更新的时间算起，设备暂停接收功能更新或质量更新的期限最长为 35 天。 超过最长期限后，暂停功能将自动过期，设备将扫描 Windows 更新以获取适用的更新。 执行此扫描后，你可以再次暂停更新。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“软件更新” > “Windows 10 更新通道”。
4. 在更新通道列表中，选择要暂停的通道，然后选择“...” > “暂停质量”> 或“暂停功能”，具体取决于要暂停的更新类型。

> [!IMPORTANT]
> 发出暂停命令后，设备会在下次签入服务时收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。
> 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>从 Windows 10 软件更新中卸载最新版本 
如果发现 Windows 10 计算机上存在重大问题，则可以选择卸载（回滚）最新的功能更新或最新的质量更新。 卸载某功能或质量更新仅适用于设备所在的服务通道。 卸载将触发恢复 Windows 10 计算机上的先前更新的策略。 特别是对于功能更新，可以限制卸载最新版本的时间（2-60 天）。 要设置软件更新卸载选项，请从 Azure 门户中的“Microsoft Intune ”边栏选项卡中选择“软件更新”。 然后，从“软件更新”边栏选项卡中选择“Windows 10 更新通道”。 然后，可以从“概述”部分选择“卸载”选项。

> [!NOTE]
> 在 Windows 10 计算机上，成功回滚质量更新后，终端用户仍可以通过选择“Windows 设置” > 更新” > “更新历史记录”来查看成功回滚的更新。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支持

Windows Holographic for Business 支持以下设置：

- 自动更新行为
- Microsoft 产品更新
- **服务频道**：支持“半年频道”和“半年频道(定向)”选项
