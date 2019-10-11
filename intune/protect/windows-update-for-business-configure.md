---
title: 在 Microsoft Intune 中配置适用于企业的 Windows 更新 - Azure | Microsoft Docs
description: 在 Windows 10 设备上，使用 Microsoft Intune 更新配置文件中的软件更新设置，以在适用于企业的 Windows 更新中创建更新通道、查看符合性和暂停更新。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a9ecc1cabb00122d2812580b663fcd0c1dfabc3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728086"
---
# <a name="manage-software-updates-in-intune"></a>在 Intune 中管理软件更新

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 Intune 定义更新通道，以指定 Windows 即服务更新 Windows 10 设备的方式和时间。 更新通道是分配给设备组的策略。 通过使用更新通道，你可以创建反映业务需求的更新策略。 有关详细信息，请参阅[使用 Windows Update for Business 更新管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

在 Windows 10 中，新的功能更新和质量更新包含了所有此前更新的内容。 只要安装了最新更新，你的 Windows 10 设备就会保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。


使用适用于企业的 Windows 更新可以简化更新管理体验。 你不必批准面向设备组的各个更新。 可通过配置更新推出策略来管理环境中的风险。 Intune 提供在设备上[配置更新设置](../windows-update-settings.md)的功能，使你能够延迟安装更新。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。 安装 Windows 10 更新时配置的此设置集合称为“Windows 10 更新通道”  。

Windows 10 更新通道支持[作用域标记](../fundamentals/scope-tags.md)。 可以结合使用作用域标记和更新通道，来帮助筛选和管理你所使用的配置集合。

## <a name="prerequisites"></a>必备条件  

要在 Intune 中对 Windows 10 设备使用 Windows 更新，必须满足以下先决条件。  

- Windows 10 电脑必须至少运行安装了 Windows 周年更新或更高版本（版本 1607 或更高版本）的 Windows 10 专业版
- Windows 更新支持以下 Windows 10 版本：
  - Windows 10
  - Windows 10 协同版（适用于 Surface Hub 设备）
  - Windows Holographic for Business  

    Windows Holographic for Business 支持 Windows 更新的一部分设置，包括：
    - 自动更新行为 
    - Microsoft 产品更新 
    - **服务频道**：支持“半年频道”  和“半年频道(定向)”  选项。 有关详细信息，请参阅[管理 Windows Holographic](../fundamentals/windows-holographic-for-business.md)。  

    > [!NOTE]  
    > **不支持的版本**：
    > - Windows 10 移动版  
    > - Windows 10 企业版 LTSC。 适用于企业的 Windows 更新 (WUfB) 当前不支持“长期服务频道”版本。  计划使用备用修补方法，如 WSUS 或 Configuration Manager。  

- 在 Windows 设备上，“反馈和诊断”   > “诊断和使用情况数据”  必须设置为“基本”  、“增强”  或“完整”  。  

  可以为 Windows 10 设备手动配置“诊断和使用情况数据”，也可以使用适用于 Windows 10 及更高版本的 Intune 设备限制配置文件。  若使用设备限制配置文件，请至少将“共享使用情况数据”的[设备限制设置](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry)设置为“基本”。   为 Windows 10 或更高版本配置设备限制策略时，可在“报告和遥测”类别中找到此设置。 

  有关设备配置文件的详细信息，请参阅[配置设备限制设置](../configuration/device-restrictions-configure.md)。  

- 如果使用 Azure 经典门户，则[将设置迁移到 Azure 门户](#migrate-update-settings-to-the-azure-portal)。  


## <a name="create-and-assign-update-rings"></a>创建和分配更新通道

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择“软件更新” > “Windows 10 更新通道” > “创建”    。
4. 输入名称和说明（可选），然后选择“配置”  。
5. 在“设置”  中，配置可满足业务需求的设置。 若要了解可用的设置，请参阅 [Windows 更新设置](../windows-update-settings.md)。  
6. 完成后，选择“确定”  。 在“创建更新频道”中，选择“创建”   。 新的更新通道显示在更新通道列表中。
7. 要分配通道，请在更新通道列表中选择一个通道，然后在“\<通道名称>”选项卡上选择“分配”  。
8. 使用“包含”  和“排除”  选项卡来定义将此通道分配到哪些组，然后选择“保存”  以完成分配。

## <a name="manage-your-windows-10-update-rings"></a>管理 Windows 10 更新通道
在门户中，可以选择一个 Windows 10 更新通道以打开其“概述”  窗格。 通过此窗格可以查看通道分配状态并执行其他操作来管理通道。 
### <a name="to-view-an-updates-rings-overview-pane"></a>若要查看更新通道“概述”窗格，请执行以下操作： 
1. 登录到 Azure 门户。
2. 导航到“Intune”   > “软件更新”   > “Windows 10 更新通道”  。
3. 选择要查看或管理的更新通道。  

除了查看分配状态之外，还可以从“概述”窗格顶部选择以下操作来管理更新通道：  
- [删除](#delete)  
- [暂停](#pause)  
- [恢复](#resume)  
- [延长](#extend)  
- [卸载](#uninstall)  

![可用操作](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>删除  
选择“删除”  可停止强制执行所选 Windows 10 更新通道的设置。 删除通道会从 Intune 中删除其配置，以便 Intune 不再应用并强制执行这些设置。  

从 Intune 中删除通道不会修改已分配有更新通道的设备上的设置。  相反，设备将保留其当前设置。 这是因为，设备不会保留先前设置的历史记录，并且设备可能会从保持活动状态的其他更新通道接收设置。  

#### <a name="to-delete-a-ring"></a>删除通道  
1. 在查看更新通道的概述页时，选择“删除”  。  
2. 选择“确定”  。  

### <a name="pause"></a>暂停  
选择“暂停”  可防止已分配的设备在暂停通道后长达 35 天的时间内接收功能更新或质量更新。 超出最长天数后，暂停功能自动过期，设备将扫描 Windows 更新以检查可用更新。 执行此扫描后，你可以再次暂停更新。 如果恢复已暂停的更新通道，然后再次暂停该通道，则暂停期将重置为 35 天。  

#### <a name="to-pause-a-ring"></a>暂停通道  
1. 在查看更新通道的概述页时，选择“暂停”  。  
2. 选择“功能”  或“质量”  以暂停该类型的更新，然后选择“确定”  。  
3. 在暂停一种更新类型后，可以再次选择“暂停”以暂停另一种更新类型。  

暂停更新类型后，该通道的“概述”窗格将显示该更新类型恢复之前剩余的天数。

> [!IMPORTANT]  
> 发出暂停命令后，设备会在下次签入服务时收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

### <a name="resume"></a>继续  
暂停更新通道时，可以选择“恢复”  ，将该通道的“功能”和“质量”更新还原为活动操作。 恢复更新通道后，可以再次暂停该通道。  

#### <a name="to-resume-a-ring"></a>恢复通道  
1. 在查看已暂停更新通道的概述页时，选择“恢复”  。  
2. 从可用选项中进行选择以恢复“功能”  或“质量”  更新，然后选择“确定”  。  
3. 在恢复一种更新类型后，可以再次选择“恢复”以恢复另一种更新类型。  

### <a name="extend"></a>Extend  
暂停更新通道时，可以选择“延长”  ，将该更新通道的“功能”和“质量”更新的暂停期重置为 35 天。  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>延长通道的暂停期  
1. 在查看已暂停更新通道的概述页时，选择“延长”  。 
2. 从可用选项中进行选择以恢复“功能”  或“质量”  更新，然后选择“确定”  。  
3. 延长一种更新类型的暂停期后，可以再次选择“延长”以延长其他更新类型的暂停期。  

### <a name="uninstall"></a>“卸载”  
Intune 管理员可以使用“卸载”  来卸载（回滚）活动更新通道或暂停的更新通道的最新功能  更新或最新质量  更新。 卸载一种类型后，还可以卸载其他类型。 Intune 不支持也不管理用户卸载更新的功能。  

若要成功卸载，必须符合以下先决条件：  
- 设备必须运行 Windows 10 2018 年 4 月更新（版本 1803）或更高版本。  

设备必须已安装最新更新。 由于更新可以累计，安装最新更新的设备将具有最新的功能和质量更新。 例如，如果在 Windows 10 计算机上发现中断问题，则可以使用此选项回滚上次更新。  

使用“卸载”时，请考虑以下各项：  
- 卸载某功能或质量更新仅适用于设备所在的服务通道。  

- 对“功能”或“质量”更新使用卸载将触发还原 Windows 10 计算机上前一个更新的策略。  

- 在 Windows 10 设备上，当质量更新成功回滚后，最终用户可继续查看列出的更新：“Windows 设置” > “更新” > “更新历史记录”    。  

- 具体而言，对于“功能”更新，根据更新通道更新设置“设置功能更新卸载期限(2 - 60 天)”  的配置，可以卸载功能更新的时间限制为 2-60 天。 如果安装功能更新的时间超过配置的卸载期限，则无法回滚设备上安装的功能更新。  

  例如，功能更新卸载期为 20 天的更新通道。 在 25 天后，你决定回滚到最新的功能更新并使用“卸载”选项。  在 20 天以前安装了功能更新的设备无法卸载更新，因为它们已删除了作为维护的一部分必需的位。 但是，在 19 天以前仅安装了功能更新的设备可以卸载更新（如果它们在超过 20 天的卸载期前成功签入以接收卸载命令）。  

有关 Windows 更新策略的详细信息，请参阅 Windows 客户端管理文档中的[更新 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)。  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>卸载最新的 Windows 10 更新  
1. 在查看已暂停更新通道的概述页时，选择“卸载”  。  
2. 从可用选项中进行选择以卸载“功能”  或“质量”  更新，然后选择“确定”  。  
3. 触发一种更新类型的卸载后，可以再次选择“卸载”以卸载其余的更新类型。  

## <a name="migrate-update-settings-to-the-azure-portal"></a>将更新设置迁移到 Azure 门户  
Azure 经典门户在设备配置文件中也有一定数量的其他 Windows 10 更新设置。 如果在迁移到 Azure 门户时配置了其中的任何设置，强烈建议执行以下操作：  

1. 使用所需的设置在 Azure 门户中创建 Windows 10 更新通道。 Azure 门户不支持“允许预发布的功能”设置，因为它不再适用于最新的 Windows 10 版本  。 创建更新通道时，可以配置其他三项设置，以及其他 Windows 10 更新设置。  

   > [!NOTE]  
   > 迁移后，在经典门户中创建的 Windows 10 更新设置不会显示在 Azure 门户中。 但会应用这些设置。 如果迁移上述任意设置，并在 Azure 门户中编辑已迁移的策略，则这些设置将从策略中删除。  

2. 删除经典门户中的更新设置。 迁移到 Azure 门户并将相同设置添加到更新通道后，必须删除经典门户中的设置，以避免任何潜在的策略冲突。 例如，为同一设置配置不同值时，将会出现冲突。 了解此情况并不容易，因为在经典门户中配置的设置不会显示在 Azure 门户中。  

## <a name="next-steps"></a>后续步骤
[Intune 支持的 Windows 更新设置](../windows-update-settings.md)  

[Intune 的更新符合性报告](../windows-update-compliance-reports.md)

[Windows 10 更新通道疑难解答](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

