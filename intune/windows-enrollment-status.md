---
title: 设置注册状态页
titleSuffix: Microsoft Intune
description: 为注册 Windows 10 设备的用户设置问候语页面。
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
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b87e0d24c000e3083eaebeac1a4cf6026d495ccf
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032089"
---
# <a name="set-up-an-enrollment-status-page"></a>设置注册状态页
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
在使用 Intune 安装设备期间，“注册状态”页将显示设备上的安装信息。 某些应用程序、配置文件和证书在用户完成开箱即用的注册登录到设备时可能尚未安装。 注册状态页有助于用户在设备安装期间了解其设备的状态。 可以创建多个注册状态页配置文件，并将其应用到不同的组。 配置文件可以设置为：
- 显示安装进度。
- 安装完成之前阻止使用。
- 指定用户在设备安装失败时可以执行的操作。

此外，还可以为每个配置文件设置优先级顺序，以对同一用户或设备的配置文件分配冲突做出解释。

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>为所有用户启用默认注册状态页

启用注册状态页，请执行以下步骤。
 
1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > Windows 注册” > 注册状态页(预览)”。
2. 在“注册状态页”边栏选项卡中，选择“默认” > “设置”。
3. 有关“显示应用和配置文件安装进度”，请选择“是”。
4. 选择要打开的其他设置，然后选择“保存”。

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>创建注册状态页配置文件并将其分配到组

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “注册状态页(预览)” > “创建配置文件”。
2. 提供名称和说明。
3. 选择“创建”。
4. 在“注册状态页”列表中选择新配置文件。
5. 选择“分配” > “选择组”> 选择要采用此配置文件的组 >“选择” > “保存”。
6. 选择“设置”> 选择要应用于此配置文件的设置 >“保存”。

## <a name="set-the-enrollment-status-page-priority"></a>设置注册状态页的优先级

设备或用户可能处于多个组中，并且具有多个注册状态页配置文件。 要处理此类冲突，可以为每个配置文件设置优先级。 如果用户具有多个注册状态页配置文件，则仅应用具有最高优先级的配置文件。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > Windows 注册” > 注册状态页(预览)”。
2. 将鼠标悬停在列表中的配置文件上。
3. 使用三个垂直点，将该配置文件拖到列表中的所需位置。

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>在安装特定应用程序之前阻止访问设备

可以指定在用户可以访问桌面之前需要安装哪些应用。

1. 在 Intune 中，选择“设备注册” > “Windows 注册” > “注册状态页(预览)”。
2. 选择配置文件 >“设置”。
3. 有关“显示应用和配置文件安装进度”，请选择“是”。
4. 有关“在安装所有应用和配置文件之前阻止设备使用”，请选择“是”。
5. 有关“如果这些所需应用已分配给用户/设备，则在安装这些应用之前阻止设备使用”，请选择“已选择”。
 6. 选择“选择应用”> 选择应用 >“选择” > “保存”。

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
- 连接性配置文件
    - 为“所有设备”或注册设备是成员的设备组分配 VPN 或 Wi-Fi 配置文件，但仅适用于 Autopilot 设备
- 为“所有设备”或注册设备是成员的设备组分配证书配置文件，但仅适用于 Autopilot 设备

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
