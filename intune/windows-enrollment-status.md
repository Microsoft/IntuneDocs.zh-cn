---
title: 设置注册状态页
titleSuffix: Microsoft Intune
description: 为注册 Windows 10 设备的用户献上问候。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f5460db2d646d8bd417baa50d8188acbf69a251d
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827983"
---
# <a name="set-up-an-enrollment-status-page"></a>设置注册状态页
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在安装设备期间，“注册状态”页将显示设备上的安装信息。 用户注册时，可能尚未完全安装某些应用程序、配置文件和证书。 状态页可帮助用户在注册期间和注册后了解其设备的状态。 可以为所有用户启用状态页，也可以创建配置文件以定位特定用户组。  可以设置配置文件以显示安装进度、阻止使用直到安装完成、允许重置等。
 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>为所有用户启用默认注册状态页

要打开所有最终用户的注册状态页，请按照以下步骤操作。
 
1.  在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > Windows 注册” > 注册状态页(预览)”。
2.  在“注册状态页”边栏选项卡中，选择“默认” > “设置”。
3.  有关“显示应用和配置文件安装进度”，请选择“是”。
4.  选择要打开的其他设置，然后选择“保存”。

## <a name="create-enrollment-status-page-profile-to-target-specific-users"></a>创建注册状态页配置文件以定位特定用户

1.  在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “注册状态页(预览)” > “创建配置文件”。
2. 提供名称和说明。
3. 选择“创建”。
4. 在“注册状态页”列表中选择新配置文件。
5. 选择“分配” > “选择组”> 选择要采用此配置文件的组 >“选择” > “保存”。
6. 选择“设置”> 选择要应用于此配置文件的设置 >“保存”。


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
- 尚未跟踪证书，因此这些配置文件将始终显示“0/0”。

### <a name="account-setup"></a>帐户设置
对于帐户设置，注册状态页会跟踪以下各项：
- 安全策略
    - 适用于所有注册的一个 CSP。
    - 此处不跟踪 Intune 配置的实际 CSP。
- 应用程序
    - 为所有设备、所有用户或注册设备的用户所属的用户组分配的每个用户 LoB MSI 应用。
    - 为所有用户或注册设备的用户所属的用户组分配的每台计算机 LoB MSI 应用。
    - 分配到以下任一对象的 LoB 商店应用、在线商店应用和离线商店应用：
        - 所有设备
        - 所有用户
        - 用户组，其中注册设备的用户是安装上下文设置为 User 的成员。
- 连接性配置文件
    - 为所有用户或注册设备的用户所属的用户组分配的 VPN 或 Wi-Fi 配置文件。
- 证书
    - 为所有用户或注册设备的用户所属的用户组分配的证书配置文件。

## <a name="next-steps"></a>后续步骤
设置 Windows 注册页后，了解如何管理 Windows 设备。 有关详细信息，请参阅[什么是 Microsoft Intune 设备管理？](https://docs.microsoft.com/intune/device-management)