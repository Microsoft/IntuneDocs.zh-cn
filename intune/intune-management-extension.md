---
title: 在 Microsoft Intune 中将 PowerShell 脚本添加到 Windows 10 设备中 - Azure | Microsoft Docs
description: 创建和运行 PowerShell 脚本，将脚本策略分配给 Azure Active Directory 组，使用报告监视脚本，并查看删除脚本的步骤，这些脚本是在 Microsoft Intune 中的 Windows 10 设备上添加的。 另请参阅一些常见问题和解决方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 230f226cba70a7fc61efd236cc0fde0ca6b7fa68
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68374923"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本

使用 Microsoft Intune 管理扩展在 Intune 中上传 PowerShell 脚本，以在 Windows 10 设备上运行。 管理扩展增强了 Windows 10 移动设备管理 (MDM)，以便更轻松地采用新式管理。

此功能适用于：

- Windows 10 及更高版本

## <a name="move-to-modern-management"></a>迁移到新式管理

最终用户的计算系统正在向数字化转型。 经典、传统的 IT 侧重于单个设备平台、企业拥有的设备、在办公室办公的用户，以及不同的手动、反应式 IT 过程。 新式工作区使用多个用户拥有和企业拥有的平台，允许用户随时随地工作，并提供自动化、积极主动的 IT 过程。

Microsoft Intune 等 MDM 服务可以管理运行 Windows 10 的移动和桌面设备。 Windows 10 内置管理客户端可与 Intune 进行通信，以运行企业管理任务。 你可能需要执行一些任务，例如高级设备配置和故障排除。 对于 Win32 应用管理，可以在 Windows 10 设备上使用 [Win32 应用管理](apps-win32-app-management.md)功能。

Intune 管理扩展对 Windows 10 MDM 内置功能进行了补充。 可创建在 Windows 10 设备上运行的 PowerShell 脚本。 例如，创建执行高级设备配置的 PowerShell 脚本。 然后，将脚本上传到 Intune，将脚本分配到 Azure Active Directory (AD) 组并运行该脚本。 然后，可全程监视脚本运行状态。

## <a name="prerequisites"></a>必备条件

Intune 管理扩展具有以下先决条件。 满足先决条件后，在向用户或设备分配 PowerShell 脚本或 Win32 应用时，系统将自动安装 Intune 管理扩展。

- 运行 Windows 10 版本 1607 或更高版本的设备。 如果设备是通过[批量自动注册](windows-bulk-enroll.md)进行注册的，设备必须运行 Windows 10 版本 1703 或更高版本。 Windows 10 上的 S 模式不支持 Intune 管理扩展，因为该模式禁止运行非存储应用。 
  
- 加入 Azure Active Directory (AD) 的设备，其中包括：  
  
  - 已联接混合 Azure AD 的设备：同时加入 Azure Active Directory (AD) 和本地 Active Directory (AD) 的设备。 相关指南请参阅[规划混合 Azure Active Directory 联接实现](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)。

