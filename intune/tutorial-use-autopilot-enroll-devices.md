---
title: 教程 - 使用 Autopilot 在 Intune 中注册设备
titleSuffix: Microsoft Intune
description: 在本教程中，将设置 Windows Autopilot 以在 Intune 中注册设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36aa9ad733e2ae5e0f4a292b073fbebd5f5f5f8f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511504"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>教程：使用 Autopilot 在 Intune 中注册 Windows 设备
Windows Autopilot 简化了设备注册。 使用 Microsoft Intune 和 Autopilot 就可向最终用户提供全新设备，而无需生成、维护和应用自定义操作系统映像。 

在本教程中，你将学习如何执行以下操作：
> [!div class="checklist"]
> * 将设备添加到 Intune
> * 创建 Autopilot 设备组
> * 创建 Autopilot 部署配置文件
> * 将 Autopilot 部署配置文件分配到设备组
> * 将 Windows 设备分配给用户

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

有关 Autopilot 优势、方案和先决条件的概述，请参阅 [Windows Autopilot 概述](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)。


## <a name="prerequisites"></a>必备条件
- [设置 Windows 自动注册](quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium 订阅](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>添加设备

设置 Windows Autopilot 的第一步是将 Windows 设备添加到 Intune。 你只需创建一个 CSV 文件并将其导入 Intune。

1. 在任何文本编辑器中，创建标识 Windows 设备的逗号分隔值 (CSV) 列表。 使用以下格式：
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    前三项是必需的，但订单 ID 是可选的。

2. 保存 CSV 文件。

3. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “设备” > “导入”。

    ![Windows Autopilot 设备的屏幕截图](media/enrollment-autopilot/autopilot-import-device.png)

4. 在“添加 Windows Autopilot 设备”下，浏览到所保存的 CSV 文件。

    ![“添加 Windows Autopilot 设备”的屏幕截图](media/enrollment-autopilot/autopilot-import-device2.png)

5. 选择“导入”以开始导入设备信息。 导入可能需要几分钟才能完成。

4. 导入完成后，依次选择“设备注册” > “Windows 注册” > “Windows Autopilot” > “设备” > “同步”。将显示一条指示同步正在进行中的消息。 此过程可能耗时数分钟才能完成，具体取决于正在同步的设备数目。

5. 刷新视图以查看新设备。

## <a name="create-an-autopilot-device-group"></a>创建 Autopilot 设备组

接下来，创建一个设备组，将刚加载的 Autopilot 设备置于该组中。

1. 在 [Azure 门户中的 Intune](https://aka.ms/intuneportal)内，选择“组” > “新建组”。
2. 在“组”边栏选项卡中：
    1. 对于“组类型”，选择“安全”。
    2. 对于“组名称”，输入“Autopilot 组”。 对于“组说明”输入“Autopilot 设备的测试组”。
    3. 对于“成员资格类型”，选择“已分配”。
3. 在“组”边栏选项卡中，选择“成员”并将 Autopilot 设备添加到该组。 尚未注册的 Autopilot 设备使用设备序列号作为名称。
4. 选择“创建”。  

## <a name="create-an-autopilot-deployment-profile"></a>创建 Autopilot 部署配置文件

在创建设备组后，必须创建一个部署配置文件，以便可以配置 Autopilot 设备。

1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件”。
2. 对于“名称”，输入“Autopilot 配置文件”。 对于“说明”输入“Autopilot 设备的测试配置文件”。
3. 将“将所有目标设备转换为 Autopilot”设置为“是”。 此设置可确保列表中的所有设备均注册到 Autopilot 部署服务。 等待 48 小时来处理注册。
4. 对于“部署模式”，选择“用户驱动”。 包含此配置文件的设备与设备注册用户相关联。 必须具备用户凭据，才能注册设备。
5. 在“加入 Azure AD 时的身份”框中，选择“Azure AD 已加入”。
6. 选择“全新体验 (OOBE)”，配置下列选项并将其他选项保留为默认值，然后选择“保存”：
    - **最终用户许可协议(EULA)**：**隐藏**
    - **隐私设置**：**显示**
    - **用户帐户类型**：**标准**

6. 选择“创建”，创建配置文件。 Autopilot 部署配置文件现在即可分配给设备。

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>将 Autopilot 部署配置文件分配到设备组

现已创建部署配置文件，可将其分配到设备组。
1. 在 [Azure 门户中的“Microsoft Intune”](https://aka.ms/intuneportal)内，依次选择“设备注册” > “Windows 注册” > “部署配置文件”>“选择配置文件”。
2. 在特定的配置文件边栏选项卡中，选择“分配”。 
3. 选中“选择组”然后在“选择组”边栏选项卡中，选择“Autopilot 组”然后选中“选择”。

## <a name="distribute-devices-to-users"></a>将设备分配给用户

现在可以将 Windows 设备分配给用户。 在他们首次登录时，Autopilot 系统将自动注册和配置设备。 

## <a name="clean-up-resources"></a>清理资源

如果不想再使用 Autopilot 设备，可以将其删除。

1. 如果已在 Intune 中注册设备，必须先[从 Azure Active Directory 门户中删除设备](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

2. 在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备注册” > “Windows 注册” > “设备”。

3. 在“Windows Autopilot 设备”下，选择要删除的设备，然后选择“删除”。

4. 通过选择“是”确认删除。 删除可能需要几分钟。

## <a name="next-steps"></a>后续步骤

可以找到有关 Windows Autopilot 可用的其他选项的更多信息。

> [!div class="nextstepaction"]
> [深入介绍 Autopilot 注册的文章](enrollment-autopilot.md)


