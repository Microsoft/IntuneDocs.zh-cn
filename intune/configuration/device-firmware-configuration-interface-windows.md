---
title: 在 Microsoft Intune 中使用 MDM 策略更新 Windows BIOS 功能 - Azure | Microsoft Docs
description: 添加设备固件配置接口 (DFCI) 配置文件，以便管理 Microsoft Intune 中 Windows 10 设备上的 CPU、内置硬件和启动选项等 UEFI 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9fe2b2174252aa1081eb311d79b4b5ba37f96f2
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755349"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>在 Microsoft Intune 中使用 Windows 设备上的设备固件配置接口配置文件（公共预览版）

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 Intune 管理 Autopilot 设备时，可以在登录设备之后使用设备固件配置接口 (DFCI) 管理 UEFI (BIOS) 设置。 有关优势、方案和先决条件的概述，请参阅 [ DFCI 概述](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/)。

DFCI [支持 Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) 将管理命令从 Intune 传递到 UEFI（统一可扩展固件接口）。

在 Intune 中，使用此功能控制 BIOS 设置。 通常固件更能抵抗恶意攻击。 它限制最终用户对 BIOS 的控制权，这在受威胁时非常有效。

例如，在安全环境中使用 Windows 10 设备，最好禁用相机。 可以在固件层禁用相机，这样最终用户的操作便无关紧要。 重新安装 OS 或擦除计算机不会重新打开相机。 在另一个示例中，锁定启动选项，以防止用户启动另一个 OS 或不具有相同安全功能的旧版本 Windows。

重新安装旧版本 Windows 时，安装独立的 OS 或格式化硬盘不会使 DFCI 管理失效。 此功能可以防止恶意软件与 OS 进程（包括优化的 OS 进程）进行通信。 DFCI 的信任链使用公钥加密，并且不依赖于本地 UEFI (BIOS) 密码安全。 此安全层阻止本地用户通过设备的 UEFI (BIOS) 菜单访问托管设置。

此功能适用于：

- 支持 UEFI 上的 Windows 10 RS5 (1809) 及更高版本

## <a name="before-you-begin"></a>在开始之前

- 设备制造商必须在制造过程中将 DFCI 添加到 UEFI 固件，或将其作为安装的固件更新进行添加。 与设备供应商合作确定[支持 DFCI 的制造商](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci)或使用 DFCI 所需的固件版本。

