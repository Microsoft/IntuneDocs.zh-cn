---
title: 使用 Windows Autopilot 注册设备
titleSuffix: Microsoft Intune
description: 了解如何使用 Windows Autopilot 注册 Windows 10 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65c19f58e41e4f8a739ae16a1b56703fb743b738
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513080"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>使用 Windows Autopilot 在 Intune 中注册 Windows 设备  
Windows Autopilot 简化了 Intune 中的设备注册。 生成和维护自定义操作系统映像的过程非常耗时。 可能还要先花时间将自定义操作系统映像应用到新设备，让其可供使用，然后再提供给最终用户。 使用 Microsoft Intune 和 Autopilot 就可向最终用户提供全新设备，而无需生成、维护自定义操作系统映像以及将其应用到设备。 使用 Intune 管理 Autopilot 设备时，可以在注册设备后管理策略、配置文件和应用等。 有关优势、方案和先决条件的概述，请参阅 [Windows Autopilot 概述](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)。


## <a name="prerequisites"></a>必备条件
- [已启用的 Windows 自动注册](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium 订阅](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>如何获取用于在 Intune 中导入的 CSV

请参阅“了解 powershell cmdlet”，了解使用说明。

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>添加设备

可以通过导入具有 Windows Autopilot 设备信息的 CSV 文件来添加这些设备。

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “设备” > “导入”。

    ![Windows Autopilot 设备的屏幕截图](media/enrollment-autopilot/autopilot-import-device.png)

2. 在“添加 Windows Autopilot 设备”下，浏览添加 CSV 文件，其中列出了要添加的设备。 此文件应列出序列号、Windows 产品 ID、硬件哈希和可选的设备订单 ID。

    ![“添加 Windows Autopilot 设备”的屏幕截图](media/enrollment-autopilot/autopilot-import-device2.png)

3. 选择“导入”以开始导入设备信息。 导入可能需要几分钟才能完成。

4. 导入完成后，依次选择“设备注册” > “Windows 注册” > “Windows Autopilot” > “设备” > “同步”。将显示一条指示同步正在进行中的消息。 此过程可能耗时数分钟才能完成，具体取决于正在同步的设备数目。

5. 刷新视图以查看新设备。

## <a name="create-an-autopilot-device-group"></a>创建 Autopilot 设备组

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal)内，选择“组” > “新建组”。
2. 在“组”边栏选项卡中：
    1. 对于“组类型”，选择“安全”。
    2. 在“组名称”和“组说明”中，输入名称和说明。
    3. 对于“成员资格类型”，选择“已分配”或“动态设备”。
3. 如果在上一步中选择“已分配”作为“成员资格类型”，请选择“组”边栏选项卡中的“成员”，并将 Autopilot 设备添加到组中。
    尚未注册的 Autopilot 设备使用设备序列号作为名称。
