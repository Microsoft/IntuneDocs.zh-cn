---
title: 在 Microsoft Intune 中创建设备配置文件 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加或配置设备配置文件。 选择平台类型，配置设置并添加作用域标记。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c4c995322234a4a2486d8e6c5e9efd88f78dd63
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390870"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中创建设备配置文件

使用设备配置文件，可以添加和配置设置，然后将这些设置推送到组织中的设备。 [对使用设备配置文件的设备应用功能和设置](device-profiles.md)介绍了更多详细信息，包括可以执行的操作。

本文：

- 列出创建配置文件的步骤。
- 演示如何添加作用域标记以“筛选”配置文件。
- 描述 Windows 10 设备上的适用性规则，并演示如何创建规则。
- 列出设备接收配置文件和任何配置文件更新时的签入刷新周期时间。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”  。 有下列选项：

    - **概述**：列出配置文件的状态，并提供有关分配给用户和设备的配置文件的其他详细信息。
    - **管理**：创建设备配置文件，并上传自定义 [PowerShell 脚本](../apps/intune-management-extension.md)以在配置文件中运行，并使用 [eSIM](esim-device-configuration.md) 向设备添加数据计划。
    - **监视**：检查配置文件的状态（成功或失败），并查看配置文件中的日志。
    - **设置**：在配置文件中添加 SCEP 或 PFX 证书颁发机构，或启用[电信费用管理](telecom-expenses-monitor.md)。

3. 选择“创建配置文件”  。 输入以下属性：

   - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，配置文件名称最好是“整个公司的 WP 电子邮件配置文件”  。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择设备平台。 选项包括：  

       - **Android**
       - **Android 企业**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更高版本**
       - **Windows 10 及更高版本**

   - **配置文件类型**：选择要创建的设置类型。 显示的列表取决于所选择的平台  。
   - **设置**：以下文章介绍了每种配置文件类型的设置：

       - [管理模板](administrative-templates-windows.md)
       - [自定义](../custom-settings-configure.md)
       - [传递优化](../delivery-optimization-windows.md)
       - [设备功能](../device-features-configure.md)
       - [设备限制](device-restrictions-configure.md)
       - [版本升级和模式切换](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Endpoint protection](../protect/endpoint-protection-configure.md)
       - [标识保护](../protect/identity-protection-configure.md)  
       - [展台](kiosk-settings.md)
       - [PKCS 证书](../protect/certficates-pfx-configure.md)
       - [PKCS 导入的证书](../protect/certificates-imported-pfx-configure.md)
       - [首选项文件](preference-file-settings-macos.md)
       - [SCEP 证书](../protect/certificates-scep-configure.md)
       - [受信任的证书](../protect/certificates-configure.md)
       - [更新策略](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows 信息保护](../protect/windows-information-protection-configure.md)

     例如，如果选择“iOS/iPadOS”作为平台，配置文件类型选项外观将类似如下配置文件所示  ：

     ![在 Intune 中创建 iOS 配置文件](./media/device-profile-create/create-device-profile.png)

4. 完成后，选择“确定” > “创建”，保存所做更改   。 此时，配置文件创建完成，并出现在列表中。

## <a name="scope-tags"></a>作用域标记

添加设置后，还可以向配置文件添加作用域标记。 作用域标记筛选策略并将其分配给特定组（例如，“HR”或“所有 US-NC 员工”）。

若要详细了解作用域标记以及可以执行的操作，请参阅[将 RBAC 和作用域标记用于分布式 IT](../fundamentals/scope-tags.md)。

### <a name="add-a-scope-tag"></a>添加作用域标记

1. 选择“作用域(标记)”  。
2. 选择“添加”  以创建新的作用域标记。 或者，从列表中选择现有作用域标记。
3. 选择“确定”，保存所做更改  。

## <a name="applicability-rules"></a>适用性规则

适用于：

- Windows 10 及更高版本

适用性规则允许管理员针对满足特定条件的组中的设备。 例如，你创建了一个适用于所有 Windows 10 设备组的设备限制配置文件  。 接下来，只需将配置文件分配给运行 Windows 10 企业版的设备。

若要执行此任务，请创建适用性规则  。 这些规则对于以下情况非常有用：

- 你使用 Windows 10 教育版 (EDU)。 在毕罗思大学，你希望针对 RS3 和 RS4 之间的所有 Windows 10 EDU 设备。
- 你希望针对 Contoso 人力资源的所有用户，但只需要 Windows 10 专业版或企业版设备。

若要实现这些方案，你需要：

