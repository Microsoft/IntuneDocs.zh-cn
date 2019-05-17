---
title: 在 Microsoft Intune 中创建设备配置文件 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加或配置设备配置文件。 选择平台类型、配置设置并添加作用域标记。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570398"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>在 Microsoft Intune 中创建设备配置文件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用设备配置文件，可以添加和配置设置，然后将这些设置推送到组织中的设备。 [对使用设备配置文件的设备应用功能和设置](device-profiles.md)介绍了更多详细信息，包括可以执行的操作。

本文：

- 列出创建配置文件的步骤。
- 演示如何添加作用域标记以“筛选”配置文件。
- 列出设备接收配置文件和任何配置文件更新时的签入刷新周期时间。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。

2. 选择“设备配置”。 有下列选项：

    - **概述**：列出配置文件的状态，并提供有关分配给用户和设备的配置文件的其他详细信息。
    - **管理**：创建设备配置文件，并上传自定义 [PowerShell 脚本](intune-management-extension.md)以在配置文件中运行，并使用 [eSIM](esim-device-configuration.md) 向设备添加数据计划。
    - **监视**：检查配置文件的状态（成功或失败），并查看配置文件中的日志。
    - **设置**：在配置文件中添加 SCEP 或 PFX 证书颁发机构，或启用[电信费用管理](telecom-expenses-monitor.md)。

3. 依次选择“配置文件” > “创建配置文件”。 输入以下属性：

   - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，配置文件名称最好是“整个公司的 WP 电子邮件配置文件”。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择设备平台。 选项包括：  

       - **Outlook Web Access (OWA)**
       - **Android 企业**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更高版本**
       - **Windows 10 及更高版本**

   - **配置文件类型**：选择要创建的设置类型。 显示的列表取决于所选择的平台。
   - **设置**：以下文章介绍了每种配置文件类型的设置：

       - [管理模板](administrative-templates-windows.md)
       - [自定义](custom-settings-configure.md)
       - [传递优化](delivery-optimization-windows.md)
       - [设备功能](device-features-configure.md)
       - [设备限制](device-restrictions-configure.md)
       - [版本升级和模式切换](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Endpoint protection](endpoint-protection-configure.md)
       - [标识保护](identity-protection-configure.md)  
       - [展台](kiosk-settings.md)
       - [PKCS 证书](certficates-pfx-configure.md)
       - [SCEP 证书](certificates-scep-configure.md)
       - [受信任的证书](certificates-configure.md)
       - [更新策略](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows 信息保护](windows-information-protection-configure.md)

     例如，如果选择“iOS”作为平台，配置文件类型选项外观将如下所示：

     ![在 Intune 中创建 iOS 配置文件](./media/create-device-profile.png)

4. 完成后，选择“确定” > “创建”，保存所做更改。 此时，配置文件创建完成，并出现在列表中。

## <a name="scope-tags"></a>作用域标记

添加设置后，还可以向配置文件添加作用域标记。 作用域标记筛选策略并将其分配给特定组（例如，“HR”或“所有 US-NC 员工”）。

若要详细了解作用域标记以及可以执行的操作，请参阅[将 RBAC 和作用域标记用于分布式 IT](scope-tags.md)。

### <a name="add-a-scope-tag"></a>添加作用域标记

1. 选择“作用域(标记)”。
2. 选择“添加”以创建新的作用域标记。 或者，从列表中选择现有作用域标记。
3. 选择“确定”，保存所做更改。

## <a name="refresh-cycle-times"></a>刷新周期时间

Intune 使用以下刷新周期来检查配置文件的更新：

| 平台 | 刷新周期|
| --- | --- |
| iOS | 每 6 小时一次 |
| macOS | 每 6 小时一次 |
| Android | 每 8 小时一次 |
| 注册为设备的 Windows 10 PC | 每 8 小时一次 |
| Windows Phone | 每 8 小时一次 |
| Windows 8.1 | 每 8 小时一次 |

如果设备是最近注册的，则会增加运行签入的频率：

| 平台 | 频率 |
| --- | --- |
| iOS | 6 小时内每 15 分钟一次，之后每 6 小时一次 |  
| macOS | 6 小时内每 15 分钟一次，之后每 6 小时一次 | 
| Android | 15 分钟内每 3 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| 注册为设备的 Windows 10 PC | 30 分钟内每 3 分钟一次，之后每 8 小时一次 | 
| Windows Phone | 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 
| Windows 8.1 | 15 分钟内每 5 分钟一次，接下来的 2 小时内每 15 分钟一次，之后每 8 小时一次 | 

用户可以随时打开公司门户应用，并同步设备以立即检查配置文件更新。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
