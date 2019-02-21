---
title: 在 Microsoft Intune 中添加 PowerShell 脚本以供 Windows 10 设备使用 - Azure | Microsoft Docs
description: 添加 PowerShell 脚本，将脚本策略分配给 Azure Active Directory 组，使用报告监视脚本，并查看如何删除在 Microsoft Intune 中为 Windows 10 设备添加的脚本。 另请参阅一些常见问题和解决方法。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 573ca3aa10094e61165d297730d556e2ef559767
ms.sourcegitcommit: 8e503c1b350f7b29a045b7daf3eece64be4ca3c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2019
ms.locfileid: "56302177"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用

使用 Intune 管理扩展在 Intune 中上传 PowerShell 脚本以在 Windows 10 设备上运行。 管理扩展增强了 Windows 10 移动设备管理 (MDM)，以便更轻松地采用新式管理。

## <a name="moving-to-modern-management"></a>移动到新式管理

最终用户的计算系统正在向数字化转型。 经典、传统的 IT 侧重于单个设备平台、企业拥有的设备、在办公室办公的用户，以及各种手动、反应式 IT 过程。 新式工作区使用多个用户拥有和企业拥有的平台，允许用户随时随地工作，并提供自动化、积极主动的 IT 过程。

Microsoft Intune 等 MDM 服务可以管理运行 Windows 10 的移动和桌面设备。 Windows 10 内置管理客户端可与 Intune 进行通信，以运行企业管理任务。 你可能需要执行一些任务，例如高级设备配置和故障排除。 对于 Win32 应用管理，可以在 Windows 10 设备上使用 [Win32 应用管理](apps-win32-app-management.md)功能。

Intune 管理扩展对 Windows 10 MDM 内置功能进行了补充。 可创建 PowerShell 脚本以在 Windows 10 设备上运行。 例如，可创建 PowerShell 脚本（执行高级设备配置、将脚本上传到 Intune、将脚本分配给 Azure Active Directory (AD) 组），然后运行这些脚本。 然后，可全程监视脚本运行状态。

## <a name="prerequisites"></a>必备条件

Intune 管理扩展具有以下先决条件：

- 必须将设备加入或注册到 Azure AD，且 Azure AD 配置为[自动注册到 Intune](windows-enroll.md#enable-windows-10-automatic-enrollment)。 Intune 管理扩展支持已加入 Azure AD、混合域和已注册共同管理的 Windows 设备。
- 设备必须运行 Windows 10 版本 1607 或更高版本。
- 将 PowerShell 脚本或 Win32 应用部署到用户或设备安全组后，将安装 Intune 管理扩展代理。

## <a name="create-a-powershell-script-policy"></a>创建 PowerShell 脚本策略 

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “PowerShell 脚本” > “添加”。
3. 输入 PowerShell 脚本的“名称”和“说明”。 对于“脚本位置”，请浏览查找该 PowerShell 脚本。 该脚本的大小不能超过 200 KB。
4. 选择**配置**。 然后选择是在设备上（“是”），还是在系统环境中（“否”）通过用户凭据运行该脚本。 默认情况下，脚本在系统环境中运行。 选择“是”，除非脚本必须在系统环境中运行。 
  ![“添加 PowerShell 脚本”窗格](./media/mgmt-extension-add-script.png)
5. 选择是否由受信任的发布者对脚本进行签名（“是”）。 默认情况下，不需要对脚本进行签名。 
6. 选择“确认”，然后选择“创建”以保存脚本。

## <a name="assign-a-powershell-script-policy"></a>分配 PowerShell 脚本策略

1. 在“PowerShell 脚本”中，选择要分配的脚本，然后选择“管理” > “分配”。

    ![“添加 PowerShell 脚本”窗格](./media/mgmt-extension-assignments.png)

2. 选择“选择组”，列出可用的 Azure AD 组。 
3. 选择一个或多个组，其中的用户的设备会接收该脚本。 “选择”分配策略到所选组。

> [!NOTE]
> - 最终用户无需登录设备即可执行 PowerShell 脚本。
> - Intune 中的 PowerShell 脚本可应用于 Azure AD 设备安全组。
> - Intune 中的 PowerShell 脚本可应用于 Azure AD 用户安全组。

Intune 管理扩展客户端每一小时检查一次 Intune。 将策略分配给 Azure AD 组后，PowerShell 脚本将运行，还将报告运行结果。

## <a name="monitor-run-status-for-powershell-scripts"></a>监视 PowerShell 脚本运行状态

可在 Azure 门户中监视用户和设备的 PowerShell 脚本运行状态。

在“PowerShell 脚本”中，选择要监视的脚本并选择“监视”，然后选择以下报表之一：

- **设备状态**
- **用户状态**

## <a name="troubleshoot-powershell-scripts"></a>对 PowerShell 脚本进行故障排除

客户端计算机上的代理日志通常位于 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 可以使用 [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) 查看这些日志文件。 

![代理日志的屏幕截图](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>删除 PowerShell 脚本

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

#### <a name="issue-the-powershell-scripts-do-not-run"></a>问题：未运行 PowerShell 脚本

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