4. 如果选择“动态设备”作为“成员资格类型”，请选择“组”边栏选项卡中的“动态设备成员”，并在“高级规则”框中键入以下任意代码。
    - 若要创建包括所有 Autopilot 设备的组，请键入：`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - 若要创建包括所有具有特定订单 ID 的 Autopilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - 若要创建包括所有具有特定采购订单 ID 的 Autopilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    在“高级规则”框中添加代码后，，选择“保存”。
5. 选择“创建”。  

## <a name="create-an-autopilot-deployment-profile"></a>创建 Autopilot 部署配置文件
Autopilot 部署配置文件用于配置 Autopilot 设备。
1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件”。
2. 在“名称”和（可选）“说明”中，键入名称和说明。
3. 如果希望已分配组中的所有设备自动转换为 Autopilot，请把“将所有目标设备转换为 Autopilot”设置为“是”。 已分配组中的所有非 Autopilot 设备都将注册 Autopilot 部署服务。 等待 48 小时来处理注册。 取消注册设备并重置后，Autopilot 将对其进行注册。 以这种方式注册设备后，禁用此选项或删除配置文件分配将不会从 Autopilot 部署服务中删除该设备。 必须改为[直接删除该设备](enrollment-autopilot.md#delete-autopilot-devices)。
4. 对于“部署模式”，选择下列两个选项之一：
    - **用户驱动**：包含此配置文件的设备与设备注册用户相关联。 必须具备用户凭据，才能注册设备。
    - **自部署(预览)**：（需要 Windows 10 版本 1809 或更高版本）包含此配置文件的设备不与设备注册用户相关联。 无需用户凭据，即可注册设备。
5. 在“加入 Azure AD 时的身份”框中，选择“Azure AD 已加入”。
6. 选择“全新体验(OOBE)”，配置下列选项，再选择“保存”：
    - **语言(区域)**\*：选择要对设备使用的语言。 仅当选择“自部署”作为“部署模式”时，此选项才可用。
    - **自动配置键盘**\*：如果选择了“语言(区域)”，请选择“是”以跳过键盘选择页。 仅当选择“自部署”作为“部署模式”时，此选项才可用。
    - **最终用户许可协议(EULA)**：（Windows 10 版本 1709 或更高版本）选择是否向用户显示 EULA。
    - **隐私设置**：选择是否向用户显示隐私设置。
    - **隐藏更改帐户选项（需要 Windows 10 版本 1809 或更高版本）**：选择“隐藏”可防止在公司登录和域错误页上显示更改帐户选项。 要执行此操作，需[在 Azure Active Directory 中配置公司品牌](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)。
    - **用户帐户类型**：选择用户的帐户类型（“管理员”或“标准”用户）。
    - **应用计算机名称模板（需要 Windows 10 版本 1809 或更高版本）**：选择“是”可创建模板，以便在注册期间命名设备时使用。 名称长度必须在 15 个字符或以下，可以包含字母、数字和连字符。 名称不能全为数字。 使用 [%SERIAL% 宏](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)添加特定于硬件的序列号。 或者使用 [%RAND:x% 宏](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)，添加随机数字字符串，其中 x 等于要添加的位数。 

6. 选择“创建”，创建配置文件。 Autopilot 部署配置文件现在即可分配给设备。

*仅当选择“自部署(预览)”作为“部署模式”时，“语言(区域)”和“自动配置键盘”才可用（需要 Windows 10 版本 1809 或更高版本）。


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>将 Autopilot 部署配置文件分配到设备组

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件”>“选择配置文件”。
2. 在特定的配置文件边栏选项卡中，选择“分配”。 
3. 选择“选择组”，在“选择组”边栏选项卡中，选择一个或多个要向其分配配置文件的组，再选择“选择”。


> [!NOTE]
> Intune 将定期检查分配组中的新设备，然后开始将配置文件分配到这些设备的过程。 此过程可能需要几分钟才能完成。 部署设备前，请确保此过程已完成。  可以在“设备注册”>“Windows 注册”>“设备”下进行检查，其中应该看到配置文件状态从“未分配”更改为“正在分配”，并最终更改为“已分配”。

## <a name="edit-an-autopilot-deployment-profile"></a>编辑 Autopilot 部署配置文件
在成功创建 Autopilot 部署配置文件后，可对该部署配置文件的某些部分进行编辑。   

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册”。
2. 在“Windows 注册”下，选择“Windows Autopilot”部分中的“部署配置文件”。
3. 选择要编辑的配置文件。
4. 单击左侧的“属性”以更改该部署配置文件的名称或说明。 更改后请单击“保存”。
5. 单击“设置”以对 OOBE 设置进行更改。 更改后请单击“保存”。

> [!NOTE]
> 对配置文件的更改应用于分配有此配置文件的设备。 但是，需在设备重置并重新注册之后，已更新的配置文件才可应用于已在 Intune 中注册的设备。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>针对 Windows Autopilot 未分配设备的警报  <!-- 163236 -->  

警报将显示没有 Autopilot 部署配置文件的 Autopilot 程序设备数。 使用警报中的信息可创建配置文件，并将其分配到未分配的设备。 单击警报时，可看到 Windows Autopilot 设备的完整列表，以及与之相关的详细信息。


若要查看未分配设备的警报，请在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “概述” > “未分配设备”。  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>将用户分配到特定 Autopilot 设备

可以将用户分配到特定 Autopilot 设备 进行此分配，进行 Windows 设置时将在[公司品牌](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)登录页预填充来自 Azure Active Directory 的用户。 它还允许设置自定义问候语名称。 它不会预填充或修改 Windows 登录名。 只能以这种方式分配拥有许可证的 Intune 用户。

先决条件：配置了 Azure Active Directory 公司门户和 Windows 10 版本 1809 或更高版本。

1. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “设备”>“选择设备”>“分配用户”。

    ![分配用户的屏幕截图](media/enrollment-autopilot/assign-user.png)

2. 选择已获得使用 Intune 的许可证的 Azure 用户，并选择“选择”。

    ![选择用户的屏幕截图](media/enrollment-autopilot/select-user.png)

3. 在“用户友好名称”框中，键入友好名称或接受默认值。 此字符串是用户在 Windows 设置期间登录时显示的友好名称。

    ![友好名称的屏幕截图](media/enrollment-autopilot/friendly-name.png)

4. 选择“确定”。


## <a name="delete-autopilot-devices"></a>删除 Autopilot 设备

可以删除未注册的 Windows Autopilot 设备。

1. 如果已在 Intune 中注册设备，必须先[从 Azure Active Directory 门户中删除设备](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

2. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “设备”。

3. 在“Windows Autopilot 设备”下，选择要删除的设备，然后选择“删除”。

4. 通过选择“是”确认删除。 删除可能需要几分钟。

## <a name="using-autopilot-in-other-portals"></a>在其他门户中使用 Autopilot
如果对移动设备管理不感兴趣，可以在其他门户中使用 Autopilot。 尽管使用其他门户也是一种选择，但我们建议仅使用 Intune 来管理 Autopilot 部署。 如果同时使用 Intune 和其他门户，Intune 将无法：  

- 显示对在 Intune 中创建、但在其他门户中编辑的配置文件的更改
- 同步在其他门户中创建的配置文件
- 显示对在其他门户中完成的配置文件分配的更改
- 同步在其他门户中完成的配置文件分配
- 显示在其他门户中对设备列表所做的更改

## <a name="windows-autopilot-for-existing-devices"></a>现有设备的 Windows Autopilot

通过 Configuration Manager [使用 Autopilot 为现有设备注册](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)时，可以按交换码 ID 对 Windows 设备进行分组。 交换码 ID 是 Autopilot 配置文件的参数。 [Azure AD 设备属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) 将自动设置为“OfflineAutopilotprofile - \< correlator ID\>”。 如此，即可使用 enrollmentprofileName 属性基于交换码 ID 创建任意 Azure AD 动态组。

>[!WARNING] 
> 由于在 Intune 中未预先列出交换码 ID，因此设备可能会报告所需的任何交换码 ID。 如果用户创建与 Autopilot 或 Apple DEP 配置文件名称匹配的交换码 ID，设备将基于 enrollmentProfileName 属性添加到任何动态 Azure AD 设备组。 避免此冲突的方法：
> - 始终创建根据整个 enrollmentProfileName 值进行匹配的动态组规则
> - 从不以“OfflineAutopilotprofile-”开头命名 Autopilot 或 Apple DEP 配置文件。

## <a name="next-steps"></a>后续步骤
在为已注册的 Windows 10 设备配置 Windows Autopilot 后，了解如何管理这些设备。 有关详细信息，请参阅[什么是 Microsoft Intune 设备管理？](https://docs.microsoft.com/intune/device-management)
