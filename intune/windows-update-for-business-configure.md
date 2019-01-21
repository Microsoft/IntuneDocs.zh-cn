---
title: 在 Microsoft Intune 中配置适用于企业的 Windows 更新 - Azure | Microsoft Docs
description: 在 Windows 10 设备上，使用 Microsoft Intune 更新配置文件中的软件更新设置，以在适用于企业的 Windows 更新中创建更新通道、查看符合性和暂停更新。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: ccb91082a3226ec4091a139d31796fd77bdf0616
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297377"
---
# <a name="manage-software-updates-in-intune"></a>在 Intune 中管理软件更新

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 即服务是更新 Windows 10 设备的方法。 在 Windows 10 中，新的功能更新和质量更新包含了所有此前更新的内容。 只要安装了最新更新，你的 Windows 10 设备就会保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

使用适用于企业的 Windows 更新可以简化更新管理体验。 你不必批准面向设备组的各个更新。 可通过配置更新推出策略来管理环境中的风险。 Windows 更新可确保在适当时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。 使用 Intune 配置和管理 Windows 10 更新通道。 更新通道包含一组设置，用于配置 Windows 10 更新的安装时间和安装方法。 例如，可以配置以下设置：

- **Windows 10 服务频道**：选择希望设备组从中接收更新的服务频道。 可用通道如下： 
  - 半年频道
  - 半年频道（定向）
  - Windows 预览体验计划 - 快
  - Windows 预览体验计划 - 慢
  - 发布 Windows 预览体验计划 
      
  有关可用服务频道的详细信息，请参阅 [Windows 即服务概述](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels)。
- **延期设置**：配置更新延期设置，以延迟设备组的更新安装。 使用这些设置可分阶段推出更新，以便随时查看进度。
- **暂停**：如果在更新推出期间出现问题，可以推迟更新安装。 
- **维护时段**：配置可以安装更新的时段。
- **更新类型**：选择要安装的更新类型。 例如，质量更新、功能更新或驱动程序。
- **安装行为**：配置更新安装方式。 例如，设备是否在安装后自动重新启动？
- **对等下载**：选择配置对等下载。 如果已配置，当设备完成下载更新时，其他设备可以从该设备下载更新。 此设置可加快下载过程。

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

    可以手动配置此设置，也可以使用适用于 Windows 10 及更高版本的 Intune 配置文件（“设备限制” > “报告和遥测”> 将“共享使用数据”至少设置为“基本”）。 有关设备配置文件的详细信息，请参阅[配置设备限制设置](device-restrictions-configure.md)。

- Azure 经典门户在设备配置文件中也有一定数量的其他 Windows 10 更新设置。 如果在迁移到 Azure 门户时配置了其中的任何设置，强烈建议执行以下操作：

  1. 使用所需的设置在 Azure 门户中创建 Windows 10 更新通道。 Azure 门户不支持“允许预发布的功能”设置，因为它不再适用于最新的 Windows 10 版本。 可以在创建更新通道时配置其他设置和其他 Windows 10 更新设置。

   > [!NOTE]
   > 迁移后，在经典门户中创建的 Windows 10 更新设置不会显示在 Azure 门户中。 但会应用这些设置。 如果迁移上述任意设置，并在 Azure 门户中编辑已迁移的策略，则这些设置将从策略中删除。

  2. 删除经典门户中的更新设置。 迁移到 Azure 门户并将相同设置添加到更新通道后，请删除经典门户中的设置，以避免任何潜在的策略冲突。 例如，为同一设置配置不同值时，将会出现冲突。 了解此情况并不容易，因为在经典门户中配置的设置并未显示在 Azure 门户中。

