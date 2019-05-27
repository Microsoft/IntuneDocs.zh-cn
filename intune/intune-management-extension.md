---
title: 在 Microsoft Intune 中将 PowerShell 脚本添加到 Windows 10 设备中 - Azure | Microsoft Docs
description: 创建和运行 PowerShell 脚本，将脚本策略分配给 Azure Active Directory 组，使用报告监视脚本，并查看删除脚本的步骤，这些脚本是在 Microsoft Intune 中的 Windows 10 设备上添加的。 另请参阅一些常见问题和解决方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7ea047daca5dad327b431986840a59074614d1
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732637"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本

使用 Microsoft Intune 管理扩展在 Intune 中上传 PowerShell 脚本，以在 Windows 10 设备上运行。 管理扩展增强了 Windows 10 移动设备管理 (MDM)，以便更轻松地采用新式管理。

此功能适用于：

- Windows 10 及更高版本

## <a name="move-to-modern-management"></a>迁移到新式管理

最终用户的计算系统正在向数字化转型。 经典、传统的 IT 侧重于单个设备平台、企业拥有的设备、在办公室办公的用户，以及不同的手动、反应式 IT 过程。 新式工作区使用多个用户拥有和企业拥有的平台，允许用户随时随地工作，并提供自动化、积极主动的 IT 过程。

Microsoft Intune 等 MDM 服务可以管理运行 Windows 10 的移动和桌面设备。 Windows 10 内置管理客户端可与 Intune 进行通信，以运行企业管理任务。 你可能需要执行一些任务，例如高级设备配置和故障排除。 对于 Win32 应用管理，可以在 Windows 10 设备上使用 [Win32 应用管理](apps-win32-app-management.md)功能。

Intune 管理扩展对 Windows 10 MDM 内置功能进行了补充。 可创建 PowerShell 脚本以在 Windows 10 设备上运行。 例如，可创建 PowerShell 脚本（执行高级设备配置、将脚本上传到 Intune、将脚本分配给 Azure Active Directory (AD) 组），然后运行这些脚本。 然后，可全程监视脚本运行状态。

## <a name="prerequisites"></a>必备条件

Intune 管理扩展具有以下先决条件：

- 必须将设备加入或注册到 Azure AD，且 Azure AD 和 Intune 配置为[自动注册](quickstart-setup-auto-enrollment.md)。 Intune 管理扩展支持已加入 Azure AD、混合 Azure AD 域和已注册共同管理的 Windows 设备。
- 设备必须运行 Windows 10 版本 1607 或更高版本。
- 将 PowerShell 脚本或 Win32 应用部署到用户或设备安全组后，将安装 Intune 管理扩展代理。

## <a name="create-a-script-policy"></a>创建脚本策略 

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “PowerShell 脚本” > “添加”。
3. 输入以下属性：
    - **名称**：输入 PowerShell 脚本的名称。 
    - **说明**：输入 PowerShell 脚本的说明。 此设置是可选的，但建议进行。 
    - **脚本位置**：浏览 PowerShell 脚本。 脚本必须小于 200 KB (ASCII)。
4. 选择“配置”，并输入以下属性：
    - **使用登录凭据运行此脚本**：选择“是”，可以使用设备上的用户凭据运行脚本。 选择“否”（默认值），在系统上下文中运行该脚本。 许多管理员选择“是”。 如果脚本必须在系统上下文中运行，请选择“否”。
    - **强制执行脚本签名检查**：如果脚本必须由受信任的发布者签名，请选择“是”。 如果不需要对脚本进行签名，请选择“否”（默认）。 
    - **在 64 位 PowerShell 主机中运行脚本**：选择“是”，可以在 64 位客户端体系结构上的 64 位 PowerShell (PS) 主机中运行脚本。 选择“否”（默认），在 32 位 PowerShell 主机中运行脚本。

      设置为“是”或“否”时，请对新策略行为和现有策略行为使用下表：

      | 在 64 位 PS 主机中运行脚本 | 客户端体系结构 | 新的 PS 脚本 | 现有的策略 PS 脚本 |
      | --- | --- | --- | --- | 
      | 否 | 32 位  | 支持 32 位 PS 主机 | 仅在 32 位 PS 主机中运行，该主机适用于 32 位和 64 位体系结构。 |
      | 是 | 64 位 | 在适用于 64 位体系结构的 64 位 PS 主机中运行脚本。 在 32 位上运行时，脚本在 32 位 PS 主机中运行。 | 在 32 位 PS 主机中运行脚本。 如果此设置更改为 64 位，则脚本将在 64 位 PS 主机中打开（它不会运行），并报告结果。 在 32 位上运行时，脚本在 32 位 PS 主机中运行。 |

    ![在 Microsoft Intune 中添加和使用 PowerShell 脚本](./media/mgmt-extension-add-script.png)
