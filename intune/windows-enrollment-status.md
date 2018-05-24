---
title: 设置注册状态页
titleSuffix: Microsoft Intune
description: 为注册 Windows 10 设备的用户献上问候。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>设置注册状态页
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在设置设备期间，“注册状态”页将显示最终用户设备上的安装状态信息。 用户注册时，可能尚未完全安装某些应用程序、配置文件和证书。 状态页可帮助用户在注册期间和注册后了解其设备的状态。 可打开所有用户的状态页，并阻止用户在安装分配的所有应用程序和配置文件之前使用设备。
 
要打开所有最终用户的注册状态页，请按照以下步骤操作。
 
1.  在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > Windows 注册” > 注册状态页(预览)”。
2.  在“注册状态页”边栏选项卡中，选择“默认” > “设置”。
3.  有关“显示应用和配置文件安装进度”，请选择“是”。
4.  选择要打开的其他设置，然后选择“保存”。
 
## <a name="enrollment-status-page-tracking-information"></a>注册状态页跟踪信息

状态页跟踪设备准备、设备设置和帐户设置的信息。

### <a name="device-preparation"></a>设备准备

对于设备准备，注册状态页跟踪受信任的平台模块 (TPM) 密钥证明（如果适用）、加入 Azure Active Directory 以及注册 Intune 的进度。

### <a name="device-setup"></a>设备设置

对于设备设置，如果分配给所有设备，则注册状态页会跟踪以下各项：
- 安全策略
    - 适用于所有注册的一个配置服务提供程序 (CSP)。
    - 此处不跟踪 Intune 配置的实际 CSP。
- 应用程序
    - 每台计算机业务线 (LoB) MSI 应用。
    - LoB 应用商店应用（安装上下文为设备）。
    - 离线应用商店和 LoB 应用商店应用（安装上下文为设备）。
- 尚未跟踪连接配置文件（VPN 和 Wi-Fi），因此这些配置文件将始终显示“0/0”。
- 尚未跟踪证书，因此这些证书将始终显示“0/0”。

### <a name="account-setup"></a>帐户设置
对于帐户设置，注册状态页会跟踪以下各项：
- 安全策略
    - 适用于所有注册的一个 CSP。
    - 此处不跟踪 Intune 配置的实际 CSP。
- 应用程序
    - 为所有设备、所有用户或注册设备的用户所属的用户组分配的每个用户 LoB MSI 应用。
    - 为所有用户或注册设备的用户所属的用户组分配的每台计算机 LoB MSI 应用。
    - 为所有设备、所有用户或注册设备的用户所属的用户组分配的 LoB 应用商店应用（安装上下文为用户）。
    - 为所有设备、所有用户或注册设备的用户所属的用户组分配的联机应用商店应用（安装上下文为用户）。
    - 为所有设备、所有用户或注册设备的用户所属的用户组分配的脱机应用商店应用（安装上下文为用户）。
- 连接性配置文件
    - 为所有用户或注册设备的用户所属的用户组分配的 VPN 或 Wi-Fi 配置文件。
- 证书
    - 为所有用户或注册设备的用户所属的用户组分配的证书配置文件。

## <a name="next-steps"></a>后续步骤
设置 Windows 注册页后，了解如何管理 Windows 设备。 有关详细信息，请参阅[什么是 Microsoft Intune 设备管理？](https://docs.microsoft.com/intune/device-management)