## <a name="create-and-assign-update-rings"></a>创建和分配更新通道

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“软件更新” > “Windows 10 更新通道” > “创建”。
3. 输入名称和说明（可选），然后选择“配置”。
4. 在“设置”中，输入以下信息：  

   更新设置  
   - **服务频道**：设置设备从中接收 Windows 更新的频道。
   - **Microsoft 产品更新**：选择扫描 Microsoft 更新中是否有应用更新。
   - **Windows 驱动程序**：选择在更新期间排除 Windows 更新驱动程序。
   - **质量更新延迟期(天)**：输入质量更新延迟天数。 自质量更新发布起，最晚应在 30 天内接收这些质量更新。

     质量更新通常是对现有 Windows 功能的修复和改进，且通常在每月的第二个星期二发布。 通过适用于企业的 Windows 更新进行的质量更新仅接收这些更新（“企业版”发布），但 Microsoft 可能随时发布其他更新。 可以定义是否在 Windows 更新上提供质量更新后推迟接收更新以及推迟时长。 有关详细信息，请参阅[使用适用于企业的 Windows 更新部署更新](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb)。

   - **功能更新延迟期(天)**：输入功能更新延迟天数。 自功能更新发布起，最晚应在 180 天内接收这些功能更新。

     功能更新通常是 Windows 的新功能。 配置“服务渠道”设置后，可以定义是否在 Windows 更新上提供功能更新后推迟接收更新以及推迟时长。

     例如：**如果将服务频道设置为半年频道(定向)，且延期期限为 30 天**：假设功能更新 X 于 1 月在 Windows 更新中作为半年频道（定向）首次公开发布。 设备将在二月（即 30 天后）才收到更新。

     **如果将服务频道设置为半年频道，且延期期限为 30 天**：假设功能更新 X 于 1 月在 Windows 更新中作为半年频道（定向）首次公开发布。 功能更新 X 将在四个月后（即 4 月份）发布到半年频道。 设备将在此半年频道发布后的 30 天后接收此功能更新，并将在 5 月进行更新。  

   用户体验设置
   
   - **自动更新行为**：选择自动更新的安装方式和重启时间。 有关详细信息，请参阅[更新/允许自动更新](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate)。

     “重置为默认值”设置将在运行“2018 年 10 月更新”或以后更新的 Windows 10 计算机上还原初始的自动更新设置。  

     - **自动行为频率**：如果对更新行为选择“在计划时间自动安装和重启”，便会看到此设置。 使用此设置计划安装更新的时间，包括星期、天和时间。

   - **重启检查**：默认情况下启用。 重启设备时，会出现一些检查项，包括检查活跃用户、电池剩余电量和正在运行的游戏等。 要在重启设备时跳过这些检查，请选择“跳过”。

   - 阻止用户暂停 Windows 更新：默认情况下允许。 使用此设置阻止或允许用户通过其计算机的“设置”暂停更新安装。 
      
   - **传递优化下载模式**：传递优化不再作为“软件更新”下的“Windows 10 更新圈”的一部分进行配置。 现在，传递优化通过设备配置进行设置。 但是，以前的配置在控制台中仍然可用。 可以通过将以前的配置编辑为“未配置”来删除这些配置，否则便无法对其进行修改。 为避免新旧策略之间的冲突，请参阅[从现有更新圈移动到传递优化](delivery-optimization-windows.md#move-from-existing-update-rings-to-delivery-optimization)，然后将设置移动到传递优化配置文件。 

5. 完成后，选择“确定”。 在“创建更新频道”中，选择“创建”。

新的更新通道显示在更新通道列表中。

1. 要分配通道，请在更新通道列表中选择一个通道，然后在“<*通道名称*>”选项卡上选择“**分配**”。
2. 在下一个选项卡上，选择“选择要包含的组”，然后选择要向其分配此通道的组。
3. 完成后，选取“选择”以完成分配。

## <a name="update-compliance-reporting"></a>更新一致性报告
可以在 Intune 中查看更新符合性，或使用名为“更新符合性”的免费解决方案。

### <a name="review-update-compliance-in-intune"></a>在 Intune 中查看更新符合性 
<!-- 1352223 --> 通过策略报告，查看已配置的 Windows 10 更新通道的部署状态。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“软件更新” > “概述”。 可查看有关已分配的任意更新通道状态的一般信息。
3. 打开以下报告之一：

   **对于所有部署通道**：  
   1. 在“软件更新” > “Windows 10 更新通道”上
   2. 在“监视”部分，选择“每个更新通道的部署状态”。

   **对于特定部署通道**：  
   1. 在“软件更新” > “Windows 10 更新通道”中，选择要查看的部署通道。
   2. 在“监视”部分，从下列报表中进行选择以查看有关更新通道的更详细信息：
      - **设备状态**
      - **用户状态**

### <a name="review-update-compliance-using-oms"></a>使用 OMS 查看更新符合性
可以使用名为“更新符合性”的免费解决方案来监视 Windows 10 更新推出。 有关详细信息，请参阅[使用更新一致性监视 Windows 更新](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)。 使用此解决方案时，可以将商业 ID 部署到要报告更新一致性的任何 Intune 托管的 Windows 10 设备上。

在 Intune 中，可以使用自定义策略的 OMA-URI 设置来配置商业 ID。 有关详细信息，请参阅 [Microsoft Intune 中适用于 Windows 10 设备的 Intune 策略设置](custom-settings-windows-10.md)。   

用于配置商业 ID 的 OMA-URI（区分大小写）路径为：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

例如，你可以在“**添加或编辑 OMA-URI 设置**”中使用以下值：

- **设置名称**：Windows Analytics 商业 ID
- **设置说明**：为 Windows Analytics 解决方案配置商业 ID
- **OMA-URI**（区分大小写）：./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **数据类型**：字符串
- **值**：<*使用 OMS 工作空间中的 Windows 遥测选项卡上显示的 GUID* >

![OMA-URI 设置 - 编辑行](./media/commID-edit.png)

> [!NOTE]
> 有关 MS DM 服务器的详细信息，请参阅 [DMClient 配置服务提供程序 (CSP)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)。

## <a name="pause-updates"></a>暂停更新
从暂停更新的时间算起，设备暂停接收功能更新或质量更新的期限最长为 35 天。 超出最长天数后，暂停功能自动过期，设备将扫描 Windows 更新以检查可用更新。 执行此扫描后，你可以再次暂停更新。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“软件更新” > “Windows 10 更新通道”。
3. 在更新通道列表中，选择要暂停的通道，然后选择“...” > “暂停质量”> 或“暂停功能”，具体取决于要暂停的更新类型。

> [!IMPORTANT]
> 发出暂停命令后，设备会在下次签入服务时收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。
> 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>从 Windows 10 软件更新中卸载最新版本 
如果 Windows 10 计算机上存在重大问题，则可以选择卸载（回滚）最新的功能更新或最新的质量更新。 卸载某功能或质量更新仅适用于设备所在的服务通道。 卸载将触发还原 Windows 10 计算机上前一个更新的策略。 特别是对于功能更新，可以限制卸载最新版本的时间（2-60 天）。 设置软件更新卸载选项：

1. 在 Intune 中，选择“软件更新”。
2. 选择“Windows 10 更新通道”，选择一个现有更新通道，然后选择“卸载”。

> [!NOTE]
> 在 Windows 10 计算机上，当质量更新成功回滚后，最终用户可继续查看列出的更新：“Windows 设置” > “更新” > “更新历史记录”。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支持

Windows Holographic for Business 支持以下设置：

- 自动更新行为
- Microsoft 产品更新
- **服务频道**：支持“半年频道”和“半年频道(定向)”选项
