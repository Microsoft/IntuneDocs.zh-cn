---
title: "在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用"
titlesuffix: Azure portal
description: "了解如何在 Intune 中上传 PowerShell 脚本以在 Windows 10 设备上运行。"
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 237d6d090d0aae7f9a0853839b72d55618f4607e
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用
Intune 管理扩展允许你在 Intune 中上传 PowerShell 脚本以在 Windows 10 设备上运行。 管理扩展对 Windows 10 移动设备管理 (MDM) 功能进行了补充，使你可更轻松地采用新式管理。

## <a name="moving-to-modern-management"></a>移动到新式管理
最终用户的计算系统正在向数字化转型。 经典、传统的 IT 侧重于单个设备平台、企业拥有的设备、在办公室办公的用户，以及各种手动、反应式 IT 过程。 而新式工作区使用多个（用户拥有和企业拥有的）设备平台、允许用户随时随地工作，并提供自动化、积极主动的 IT 过程。 

Microsoft Intune 等 MDM 服务可使用 MDM 协议来管理 Windows 10 设备。 Windows 10 内置管理客户端可与 Intune 进行通信，以执行企业管理任务。 它会促使你在 Windows 10 设备上采用新式管理。 但是，可能存在你需要但 Windows 10 MDM 当前并未提供的功能，例如，高级设备配置、故障排除以及旧版 Win32 应用管理。 对于这些功能，可在 Windows 10 设备上运行 Intune 软件客户端。 但无法使用 Windows 10 MDM 提供的新功能。 [比较 Intune 软件客户端与 Windows 10 MDM 的差异](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison)。

Intune 管理扩展对 Windows 10 MDM 内置功能进行了补充。 可创建 PowerShell 脚本以在提供所需功能的 Windows 10 设备上运行。 例如，可创建 PowerShell 脚本（在 Windows 10 设备上安装旧版 Win32 应用、将脚本上传到 Intune、将脚本分配给 Azure Active Directory (AD) 组），然后在 Windows 10 设备上运行这些脚本。 然后，可在 Windows 10 设备上全程监视脚本运行状态。

## <a name="prerequisites"></a>先决条件
Intune 管理扩展具有以下先决条件：
- 设备必须加入 Azure AD
- 设备必须运行 Windows 10 版本 1607 或更高版本

## <a name="create-a-powershell-script-policy"></a>创建 PowerShell 脚本策略 
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
4. 在“设备配置”边栏选项卡上，依次选择“管理” > “PowerShell 脚本”。
5. 在“PowerShell 脚本”边栏选项卡上，选择“添加脚本”。
6. 在“添加 PowerShell 脚本”边栏选项卡上，为 PowerShell 脚本输入“名称”和“说明”。
7. 对于“脚本位置”，请浏览查找该 PowerShell 脚本。 脚本必须小于 10 KB (ASCII) 或 5 KB (Unicode)。
8. 选择“配置”，然后选择是在设备上（“是”），还是在系统环境中（“否”）通过用户凭据运行该脚本。 默认情况下，脚本在系统环境中运行。 选择“是”，除非脚本必须在系统环境中运行。 
  ![“添加 PowerShell 脚本”边栏选项卡](./media/mgmt-extension-add-script.png)
9. 选择是否由受信任的发布者对脚本进行签名（“是”）。 默认情况下，不需要对脚本进行签名。 
10. 单击“确定”，然后单击“创建”以保存脚本。

## <a name="assign-a-powershell-script-policy"></a>分配 PowerShell 脚本策略
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
4. 在“设备配置”边栏选项卡上，依次选择“管理” > “PowerShell 脚本”。
5. 在“PowerShell 脚本”边栏选项卡上，选择要分配的脚本，然后选择“管理” > “分配”。
  ![“添加 PowerShell 脚本”边栏选项卡](./media/mgmt-extension-assignments.png)
 
6. 选择“选择组”，列出可用的 Azure AD 组。 
7. 选择组，然后单击“选择”，将策略分配到所选组。

Intune 管理扩展每一小时与 Intune 同步一次。 将策略分配给 Azure AD 组后，PowerShell 脚本将运行，还将报告运行结果。 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>监视 PowerShell 脚本运行状态
可在 Azure 门户中监视用户和设备的 PowerShell 脚本运行状态。
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
4. 在“设备配置”边栏选项卡上，依次选择“管理” > “PowerShell 脚本”。
5. 在“PowerShell 脚本”边栏选项卡上，选择要监视的脚本并选择“监视”，然后选择以下报告之一：
   - **设备状态**
   - **用户状态**