- 设备必须由 [Microsoft 云解决方案提供商 (CSP) 合作伙伴](https://partner.microsoft.com/cloud-solution-provider)注册为 Windows Autopilot，或由 OEM 直接注册。 

  手动注册 Autopilot 的设备（例如[从 csv 文件](../enrollment/enrollment-autopilot.md#add-devices)导入）无法使用 DFCI。 DFCI 管理默认需要通过 OEM 或 Microsoft CSP 合作伙伴注册 Windows Autopilot 来对设备的商业采购进行外部认证。

  注册设备后，其序列号将显示在 Windows Autopilot 设备列表中。

  有关 Autopilot 的详细信息（包括任何要求），请参阅[使用 Windows AutoPilot 在 Intune 中注册 Windows 设备](../enrollment/enrollment-autopilot.md)。

## <a name="create-your-azure-ad-security-groups"></a>创建 Azure AD 安全组

将 Autopilot 部署配置文件分配到 Azure AD 安全组。 确保创建包含支持 DFCI 设备的组。 对于 DFCI 设备，大多数组织可能会创建设备组，而不是用户组。 请考虑以下方案：

- 人力资源 (HR) 组使用不同的 Windows 设备。 出于安全原因，最好不让此组中的任何人使用设备上的相机。 这种情况下，可以创建 HR 安全用户组，以便策略无视设备类型而应用于 HR 组中的用户。
- 生产车间有 10 台设备。 对于所有这些设备，最好阻止使用 USB 设备启动设备。 这种情况下，可以创建安全设备组，并将这 10 台设备添加到组中。

有关在 Intune 中创建组的详细信息，请参阅[添加组以组织用户和设备](../fundamentals/groups-add.md)。

## <a name="create-the-profiles"></a>创建配置文件

若要使用 DFCI，请创建以下配置文件，并将其分配到组中。

### <a name="create-an-autopilot-deployment-profile"></a>创建 Autopilot 部署配置文件

此配置文件设置并预配新设备。 [Autopilot 部署配置文件](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)列出了创建配置文件所需步骤。

### <a name="create-an-enrollment-state-page-profile"></a>创建注册状态页配置文件

此配置文件确保 Windows 安装过程中设备验证并启用 DFCI。 强烈建议使用此配置文件，在安装所有应用和配置文件之前阻止使用设备。 [注册状态页配置文件](../enrollment/windows-enrollment-status.md)列出了创建配置文件所需步骤。

### <a name="create-the-dfci-profile"></a>创建 DFCI 配置文件

此配置文件包含所配置的 DFCI 设置。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入配置文件的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，“Windows：  在 Windows 设备上配置 DFCI 设置”是个不错的配置文件名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”  。
    - **配置文件类型**：选择“设备固件配置接口”  。

4. 配置设置：

    - **允许本地用户更改 UEFI (BIOS) 设置**：选项包括：
      - **仅未配置的设置**：本地用户可以更改任何设置，但 Intune 显式设置为“启用”或“禁用”的设置除外    。
      - **无**：本地用户可能不会更改任何 UEFI (BIOS) 设置，包括 DFCI 配置文件中未显示的设置。

    - **CPU 和 IO 虚拟化**：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：BIOS 允许使用 OS 使用平台的 CPU 和 IO 虚拟化功能。 它会启用基于 Windows 虚拟化的安全和设备防护技术。
        - **禁用**：BIOS 禁用平台 CPU 和 IO 虚拟化功能，并阻止对其的使用。
    - **相机**：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：启用由 UEFI (BIOS) 直接管理的所有内置相机。 USB 相机等外围设备不受影响。
        - **禁用**：禁用由 UEFI (BIOS) 直接管理的所有内置相机。 USB 相机等外围设备不受影响。
    - **麦克风和扬声器**：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：启用由 UEFI (BIOS) 直接管理的所有内置麦克风和扬声器。 USB 设备等外围设备不受影响。
        - **禁用**：禁用由 UEFI (BIOS) 直接管理的所有内置麦克风和扬声器。 USB 设备等外围设备不受影响。
    - **无线收发器（蓝牙、Wi-fi、NFC 等）** ：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：启用由 UEFI (BIOS) 直接管理的所有内置无线收发器。 USB 设备等外围设备不受影响。
        - **禁用**：禁用由 UEFI (BIOS) 直接管理的所有内置无线收发器。 USB 设备等外围设备不受影响。

        > [!WARNING]
        > 如果禁用“无线收发器”设置，则设备需要有线网络连接  。 否则，可能无法管理设备。

    - **通过外部媒体 (USB、SD) 启动**：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：UEFI (BIOS) 支持通过非硬盘存储启动。
        - **禁用**：UEFI (BIOS) 不支持通过非硬盘存储启动。
    - **通过网络适配器启动**：选项包括：
        - **未配置**：Intune 不涉及此功能，并原样保留任何设置。
        - **启用**：UEFI (BIOS) 支持通过内置网络接口启动。
        - **禁用**：UEFI (BIOS) 不支持启动内置网络接口。

5. 完成后，选择“确定”   > “创建”  以保存所做的更改。 此时，配置文件创建完成，并出现在列表中。

## <a name="assign-the-profiles-and-reboot"></a>分配配置文件，并重启

创建配置文件之后，[即可进行分配](../configuration/device-profile-assign.md)。 确保将配置文件分配到包含 DFCI 设备的 Azure AD 安全组。

设备运行 Windows Autopilot 时，DFCI 可能会在“注册状态页”期间强制重启。 第一次重新启动会将 UEFI 注册到 Intune。 

如果要确认设备已注册，则可以再次重新启动该设备，但这不是必需的。 按设备制造商的说明打开 UEFI 菜单，确认 UEFI 现在已托管。

设备下一次与 Intune 同步时，Windows 将接收 DFCI 设置。 重新启动设备。 需要第三次重新启动，UEFI 才能接收来自 Windows 的 DFCI 设置。

## <a name="update-existing-dfci-settings"></a>更新现有 DFCI 设置

如果要更改所用设备上的现有 DFCI 设置，可执行以下操作。 在现有的 DFCI 配置文件中，更改设置，并保存更改。 由于已分配配置文件，因此新的 DFCI 设置在以下情况下生效：

1. 设备签入 Intune 服务以查看配置文件更新。 可在任意时间点进行签入。 有关详细信息，请参阅[设备获取策略、配置文件或应用更新时](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)。

2. 若要强制执行新的设置，请[远程](../remote-actions/device-restart.md)或本地重启设备。

还可以[向设备发送信号进行签入](../remote-actions/device-sync.md)。 成功同步之后，[发信号示意重启](../remote-actions/device-restart.md)。

>[!NOTE]
> 删除 DFCI 配置文件或从分配到配置文件的组中删除设备不会删除 DFCI 设置或重新启用 UEFI (BIOS) 菜单。 如果要停止使用 DFCI，请更新现有的 DFCI 配置文件。 关于步骤的详细信息，请参阅本文中的[停用设备](#retire)。

## <a name="reuse-retire-or-recover-the-device"></a>重用、停用或恢复设备

### <a name="reuse"></a>重用

如果计划重置 Windows 以更改设备用途，请[擦除设备](../remote-actions/devices-wipe.md)。 请勿删除 Autopilot 设备记录  。

擦除设备之后，将设备移动到分配了新 DFCI 和 Autopilot 配置文件的组。 确保重启设备以重新运行 Windows 设置。

### <a name="retire"></a>停用

准备好停用设备并解除管理之后，在退出状态下将 DFCI 配置文件更新为所需的 UEFI (BIOS) 设置。 通常最好启用所有设置。 例如：

1. 打开 DFCI 配置文件（“设备”   > “配置文件”  ）。
2. 将“允许本地用户更改 UEFI (BIOS) 设置”更改为“仅未配置的设置”   。
3. 将所有其他设置设置为“未配置”  。
4. 保存设置。

这些步骤会解锁设备的 UEFI (BIOS) 菜单。 这些值与配置文件（“已启用”或“已禁用”）相同，并未重置为任何默认的 OS 值   。

现在即可擦除设备。 擦除设备之后，删除 Autopilot 记录。 删除记录会阻止设备在重启时自动重新注册。

### <a name="recover"></a>恢复

如果擦除设备，并在解锁 UEFI (BIOS) 菜单之前删除 Autopilot 记录，则菜单保持锁定。 Intune 无法发送配置文件更新以将其解锁。

若要解锁设备，请打开 UEFI (BIOS) 菜单，然后从网络刷新管理。 恢复会解锁菜单，但会将所有 UEFI (BIOS) 设置设为先前 Intune DFCI 配置文件中的值。

## <a name="end-user-impact"></a>最终用户影响

应用 DFCI 策略时，即便 UEFI (BIOS) 菜单受密码保护，本地用户也无法更改 DFCI 配置的设置。 基于配置的设置，最终用户可能会收到“未找到或无法诊断硬件组件”错误。 请务必为最终用户提供阐明已禁用选项的文档。  

## <a name="next-steps"></a>后续步骤

分配配置文件之后，[监视其状态](../device-profile-monitor.md)。