- 创建包括毕罗思大学的所有设备的设备组。 在配置文件中，添加一个在操作系统最低版本为 `16299`、最大版本为 `17134` 时应用的适用性规则。 将此配置文件分配给毕罗思大学设备组。

  分配该配置文件后，该配置文件将应用于输入的最低和最高版本之间的设备。 对于不在输入的最低和最高版本之间的设备，其状态显示为“不适用”  。

- 创建一个用户组，该用户组包括 Contoso 的人力资源 (HR) 中的所有用户。 在配置文件中，添加一个适用性规则，使其适用于运行 Windows 10 专业版或企业版的设备。 将此配置文件分配给 HR 用户组。

  分配该配置文件后，该配置文件将应用于运行 Windows 10 专业版或企业版的设备。 对于未运行这些版本的设备，其状态显示为“不适用”  。

- 如果有两个配置文件具有完全相同的设置，则会应用没有适用性规则的配置文件。 

  例如，ProfileA 针对 Windows 10 设备组，它启用 BitLocker，并且没有适用性规则。 ProfileB 针对相同的 Windows 10 设备组，它启用 BitLocker，并且具有仅将配置文件应用于 Windows 10 企业版的适用性规则。

  如果同时分配了两个配置文件，则会应用 ProfileA，因为它没有适用性规则。 

将配置文件分配给组时，适用性规则充当筛选器，仅针对满足条件的设备。

### <a name="add-a-rule"></a>添加规则

1. 选择“适用性规则”  。 可以选择“规则”、“属性”和“OS 版本”    ：

    ![在 Microsoft Intune 中向设备配置文件添加适用性规则](./media/device-profile-create/applicability-rules.png)

2. 在“规则”  中，选择是否要包括或排除用户或组。 选项包括：

    - **在以下情况下分配配置文件**：包括满足你输入的条件的用户或组。
    - **在以下情况下不分配配置文件**：排除满足你输入的条件的用户或组。

3. 在“属性”  中，选择筛选器。 选项包括： 

    - **OS 版本**：在列表中，选中要在规则中包括（或排除）的 Windows 10 版本。
    - **OS 版本**：输入要在规则中包括（或排除）的最小和最大 Windows 10 版本号   。 两个值都是必需的。

      例如，对于最低版本，可以输入 `10.0.16299.0`（RS3 或 1709），对于最高版本，可以输入 `10.0.17134.0`（RS4 或 1803）。 或者，可以更精细地输入 `10.0.16299.001` 表示最低版本，`10.0.17134.319` 表示最高版本。

4. 选择“添加”  ，保存所做更改。

## <a name="refresh-cycle-times"></a>刷新周期时间

Intune 使用不同的刷新周期来检查配置文件的更新。 如果设备是最近注册的，则会增加运行签入的频率。 [策略和配置文件刷新周期](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)列出了估计的刷新时间。

用户可以随时打开公司门户应用，并同步设备以立即检查配置文件更新。

## <a name="recommendations"></a>建议

创建配置文件时，请考虑下列建议：

- 命名策略，以便了解其定义和用途。 所有[符合性策略](../protect/create-compliance-policy.md)和[配置文件](../configuration/device-profile-create.md)都有一个可选的“说明”  属性。 在“说明”  中，具体明确并包含信息，使其他人知道策略的用途。

  某些配置文件示例包括：

  **配置文件名称**：管理模板 - 适用于所有 Windows 10 用户的 OneDrive 配置文件  
  **配置文件说明**：OneDrive 管理模板配置文件，其中包括适用于所有 Windows 10 用户的最小和基本设置。 由 user@contoso.com 创建，可防止用户将组织数据共享到个人 OneDrive 帐户。

  **配置文件名称**：适用于所有 iOS 用户的 VPN 配置文件  
  **配置文件说明**：VPN 配置文件，其中包括适用于要连接到 Contoso VPN 的所有 iOS 用户的最小和基本设置。 由 user@contoso.com 创建，以便用户自动向 VPN 进行身份验证，而不是提示用户输入其用户名和密码。

- 按照任务创建配置文件，例如配置 Microsoft Edge 设置、启用 Microsoft Defender 防病毒设置、阻止 iOS 越狱设备等。

- 创建适用于特定组（如市场营销、销售、IT 管理员）的配置文件，或按位置或学校系统创建配置文件。

- 将用户策略与设备策略分开。

  例如，[Intune 中的管理模板](administrative-templates-windows.md)具有数百个 ADMX 设置。 这些模板将显示是否将设置应用于用户或设备。 创建管理模板时，将用户设置分配给用户组，并将设备设置分配给设备组。

  下图显示了可应用于用户和/或应用于设备的设置示例：

  ![适用于用户和设备的 Intune 管理模板](./media/device-profile-create/setting-applies-to-user-and-device.png)

## <a name="next-steps"></a>后续步骤

[分配配置文件](../device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
