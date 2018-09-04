---
title: 使用 Windows AutoPilot 注册设备
titleSuffix: Microsoft Intune
description: 了解如何使用 Windows AutoPilot 注册 Windows 10 设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: b3c374e4ce6baeab8cc6fde3f6c45c63c48e34dd
ms.sourcegitcommit: d99def6e4ceb44f3e7ca10fe7cdd7f222cf814c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903069"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>使用 Windows AutoPilot 注册 Windows 设备
Windows AutoPilot 简化了设备预配。 生成和维护自定义操作系统映像的过程非常耗时。 可能还要先花时间将自定义操作系统映像应用到新设备，让其可供使用，然后再提供给最终用户。 使用 Microsoft Intune 和 AutoPilot 就可向最终用户提供全新设备，而无需生成、维护自定义操作系统映像以及将其应用到设备。 使用 Intune 管理 AutoPilot 设备时，可以在注册设备后管理策略、配置文件和应用等。 有关优势、方案和先决条件的概述，请参阅 [Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)（Windows AutoPilot 概述）。

## <a name="prerequisites"></a>必备条件
- [已启用的 Windows 自动注册](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium 订阅](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)<!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>添加设备

可以通过导入具有 Windows AutoPilot 设备信息的 CSV 文件来添加 Windows AutoPilot 设备。

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “设备” > “导入”。

    ![Windows AutoPilot 设备的屏幕快照](media/enrollment-autopilot/autopilot-import-device.png)

2. 在“添加 Windows Autopilot 设备”下，浏览添加 CSV 文件，其中列出了要添加的设备。 此文件应包含序列号、Windows 产品 ID、硬件哈希和可选的设备订单 ID。

    ![“添加 Windows AutoPilot 设备”的屏幕快照](media/enrollment-autopilot/autopilot-import-device2.png)

3. 选择“导入”以开始导入设备信息。 导入可能需要几分钟才能完成。

4. 导入完成后，依次选择“设备注册” > “Windows 注册” > “Windows AutoPilot” > “设备” > “同步”。将显示一条指示同步正在进行中的消息。 此过程可能耗时数分钟才能完成，具体取决于正在同步的设备数目。

5. 刷新视图以查看新设备。

## <a name="create-an-autopilot-device-group"></a>创建 AutoPilot 设备组

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，选择“组”。
2. 在“组”边栏选项卡中：
    1. 对于“组类型”，选择“安全”。
    2. 在“组名称”和“组说明”中，输入名称和说明。
    3. 对于“成员资格类型”，选择“已分配”或“动态设备”。
3. 如果在上一步中选择“已分配”作为“成员资格类型”，请选择“组”边栏选项卡中的“成员”，并将 AutoPilot 设备添加到组中。
    尚未注册的 AutoPilot 设备是将设备序列号用作名称的设备。