5. 选择“确定” > “创建”保存脚本。

> [!NOTE]
> 将 PowerShell 脚本设置为用户上下文且设备上的最终用户具有管理员权限时，将在管理员权限下运行该脚本（默认情况）。

## <a name="assign-the-policy"></a>分配策略

1. 在“PowerShell 脚本”中，选择要分配的脚本，然后选择“管理” > “分配”。

    ![将 PowerShell 脚本分配或部署到 Microsoft Intune 中的设备组](./media/mgmt-extension-assignments.png)

2. 选择“选择组”，列出可用的 Azure AD 组。 
3. 选择一个或多个组，其中的用户的设备会接收该脚本。 “选择”分配策略到所选组。

> [!NOTE]
> - 最终用户无需登录设备即可执行 PowerShell 脚本。
> - Intune 中的 PowerShell 脚本可应用于 Azure AD 设备安全组。
> - Intune 中的 PowerShell 脚本可应用于 Azure AD 用户安全组。

对于任何新脚本或更改，Intune 管理扩展客户端都会每隔一小时检查一次，并在每次重启后使用 Intune 检查。 将策略分配给 Azure AD 组后，PowerShell 脚本将运行，还将报告运行结果。 脚本执行后，除非脚本或策略发生更改，否则不会再次执行。

## <a name="monitor-run-status"></a>监视运行状态

可在 Azure 门户中监视用户和设备的 PowerShell 脚本运行状态。

在“PowerShell 脚本”中，选择要监视的脚本并选择“监视”，然后选择以下报表之一：

- **设备状态**
- **用户状态**

## <a name="troubleshoot-scripts"></a>故障排除脚本

客户端计算机上的代理日志通常位于 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 查看这些日志文件。 

![Microsoft Intune 中的屏幕截图或 cmtrace 代理日志示例](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>删除脚本

在“PowerShell 脚本”中，右键单击该脚本，然后选择“删除”。

## <a name="common-issues-and-resolutions"></a>常见问题和解决方法

PowerShell 脚本不会在每次登录时运行。 它们仅在重新启动后运行，或在重新启动“Microsoft Intune 管理扩展”服务后运行。 Intune 管理扩展客户端每小时检查一次 Intune 中的脚本或策略发生的任何更改。

#### <a name="issue-intune-management-extension-doesnt-download"></a>问题：未下载 Intune 管理扩展

**可能的解决方法**：

- 确保在 Azure AD 中自动注册设备。 若要确认，在设备上执行以下操作： 

  1. 转至“设置” > “帐户” > “访问工作或学校”。
  2. 选择已加入的帐户 >“信息”。
  3. 在“高级诊断报告”下，选择“创建报表”。
  4. 在 Web 浏览器中打开 `MDMDiagReport`，然后转到“已注册的配置源”部分。
  5. 查找“MDMDeviceWithAAD”属性。 如果此属性不存在，则不会自动注册用户的设备。

    [启用 Windows 10 自动注册](windows-enroll.md#enable-windows-10-automatic-enrollment)包括相关步骤。

#### <a name="issue-powershell-scripts-do-not-run"></a>问题：PowerShell 脚本未运行

**可能的解决方法**：

- 确认 Intune 管理扩展已下载到 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`。
- 在 Surface Hub 上未运行脚本。
- 检查 `\ProgramData\Microsoft\IntuneManagementExtension\Logs` 中的日志是否存在任何错误。
- 对于可能的权限问题，确保将 PowerShell 脚本的属性设置为 `Run this script using the logged on credentials`。 另外，确保已登录的用户具有适当的权限来运行脚本。
- 若要找出脚本问题，请运行示例脚本。 例如，创建 `C:\Scripts` 目录，并为每个人提供完全控制权限。 运行以下脚本：

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  如果成功，应创建 output.txt，其中应包括“脚本已运行”文本。

- 若要在不使用 Intune 的情况下测试脚本执行，请本地使用 [psexec 工具](https://docs.microsoft.com/sysinternals/downloads/psexec)在系统上下文中运行脚本：

  `psexec -i -s`

## <a name="next-steps"></a>后续步骤

配置文件的[监视](device-profile-monitor.md)和[故障排除](device-profile-troubleshoot.md)。
