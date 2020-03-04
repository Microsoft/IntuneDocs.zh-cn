---
title: 在 Microsoft Intune 中配置适用于企业的 Windows 更新 - Azure | Microsoft Docs
description: 使用更新通道和功能更新策略管理 Windows 10 软件更新。 你可以使用 Microsoft Intune 查看符合性和暂停使用“适用于企业的 Windows 更新”设置安装更新。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9245ca028bdb5589df8c76b10560d9130a1108c
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181715"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>在 Intune 中管理 Windows 10 软件更新

使用 Intune 管理从“适用于企业的 Windows 更新”进行的 Windows 10 软件更新安装。

使用适用于企业的 Windows 更新可以简化更新管理体验。 你不必批准面向设备组的各个更新。 可通过配置更新推出策略来管理环境中的风险。 Intune 提供在设备上[配置更新设置](windows-update-settings.md)的功能，使你能够延迟安装更新。 你还可以阻止设备从新的 Windows 版本安装功能以帮助其保持稳定，同时允许这些设备继续安装质量和安全性更新。

Intune 只存储更新策略分配，而不存储更新本身。 设备直接访问 Windows 更新以进行更新。

Intune 提供以下策略类型来管理更新：

- **Windows 10 更新通道**：此策略是安装 Windows 10 更新时配置的设置集合。

- **Windows 10 功能更新（公开预览版）** :此策略会将设备带到你指定的 Windows 版本，并在这些设备上冻结功能集，直到你选择将其更新到更高的 Windows 版本。  尽管该功能版本保持不变，但设备仍可继续安装适用于其功能版本的质量和安全更新。

将 Windows 10 更新通道和 Windows 10 功能更新的策略分配给设备组。 可以在同一 Intune 环境中同时使用这两种策略类型来管理 Windows 10 设备的软件更新，并创建反映业务需求的更新策略。

有关详细信息，请参阅[使用 Windows Update for Business 更新管理更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)。

## <a name="prerequisites"></a>必备条件

要在 Intune 中对 Windows 10 设备使用 Windows 更新，必须满足以下先决条件。

- Windows 10 PC 必须运行以下 Windows 10 版本：
  - **Windows 10 更新通道**：版本 1607 或更高版本
  - **Windows 10 功能更新**：版本 1703 或更高版本

- Windows 更新支持以下 Windows 10 版本：
  - Windows 10
  - Windows 10 协同版 - 适用于 Surface Hub 设备（不支持 Windows 10 功能更新  ）
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

## <a name="windows-10-update-rings"></a>Windows 10 更新通道

创建更新通道，以指定 Windows 即服务使用“功能和质量更新”更新你的 Windows 10 设备的方式和时间。 在 Windows 10 中，新的功能更新和质量更新包含了所有此前更新的内容。 只要安装了最新更新，你的 Windows 10 设备就会保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

Windows 10 更新通道支持[作用域标记](../fundamentals/scope-tags.md)。 可以结合使用作用域标记和更新通道，来帮助筛选和管理你所使用的配置集合。

### <a name="create-and-assign-update-rings"></a>创建和分配更新通道

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “Windows” > “Windows 10 更新通道” > “创建”     。

3. 在“基本信息”下，指定名称和描述（可选），然后选择“下一步”   。
  ![创建更新通道](./media/windows-update-for-business-configure/basics-tab.png)

4. 在“更新通道设置”下，配置可满足业务需求的设置  。 若要了解可用的设置，请参阅 [Windows 更新设置](../protect/windows-update-settings.md)。 配置“更新”和“用户体验”设置之后，选择“下一步”   。

5. 若要在更新通道中应用作用域标记，则在“作用域标记”下，选择“+ 选择作用域标记”以打开“选择标记”窗格    。 选择一个或多个标记，然后单击“选择”以将其添加到更新通道，然后返回“作用域标记”页   。

   准备就绪后，选择“下一步”，转到“分配”   。

6. 在“分配”下，选择“+ 选择要包括的组”，然后将更新通道分配到一个或多个组   。 使用“+ 选择要排除的组”对分配进行相应调整  。 选择“下一步”继续操作  。

7. 在“查看 + 创建”  下，查看设置，然后在准备好保存 Windows 10 更新通道时选择“创建”  。 新的更新通道显会示在更新通道列表中。

### <a name="manage-your-windows-10-update-rings"></a>管理 Windows 10 更新通道

在门户中，导航到“设备” > “Windows” > “Windows 10 更新通道”，并选择要管理的策略    。  策略将打开到“概述”页  。

在此页上，可以查看通道分配状态，从“概述”窗格顶部选择以下操作来管理更新通道：