4. 如果选择“动态设备”作为“成员资格类型”，请选择“组”边栏选项卡中的“动态设备成员”，并在“高级规则”框中键入以下任意代码。
    - 若要创建包括所有 AutoPilot 设备的组，请键入：`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - 若要创建包括所有具有特定订单 ID 的 AutoPilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - 若要创建包括所有具有特定采购订单 ID 的 AutoPilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    在“高级规则”框中添加代码后，，选择“保存”。
5. 选择“创建”。



## <a name="create-an-autopilot-deployment-profile"></a>创建 AutoPilot 部署配置文件
AutoPilot 部署配置文件用于配置 AutoPilot设备。
1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件”。
2. 在“名称”和（可选）“说明”中，键入名称和说明。
3. 对于“部署模式”，选择下列两个选项之一：
    - “用户驱动”：包含此配置文件的设备与设备注册用户相关联。 必须有用户凭据，才能预配设备。
    - “自部署(预览)”：（Windows 10 Insider Preview 内部版本 17672 或更高版本）包含此配置文件的设备不与设备注册用户相关联。 无需用户凭据，即可预配设备。
4. 在“加入 Azure AD 时的身份”框中，选择“Azure AD 已加入”。
5. 选择“全新体验(OOBE)”，配置下列选项，再选择“保存”：
    - **语言(区域)**\*：选择要对设备使用的语言。 仅当选择“自部署”作为“部署模式”时，此选项才可用。
    - **自动配置键盘**\*：如果选择了“语言(区域)”，请跳过键盘选择页。 仅当选择“自部署”作为“部署模式”时，此选项才可用。
    - “最终用户许可协议(EULA)”：（Windows 10 版本 1709 或更高版本）选择是否向用户显示 EULA。
    - “隐私设置”：选择是否向用户显示隐私设置。
    - “用户帐户类型”：选择用户帐户类型是“管理员”，还是“标准”用户。 

6. 选择“创建”，创建配置文件。 AutoPilot 部署配置文件现在即可分配给设备。

*仅当选择“自部署(预览)”作为“部署模式”时，“语言(区域)”和“自动配置键盘”才可用（Windows 10 Insider Preview 内部版本 17672 或更高版本）。


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>将 AutoPilot 部署配置文件分配到设备组

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件”>“选择配置文件”。
2. 在特定的配置文件边栏选项卡中，选择“分配”。 
3. 选择“选择组”，在“选择组”边栏选项卡中，选择一个或多个要向其分配配置文件的组，再选择“选择”。

## <a name="edit-an-autopilot-deployment-profile"></a>编辑 AutoPilot 部署配置文件
在成功创建 AutoPilot 部署配置文件后，可对该部署配置文件的某些部分进行编辑。   

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册”。
2. 在“Windows 注册”下，选择“Windows AutoPilot”部分中的“部署配置文件”。
3. 选择要编辑的配置文件。
4. 单击左侧的“属性”以更改该部署配置文件的名称或说明。 更改后请单击“保存”。
5. 单击“设置”以对 OOBE 设置进行更改。 更改后请单击“保存”。

> [!NOTE]
> 对配置文件的更改应用于分配有此配置文件的设备。 但是，需在设备重置并重新注册之后，已更新的配置文件才可应用于已在 Intune 中注册的设备。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows AutoPilot 未分配设备警报<!-- 163236 -->
可查看警报，了解 AutoPilot 计划中有多少设备尚未分配有 AutoPilot 部署配置文件。 使用警报中的信息可创建配置文件，并将其分配到未分配的设备。 单击警报时，会看到 Windows AutoPilot 设备的完整列表，以及与之相关的详细信息。

若要查看未分配设备的警报，请在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “概述” > “未分配设备”。  

## <a name="delete-autopilot-devices"></a>删除 AutoPilot 设备

可以删除未注册的 Windows AutoPilot 设备。

1. 如果已在 Intune 中注册设备，必须先[从 Azure Active Directory 门户中删除设备](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

2. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “设备”。

3. 在“Windows AutoPilot 设备”下，选择要删除的设备，然后选择“删除”。

4. 通过选择“是”确认删除。 删除可能需要几分钟。

## <a name="using-autopilot-in-other-portals"></a>在其他门户中使用 AutoPilot
如果对移动设备管理不感兴趣，可以在适用于企业的 Microsoft Store 中使用 AutoPilot（举个例子）。 尽管使用其他门户也是一种选择，但我们建议仅使用 Intune 来管理 AutoPilot 部署。 如果同时使用 Intune 和其他门户，则 Intune 将无法：
- 显示对在 Intune 中创建、但在其他门户中编辑的配置文件的更改
- 同步在其他门户中创建的配置文件
- 显示对在其他门户中完成的配置文件分配的更改
- 同步在其他门户中完成的配置文件分配
- 显示在其他门户中对设备列表所做的更改

## <a name="next-steps"></a>后续步骤
在为已注册的 Windows 10 设备配置 Windows AutoPilot 后，了解如何管理这些设备。 有关详细信息，请参阅[什么是 Microsoft Intune 设备管理？](https://docs.microsoft.com/intune/device-management)
