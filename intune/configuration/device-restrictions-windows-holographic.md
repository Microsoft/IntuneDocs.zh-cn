---
title: Windows Holographic for Business 设备设置 - Microsoft Intune - Azure | Microsoft Docs
description: 阅读在 Microsoft Intune 中配置适用于 Windows Holographic for Business 的设备限制的相关信息并进行配置，包括注销、地理位置、密码、从应用商店安装应用、Microsoft Edge 中的 Cookie 和弹出窗口、Microsoft Defender、搜索、云和存储、蓝牙连接、系统时间，以及 Azure 中的使用情况数据。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f90a5a13859ff19765e22444a84b9c11405af73
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059508"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>便于使用 Intune 允许或限制功能的 Windows Holographic for Business 设备设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出并介绍了可以在 Windows Holographic for Business 设备（如 Microsoft Hololens）上控制的各种设置。 在移动设备管理 (MDM) 解决方案中，使用这些设置可允许或禁用功能、控制安全等。

## <a name="before-you-begin"></a>开始之前

[创建设备配置配置文件](device-restrictions-configure.md#create-the-profile)。

## <a name="general"></a>常规

- **手动注销**：允许用户手动从设备中删除工作区帐户。
- **Cortana**：启用或禁用 Cortana 语音助手。
- **地理位置**：指定设备是否可以使用位置服务信息。

## <a name="password"></a>密码

- **密码**：需要最终用户输入密码才能访问设备。
- **设备从空闲状态返回时需要输入密码**：指定用户必须输入密码以解锁设备。

## <a name="app-store"></a>App Store

- **自动更新应用商店的应用**：允许自动更新从 Microsoft 应用商店安装的应用。
- **受信任的应用安装**：允许对使用受信任的证书签名的应用进行旁加载。
- **开发人员解锁**：允许 Windows 开发人员设置，如允许最终用户修改旁加载的应用。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 浏览器

- **Cookie**：允许浏览器将 Internet Cookie 保存到设备。
- **弹出窗口**：阻止浏览器中的弹出窗口（仅适用于 Windows 10 桌面版）。
- **搜索建议**：允许搜索引擎在你键入搜索短语时建议站点。
- **密码管理器**：启用或禁用 Microsoft Edge 密码管理器功能。
- **发送“请勿跟踪”标头**：配置 Microsoft Edge 浏览器，将“禁止跟踪”标头发送到用户访问的网站。

## <a name="microsoft-defender-smart-screen"></a>Microsoft Defender 智能屏幕

- **Microsoft Edge SmartScreen**：启用 Microsoft Edge SmartScreen，以便访问网站和下载文件。

## <a name="search"></a>搜索

- **搜索位置** - 指定搜索是否可使用位置。 信息

## <a name="cloud-and-storage"></a>云和存储

- **Microsoft 帐户**：使用户可以将 Microsoft 帐户与设备关联。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- **蓝牙**：控制用户是否可以在设备上启用和配置蓝牙。
- **蓝牙可发现性**：允许其他已启用蓝牙的设备可发现此设备。
- **蓝牙广告**：允许设备通过蓝牙接收广告。

## <a name="control-panel-and-settings"></a>控制面板和设置

- **系统时间修改**：阻止最终用户更改设备日期和时间。

## <a name="kiosk---obsolete"></a>展台 - 已过时

这些设置为只读，无法更改。 若要配置展台模式，请参阅[展台设置](kiosk-settings-holographic.md)。

展台设备通常运行特定应用。 用户不得在该设备上访问除展台应用以外的任何功能。

- **展台模式**：标识策略支持的展台模式类型。 选项包括：

  - 未配置（默认设置）：策略不启用展台模式  。 
  - **单应用展台**：配置文件使设备仅运行一个应用。 用户登录时，将启动一个特定应用。 此模式还会限制用户打开新应用或更改正在运行的应用。
  - **多应用展台**：配置文件使设备能够运行多个应用。 用户仅可使用你添加的应用。 多应用展台或固定目标设备的优势为，通过让用户仅访问其所需应用为个人提供易于理解的体验。 并且，从他们的视图中删除不需要的应用。 
  
    添加应用以获取多应用展台体验时，还需添加一个“开始”菜单布局文件。 [“开始”菜单布局文件](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others)包含可在 Intune 中使用的 XML 示例。 

### <a name="single-app-kiosks"></a>单应用展台

输入以下设置：

- **用户帐户**：输入与展台应用关联的本地（对设备而言）用户帐户或 Azure AD 帐户登录名。 对于加入 Azure AD 域的帐户，请使用 `domain\username@tenant.org` 格式输入帐户。 

    对于面向公众且启用自动登录的环境中的展台，应使用具有最低权限的用户类型（如本地标准用户帐户）。 若要针对展台模式配置 Azure Active Directory (AD) 帐户，请使用 `AzureAD\user@contoso.com` 格式。

- **应用的应用程序用户模型 ID (AUMID)** ：输入展台应用的 AUMID。 若要了解详细信息，请参阅 [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)（查找已安装应用的应用程序用户模型 ID）。

## <a name="reporting-and-telemetry"></a>报告和遥测

- **共享使用情况数据**：选择诊断数据提交级别。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