- [删除](#delete)
- [暂停](#pause)
- [恢复](#resume)
- [延长](#extend)
- [卸载](#uninstall)

![可用操作](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>删除

选择“删除”  可停止强制执行所选 Windows 10 更新通道的设置。 删除通道会从 Intune 中删除其配置，以便 Intune 不再应用并强制执行这些设置。

从 Intune 中删除通道不会修改已分配有更新通道的设备上的设置。  相反，设备将保留其当前设置。 设备不会保留它们之前保存的设置的历史记录。 设备还可以从保持活动状态的其他更新通道接收设置。

##### <a name="to-delete-a-ring"></a>删除通道

1. 在查看更新通道的概述页时，选择“删除”  。
2. 选择“确定”  。

#### <a name="pause"></a>暂停

选择“暂停”  可防止已分配的设备在暂停通道后长达 35 天的时间内接收功能更新或质量更新。 超出最长天数后，暂停功能自动过期，设备将扫描 Windows 更新以检查可用更新。 在此扫描之后，你可以再次暂停更新。
如果恢复已暂停的更新通道，然后再次暂停该通道，则暂停期将重置为 35 天。

##### <a name="to-pause-a-ring"></a>暂停通道

1. 在查看更新通道的概述页时，选择“暂停”  。
2. 选择“功能”  或“质量”  以暂停该类型的更新，然后选择“确定”  。
3. 在暂停一种更新类型后，可以再次选择“暂停”以暂停另一种更新类型。

暂停更新类型后，该通道的“概述”窗格将显示该更新类型恢复之前剩余的天数。

> [!IMPORTANT]
> 发出暂停命令后，设备会在下次签入服务时收到此命令。 可能的情况是，在设备签入前，它们可能安装了计划更新。 此外，如果在发出暂停命令时关闭目标设备，则当打开它时，可能会在它使用 Intune 签入前下载并安装计划的更新。

#### <a name="resume"></a>恢复

暂停更新通道时，可以选择“恢复”  ，将该通道的“功能”和“质量”更新还原为活动操作。 恢复更新通道后，可以再次暂停该通道。

##### <a name="to-resume-a-ring"></a>恢复通道

1. 在查看已暂停更新通道的概述页时，选择“恢复”  。
2. 从可用选项中进行选择以恢复“功能”  或“质量”  更新，然后选择“确定”  。
3. 在恢复一种更新类型后，可以再次选择“恢复”以恢复另一种更新类型。

#### <a name="extend"></a>Extend  

暂停更新通道时，可以选择“延长”  ，将该更新通道的“功能”和“质量”更新的暂停期重置为 35 天。

##### <a name="to-extend-the-pause-period-for-a-ring"></a>延长通道的暂停期

1. 在查看已暂停更新通道的概述页时，选择“延长”  。
2. 从可用选项中进行选择以恢复“功能”  或“质量”  更新，然后选择“确定”  。
3. 延长一种更新类型的暂停期后，可以再次选择“延长”以延长其他更新类型的暂停期。

#### <a name="uninstall"></a>“卸载”  

Intune 管理员可以使用“卸载”  来卸载（回滚）活动更新通道或暂停的更新通道的最新功能  更新或最新质量  更新。 卸载一种类型后，还可以卸载其他类型。 Intune 不支持也不管理用户卸载更新的功能。  

> [!IMPORTANT]
> 使用“卸载”选项时，Intune 会立即将卸载请求传递到设备  。
>
> - Windows 设备在收到 Intune 策略更改后立即开始删除更新。 更新删除并不限于维护计划，即使它们作为更新通道的一部分进行配置时也是如此。
> - 如果更新删除需要重新启动设备，则设备将重新启动，而不会向设备用户提供延迟选项。

若要成功卸载，必须符合以下先决条件：

- 设备必须运行 Windows 10 2018 年 4 月更新（版本 1803）或更高版本。

设备必须已安装最新更新。 由于更新可以累计，安装最新更新的设备将具有最新的功能和质量更新。 例如，如果在 Windows 10 计算机上发现中断问题，则可以使用此选项回滚上次更新。

使用“卸载”时，请考虑以下各项：

- 卸载某功能或质量更新仅适用于设备所在的服务通道。

- 对“功能”或“质量”更新使用卸载将触发还原 Windows 10 计算机上前一个更新的策略。

- 在 Windows 10 设备上，当质量更新成功回滚后，设备用户可继续查看列出的更新：“Windows 设置” > “更新” > “更新历史记录”    。

- 针对功能更新，可以卸载更新的时间限制为 2-60 天。 此期限由更新通道的更新设置——“设置功能更新卸载期限(2 - 60 天)”进行配置  。 如果安装功能更新的时间超过配置的卸载期限，则无法回滚设备上已安装的更新。

  例如，功能更新卸载期为 20 天的更新通道。 在 25 天后，你决定回滚到最新的功能更新并使用“卸载”选项。  在 20 天以前安装了功能更新的设备无法卸载更新，因为它们已删除了作为维护一部分的必需的位。 但是，在 19 天以前仅安装了功能更新的设备可以卸载更新（如果它们在超过 20 天的卸载期前成功签入以接收卸载命令）。

有关 Windows 更新策略的详细信息，请参阅 Windows 客户端管理文档中的[更新 CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp)。

##### <a name="to-uninstall-the-latest-windows-10-update"></a>卸载最新的 Windows 10 更新

1. 在查看已暂停更新通道的概述页时，选择“卸载”  。
2. 从可用选项中进行选择以卸载“功能”  或“质量”  更新，然后选择“确定”  。
3. 触发一种更新类型的卸载后，可以再次选择“卸载”以卸载其余的更新类型。

## <a name="windows-10-feature-updates"></a>Windows 10 功能更新

*此功能目前提供公共预览版。*

使用 Windows 10 功能更新时，可以选择想要设备保留的 Windows 功能版本，如 Windows 10 版本 1803 或 1809  。 可以设置 1803 或更高版本的功能级别。

当设备收到 Windows 10 功能更新策略时：

- 设备将更新到策略中指定的 Windows 版本。 已运行更高版本 Windows 的设备将保持其当前版本。 通过冻结版本，设备功能集在策略持续时间内保持稳定。

- 虽然安装的 Windows 版本仍然不变，但在对该版本的支持持续时间内，设备仍可以接收并安装 Windows 版本的质量和安全更新，这有助于使设备保持最新和安全状态。

- 与对更新通道使用“暂停”  （在 35 天后过期）不同，Windows 10 功能更新策略一直有效。 在修改或删除 Windows 10 功能更新策略之前，设备不会安装新的 Windows 版本。 如果你编辑该策略以指定较新的版本，则设备可以从该 Windows 版本安装相应功能。

### <a name="prerequisites-for-windows-10-feature-updates"></a>Windows 10 功能更新先决条件

要在 Intune 中使用 Windows 10 功能更新，必须满足以下先决条件。

- 设备必须在 Intune MDM 中注册，并加入 Azure AD 或注册 Azure AD。
- 若要将功能更新策略与 Intune 配合使用，设备必须打开遥测，同时最小设置为[基本  ](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry)。 作为[设备限制策略](../configuration/device-restrictions-configure.md)的一部分，在“报告遥测”  下配置遥测。
  
  如果设备接收功能更新策略，并将遥测设置为“未配置”  （这意味着它处于关闭状态），则可能会安装比功能更新策略中定义的版本更新的 Windows。 需要遥测的先决条件正在审查中，因为此功能将正式发布。

### <a name="limitations-for-windows-10-feature-updates"></a>Windows 10 功能更新限制

- 当将“Windows 10 功能更新”  策略部署到同样接收“Windows 10 更新通道”  策略的设备时，请查看更新通道中的以下配置：
  - “功能更新延迟期(天)”  必须设置为“0”  。
  - 更新通道的功能更新必须为运行状态  。 这些更新不能暂停。

- 在 Autopilot 开箱即用体验 (OOBE) 期间，不能应用 Windows 10 功能更新策略，这些策略仅在设备完成预配（通常为一天）后第一次进行 Windows 更新扫描时应用。

### <a name="create-and-assign-windows-10-feature-updates"></a>创建和分配 Windows 10 功能更新

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “Windows” > “Windows 10 功能更新” > “创建”     。

3. 在“基本信息”下，指定名称、说明（可选），对于“要部署的功能更新”，选择具有所需功能集的 Windows 版本，然后选择“下一步”    。

4. 在“分配”  下，选择“+ 选择要包括的组”  ，然后将功能更新部署分配到一个或多个组。 选择“下一步”继续操作  。

5. 在“查看 + 创建”下，查看设置，然后在准备好保存 Windows 10 功能更新处理时选择“创建”   。  

### <a name="manage-windows-10-feature-updates"></a>管理 Windows 10 功能更新

在管理中心中，转到“设备” > “Windows” > “Windows 10 功能更新”，并选择要管理的策略    。 策略将打开到“概述”窗格  。

从该窗格中，你可以：

- 选择“删除”从 Intune 中删除策略，并将其从设备中删除  。
- 选择“属性”  以修改部署。  在“属性”  窗格中，选择“编辑”  以打开“部署设置或分配”  ，然后你可以在其中修改部署。
- 选择“最终用户更新状态”  以查看有关策略的信息。

## <a name="validation-and-reporting-for-windows-10-updates"></a>Windows 10 更新的验证和报告

对于 Windows 10 更新环和 Windows 10 功能更新，请使用 [Intune 符合性报告更新](../windows-update-compliance-reports.md)以监视设备的更新状态。 此解决方案在 Azure 订阅中使用[更新符合性](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor)。

## <a name="next-steps"></a>后续步骤

[Intune 支持的 Windows 更新设置](../windows-update-settings.md)

[Windows 10 更新通道疑难解答](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)
