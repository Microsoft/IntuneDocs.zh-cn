---
title: 注册混合 Active Directory 加入设备 - Windows Autopilot
titleSuffix: ''
description: 使用 Windows Autopilot 在 Microsoft Intune 中注册混合 Active Directory 加入设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f81875afffa461e036bc319febc9a6141967c440
ms.sourcegitcommit: 8e3a20b2ad59d3a6789ee81b9cbe6d2c711da11d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2019
ms.locfileid: "54380469"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>使用 Intune 和 Windows Autopilot（预览版）部署已加入混合 Azure AD 的设备
可以使用 Intune 和 Windows Autopilot 设置已加入混合 Azure Active Directory 的设备。 为此，请执行以下步骤。

## <a name="prerequisites"></a>必备条件

- 成功配置[已加入混合 Azure Active Directory 的设备](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)。
    - 请确保[使用 Get-MsolDevice cmdlet 验证注册]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration)。

要注册的设备还必须：
- 使用 [2018 年 10 月更新](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)运行 Windows 10。
- 可以访问 Internet。
- 可以访问 Active Directory（不支持 VPN 连接）。
- 体验全新体验 (OOBE)。

## <a name="set-up-windows-10-automatic-enrollment"></a>设置 Windows 10 自动注册

1. 登录 [Azure 门户](https://portal.azure.com)，然后选择“Azure Active Directory”。

   ![Azure 门户的屏幕截图](./media/auto-enroll-azure-main.png)

2. 选择“移动性(MDM 和 MAM)”。

   ![Azure 门户的屏幕截图](./media/auto-enroll-mdm.png)

3. 选择“Microsoft Intune”。

   ![Azure 门户的屏幕截图](./media/auto-enroll-intune.png)

4. 确保使用 Intune 和 Windows 部署已加入 Azure Active Directory 的设备的用户是 MDM 用户范围中包含的组成员。

   ![Azure 门户的屏幕截图](./media/auto-enroll-scope.png)

5. 对以下 URL 使用默认值：
    - **MDM 使用条款 URL**
    - **MDM 发现 URL**
    - **MDM 符合性 URL**
6. 选择 **“保存”**。

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>增加组织单位中的计算机帐户限制

可使用适用于 Active Directory 的 Intune Connector 在本地 Active 目录域中创建 Autopilot 注册计算机。 托管 Intune Connector 的计算机必须有权在域中创建计算机对象。 

在某些域中，计算机未被授予创建计算机的权限。 此外，域内置有一个限制（默认值为 10），未获得创建计算机对象的委托权限的所有用户和计算机都要遵循此限制。 因此，必须向在创建混合 Aure AD 加入设备的组织单位上托管 Intune 连接器的计算机委托权限。

授予创建计算机权限的组织单位必须与以下内容匹配：
- 在域加入配置文件中输入的组织单位
- 或者，计算机域的域名（如果未选择配置文件）。

1. 打开“Active Directory 用户和计算机”(DSA.msc)。

2. 右键单击将用于创建已加入混合 Azure AD 的计算机的组织单位 >“委派控制”。

    ![委派控制的屏幕截图](media/windows-autopilot-hybrid/delegate-control.png)

3. 在“控制委派”向导中，选择“下一步” > “添加...” > “对象类型”。

4. 在“对象类型”对话框中，选择“计算机”，然后选择“确定”。

    ![委派控制的屏幕截图](media/windows-autopilot-hybrid/object-types-computers.png)

5. 在“选择用户、计算机或组”对话框的“输入要选择的对象名称”框中，输入安装连接器的计算机的名称。

    ![委派控制的屏幕截图](media/windows-autopilot-hybrid/enter-object-names.png)

6. 选择“检查名称”以验证输入，然后选择确定” > “下一步”。

7. 选择“创建要委派的自定义任务” > “下一步”。

8. 选择“仅文件夹中的以下对象”，然后选中以下选项：
    - **计算机对象**
    - **在此文件夹中创建选定的对象**
    - **删除此文件夹中的选定的对象**

    ![委派控制的屏幕截图](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. 选择“下一步”。

10. 在“权限”下，选择“完全控制”（这将选中所有其他选项）>“下一步” > “完成”。

    ![委派控制的屏幕截图](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>安装 Intune Connector

需要在运行 Windows Server 2016 且有权访问 Internet 和 Active Directory 的计算机上安装适用于 Active Directory 的 Intune Connector。 要增加扩展性和可用性或要支持多个 Active Directory 域，可以在环境中安装多个连接器。 建议在未运行任何其他 Intune 连接器的服务器上安装连接器。

1. 确保已安装并配置语言包，如 [Intune 连接器（预览版）语言要求](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector)中所述。
2. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “适用于 Active Directory 的 Intune Connector（预览版）” > “添加连接器”。 
3. 按照说明下载连接器。
4. 打开下载的连接器安装文件以安装连接器 (ODJConnectorBootstrapper.exe)。
5. 在安装结束时，选择“配置”。
6. 选择“登录”。
7. 输入用户全局管理员或 Intune 管理员角色凭据。
8. 转到“设备注册” > “Windows 注册” > “适用于 Active Directory 的 Intune Connector (预览版)”并确认连接状态为“活动”。

 > [!NOTE]
 > 在连接器中登录后，可能需要几分钟才能显示在 [Intune](https://aka.ms/intuneportal) 中。 请注意，连接器将仅显示是否可以与 Intune 服务成功通信。

### <a name="configure-web-proxy-settings"></a>配置 Web 代理设置

如果网络环境中有 Web 代理，请按照此处的说明操作，让适用于 Active Directory 的 Intune Connector 能够正常运行：[使用现有本地代理服务器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。


## <a name="create-a-device-group"></a>创建设备组
1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“组” > “新建组”。
2. 在“组”边栏选项卡中：
    1. 对于“组类型”，选择“安全”。
    2. 在“组名称”和“组说明”中，输入名称和说明。
    3. 选择“成员身份类型”。
3. 如果选择“动态设备”作为“成员资格类型”，请选择“组”边栏选项卡中的“动态设备成员”，并在“高级规则”框中键入以下任意代码。
    - 若要创建包括所有 Autopilot 设备的组，请键入：`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - 若要创建包括所有具有特定订单 ID 的 Autopilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - 若要创建包括所有具有特定采购订单 ID 的 Autopilot 设备的组，请键入：`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    在“高级规则”框中添加代码后，，选择“保存”。
5. 选择“创建”。  

## <a name="register-your-autopilot-devices"></a>注册 Autopilot 设备

选择以下方法之一注册 Autopilot 设备：

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>注册已注册的 Autopilot 设备

1. 创建 Autopilot 部署配置文件，将“将所有目标设备转换为 Autopilot”设置为“是”。 
2. 将配置文件分配给包含要自动注册到 Autopilot 的成员组。

有关详细信息，请参阅[创建 Autopilot 部署配置文件](enrollment-autopilot.md#create-an-autopilot-deployment-profile)。

### <a name="register-autopilot-devices-that-arent-enrolled"></a>注册未注册的 Autopilot 设备

如果设备尚未注册，可以自行注册。 有关详细信息，请参阅[添加设备](enrollment-autopilot.md#add-devices)。

### <a name="register-devices-from-an-oem"></a>从 OEM 注册设备

如果要购买新设备，某些 OEM 可以为你注册设备。 有关详细信息，请参阅 [Windows Autopilot 页面](http://aka.ms/WindowsAutopilot)。

在注册 Autopilot 设备时（以及在注册到 Intune 之前），可在以下三个地方看到这些设备（名称设置为其序列号）：
- Azure 门户中 Intune 中的“Autopilot 设备”边栏选项卡上（“设备注册” > “Windows 注册” > “设备”）。
- Azure 门户中 Intune 中的“Azure AD 设备”边栏选项卡上（“设备” > “Azure AD 设备”）。
- Azure 门户中 Azure Active Directory 中的 AAD“所有设备”边栏选项卡上（“设备” > “所有设备”）。

注册 Autopilot 设备后，可在以下四个位置看到它们：
- Azure 门户中 Intune 中的“Autopilot 设备”边栏选项卡上（“设备注册” > “Windows 注册” > “设备”）。
- Azure 门户中 Intune 中的“Azure AD 设备”边栏选项卡上（“设备” > “Azure AD 设备”）。
- Azure 门户中 Azure Active Directory 中的 AAD“所有设备”边栏选项卡上（“设备” > “所有设备”）。
- Azure 门户中 Intune 中的“所有设备”边栏选项卡上（“设备” > “所有设备”）。

注册 Autopilot 设备后，其设备名称将更改为设备的主机名。 默认情况下，它以“DESKTOP-”开头。




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>创建并分配 AutoPilot 部署配置文件
Autopilot 部署配置文件用于配置 Autopilot 设备。

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件”。
2. 在“名称”和（可选）“说明”中，键入名称和说明。
3. 对于“部署模式”，选择“用户驱动”。
4. 在“加入到 Azure AD 时的身份”框中，选择“已加入混合 Azure AD”。
5. 选择“全新体验(OOBE)”，根据需要配置下列选项，再选择“保存”。
6. 选择“创建”，创建配置文件。 
7. 在配置文件边栏选项卡中，选择“分配”。
8. 选择“选择组”，在“选择组”边栏选项卡中选择设备组，再单击“选择”。

设备配置文件的状态从“未分配”更改为“正在分配”，最后更改为“已分配”大约会用时 15 分钟。

## <a name="turn-on-the-enrollment-status-page-optional"></a>打开注册状态页面（可选）

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > Windows 注册” > 注册状态页(预览)”。
2. 在“注册状态页”边栏选项卡中，选择“默认” > “设置”。
3. 有关“显示应用和配置文件安装进度”，请选择“是”。
4. 根据需要配置其他选项。
5. 选择 **“保存”**。

## <a name="create-and-assign-a-domain-join-profile"></a>创建并分配域加入配置文件

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“设备配置” > “配置文件” > “创建配置文件”。
2. 输入以下属性：
   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。
   - **平台**：选择“Windows 10 及更高版本”。
   - **配置文件类型**：选择“域加入(预览版)”。
3. 选择“设置”，然后提供 [DN 格式](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name)的“计算机名前缀”、“域名”和（可选）“组织单位”。 
4. 选择“确定” > “创建”。 配置文件随即创建并显示在列表中。
5. 要分配配置文件，请按照[分配设备配置文件](device-profile-assign.md#assign-a-device-profile)下的步骤操作。 

## <a name="next-steps"></a>后续步骤

配置 Windows Autopilot 后，了解如何管理这些设备。 有关详细信息，请参阅[什么是 Microsoft Intune 设备管理？](device-management.md)