- 在 Intune 中注册的设备，其中包括：

  - 在组策略 (GPO) 中注册的设备。 相关指南请参阅[通过组策略自动注册 Windows 10 设备](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)。
  
  - 在 Intune 中手动注册的设备，即在下述情况下注册的设备：
  
    - Azure AD 中已启用[自动注册到 Intune](quickstart-setup-auto-enrollment.md)。 最终用户使用本地用户帐户登录设备，将设备手动加入 Azure AD，然后使用其 Azure AD 帐户登录设备。
    
    要么  
    
    - 用户使用其 Azure AD 帐户登录设备，然后在 Intune 中进行注册。

  - 使用 Configuration Manager 和 Intune 的共同托管设备。 确保将  “客户端应用”工作负载设置为“试点 Intune”  或“Intune”  。 若要获取指南，请参阅下列文章： 
  
    - [什么是共同管理](https://docs.microsoft.com/sccm/comanage/overview) 
    - [“客户端应用”工作负载](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [将 Configuration Manager 工作负荷切换到 Intune](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> 确保设备已[加入](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) Azure AD。 仅在 Azure AD 中[注册](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)的设备不会收到你的脚本。

## <a name="create-a-script-policy-and-assign-it"></a>创建脚本策略并分配该策略

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “PowerShell 脚本” > “添加”    。

    ![在 Microsoft Intune 中添加和使用 PowerShell 脚本](./media/mgmt-extension-add-script.png)

3. 在“基本信息”中，输入以下属性并选择“下一步”   ：
    - **名称**：输入 PowerShell 脚本的名称。 
    - **说明**：输入 PowerShell 脚本的说明。 此设置是可选的，但建议进行。
4. 在“脚本设置”中，输入以下属性并选择“下一步”   ：
    - **脚本位置**：浏览 PowerShell 脚本。 脚本必须小于 200 KB (ASCII)。
    - **使用登录凭据运行此脚本**：选择“是”，可以使用设备上的用户凭据运行脚本  。 选择“否”（默认值），在系统上下文中运行该脚本  。 许多管理员选择“是”  。 如果脚本必须在系统上下文中运行，请选择“否”  。
    - **强制执行脚本签名检查**：如果脚本必须由受信任的发布者签名，请选择“是”  。 如果不需要对脚本进行签名，请选择“否”（默认）  。 
    - **在 64 位 PowerShell 主机中运行脚本**：选择“是”，可以在 64 位客户端体系结构上的 64 位 PowerShell (PS) 主机中运行脚本  。 选择“否”（默认），在 32 位 PowerShell 主机中运行脚本  。

      设置为“是”或“否”时，请对新策略行为和现有策略行为使用下表   ：

      | 在 64 位 PS 主机中运行脚本 | 客户端体系结构 | 新的 PS 脚本 | 现有的策略 PS 脚本 |
      | --- | --- | --- | --- | 
      | 否 | 32 位  | 支持 32 位 PS 主机 | 仅在 32 位 PS 主机中运行，该主机适用于 32 位和 64 位体系结构。 |
      | 是 | 64 位 | 在适用于 64 位体系结构的 64 位 PS 主机中运行脚本。 在 32 位上运行时，脚本在 32 位 PS 主机中运行。 | 在 32 位 PS 主机中运行脚本。 如果此设置更改为 64 位，则脚本将在 64 位 PS 主机中打开（它不会运行），并报告结果。 在 32 位上运行时，脚本在 32 位 PS 主机中运行。 |

5. 选择“作用域标记”  。 作用域标记是可选的。 有关详细信息，请参阅[对分布式 IT 使用基于角色的访问控制 (RBAC) 和作用域标记](scope-tags.md)。

    添加作用域标记：

    1. 选择“选择作用域标记”，然后从列表中选择现有作用域标记，然后选择“选择”   。

    2. 完成后，选择“下一步”  。

6. 选择“分配” >  选择要包含的组   。 随即显示 Azure AD 组的现有列表。

    1. 选择一个或多个组，其中的用户的设备会接收该脚本。 选择“选择”  。 你选择的组将显示在列表中，并将收到策略。

        > [!NOTE]
        > Intune 中的 PowerShell 脚本可定向于 Azure AD 设备安全组或 Azure AD 用户安全组。

    2. 选择“下一步”  。

        ![将 PowerShell 脚本分配或部署到 Microsoft Intune 中的设备组](./media/mgmt-extension-assignments.png)

7. 在“查看 + 添加”中，将显示你配置的设置的摘要  。 选择“添加”以保存脚本  。 选择“添加”后，策略将部署到你选择的组  。

## <a name="important-considerations"></a>重要注意事项

- 将脚本设置为用户上下文且最终用户拥有管理员权限时，默认情况下将在管理员权限下运行 PowerShell 脚本。

- 最终用户无需登录设备即可执行 PowerShell 脚本。

- Intune 管理扩展客户端每隔一小时都会检查一次 Intune，并且每次重启后都会对任何新脚本或所做更改进行检查。 将策略分配给 Azure AD 组后，PowerShell 脚本将运行，还将报告运行结果。 脚本执行后，除非脚本或策略发生更改，否则不会再次执行。

## <a name="monitor-run-status"></a>监视运行状态

可在 Azure 门户中监视用户和设备的 PowerShell 脚本运行状态。

在“PowerShell 脚本”中，选择要监视的脚本并选择“监视”，然后选择以下报表之一   ：

- **设备状态**
- **用户状态**

## <a name="intune-management-extension-logs"></a>Intune 管理扩展日志

客户端计算机上的代理日志通常位于 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 查看这些日志文件。 

![Microsoft Intune 中的屏幕截图或 cmtrace 代理日志示例](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>删除脚本

在“PowerShell 脚本”中，右键单击该脚本，然后选择“删除”   。

## <a name="common-issues-and-resolutions"></a>常见问题和解决方法

### <a name="issue-intune-management-extension-doesnt-download"></a>问题：未下载 Intune 管理扩展

**可能的解决方法**：

- 设备未加入 Azure AD。 请确保设备满足本文中的[先决条件](#prerequisites)。 
- 未向用户或设备所属的组分配任何 PowerShell 脚本或 Win32 应用。
- 由于未访问 Internet 和未访问 Windows 推送通知服务 (WNS) 等原因，无法向 Intune 服务嵌入设备。
- 设备处于 S 模式下。 S 模式下运行的设备不支持 Intune 管理扩展。 

要查看是否会自动注册设备，可执行以下操作：

  1. 转至“设置”   > “帐户”   > “访问工作或学校”  。
  2. 选择已加入的帐户 >“信息”  。
  3. 在“高级诊断报告”  下，选择“创建报表”  。
  4. 在 Web 浏览器中，打开 `MDMDiagReport`。
  5. 搜索 MDMDeviceWithAAD 属性  。 如果存在此属性，则设备已自动注册。 如果没有此属性，则未自动注册设备。

[启用 Windows 10 自动注册](windows-enroll.md#enable-windows-10-automatic-enrollment)分步介绍了如何在 Intune 中配置自动注册功能。

### <a name="issue-powershell-scripts-do-not-run"></a>问题：PowerShell 脚本未运行

**可能的解决方法**：

- PowerShell 脚本不会在每次登录时运行。 它们在下述情况下运行：

  - 在向设备分配脚本时
  - 如果更改了脚本，请将其上传，再将其分配给用户或设备
  
    > [!TIP]
    > Microsoft Intune 管理扩展是一项在设备上运行的服务，如同服务应用 (services.msc) 中列出中的任何其他服务一样  。 设备重启后，此服务可能也会重启，并检查是否随附 Intune 服务分配了任何 PowerShell 脚本。 如果 Microsoft Intune 管理扩展服务设置为“手动”，则设备重启后可能不会重启此服务  。

- 确保设备已[加入 Azure AD](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)。 仅加入你的工作区或组织（在 Azure AD 中[注册](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)）的设备不会收到脚本。
- Intune 管理扩展客户端每小时检查一次 Intune 中的脚本或策略是否发生任何更改。
- 确认 Intune 管理扩展已下载到 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`。
- 未在 Surface Hub 或 Windows 10 的 S 模式下运行的脚本。
- 检查日志是否存在任何错误。 请参阅（本文中的）[Intune 管理扩展日志](#intune-management-extension-logs)。
- 对于可能的权限问题，确保将 PowerShell 脚本的属性设置为 `Run this script using the logged on credentials`。 另外，确保已登录的用户具有适当的权限来运行脚本。

- 要隔离脚本问题，请执行以下步骤：

  - 检查设备上的 PowerShell 执行配置。 相关指南请参阅[PowerShell 执行策略](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) 。
  - 使用 Intune 管理扩展运行示例脚本。 例如，创建 `C:\Scripts` 目录，并为每个人提供完全控制权限。 运行以下脚本：

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    如果成功，应创建 output.txt，其中应包括“脚本已运行”文本。

  - 要在不使用 Intune 的情况下测试脚本执行，请在系统帐户中本地使用 [psexec 工具](https://docs.microsoft.com/sysinternals/downloads/psexec)来运行脚本：

    `psexec -i -s`

## <a name="next-steps"></a>后续步骤

配置文件的[监视](device-profile-monitor.md)和[故障排除](device-profile-troubleshoot.md)。
