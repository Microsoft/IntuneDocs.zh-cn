---
title: Microsoft Edge 的 Intune 安全基准设置
titleSuffix: Microsoft Intune
description: Intune 支持的安全基线设置用于管理 Microsoft Edge 浏览器
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c75029c60609b0383e2f647e5b94144d4186248c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754879"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Intune 的 Microsoft Edge 基线设置

查看 Microsoft Intune 支持的 Microsoft Edge web 浏览器基线设置。 Microsoft Edge 基线默认值表示建议的 Microsoft Edge 浏览器配置，并且可能与其他安全基线的基线默认值不匹配。

> [!NOTE]
> Microsoft Edge 基线为公共预览版。 

## <a name="microsoft-edge"></a>Microsoft Edge

- **阻止绕过 Microsoft Defender SmartScreen 站点提示**  
  **默认值**：已启用  
  Microsoft Edge CSP：[浏览器/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  此策略设置允许你确定用户是否可以替代有关潜在恶意网站的 Microsoft Defender SmartScreen 警告。 
  - 如果启用此设置，则用户不能忽略 Microsoft Defender SmartScreen 警告，阻止它们继续进入站点。 
  - 如果禁用或未配置此设置，则用户可以忽略 Microsoft Defender SmartScreen 警告并继续进入站点。

- **最低 SSL 版本已启用**  
  **默认值**：已启用  

  设置最低支持的 SSL 版本。 如果将此策略设置为 "*未配置*"，Microsoft Edge 将使用默认的最低版本的*TLS 1.0*。 当设置为 "*已启用*" 时，可以从以下值中选择最低版本：

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **最低 SSL 版本已启用**  
    **默认**： TLS 1。2

- **阻止绕过有关下载的 Microsoft Defender SmartScreen 警告**  
  **默认值**：已启用  
  Microsoft Edge CSP：[浏览器/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  此策略允许你确定用户是否可以覆盖有关未验证的下载的 Microsoft Defender SmartScreen 警告。
  - 如果启用此策略，则组织中的用户将无法忽略 Microsoft Defender SmartScreen 警告，因此无法完成未经验证的下载。
  - 如果禁用或未配置此策略，用户可以忽略 Microsoft Defender SmartScreen 警告并完成未验证的下载。

- **允许用户从 SSL 警告页继续**  
  **默认值**：已禁用  
  Microsoft Edge CSP：[浏览器/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  当用户访问具有 SSL 错误的站点时，Microsoft Edge 将显示一个警告页。 如果将此策略设置为 "*已启用*" 或 "*未配置*"，则用户可以在这些警告页中单击。 *禁用*此策略后，用户将被阻止单击任何警告页。 

- **默认 Adobe Flash 设置**  
  **默认值**：已启用  
  Microsoft Edge CSP： [browser/AllowFlash](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflash)和[browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  确定未通过 "PluginsAllowedForUrls" 或 "PluginsBlockedForUrls" 覆盖的网站是否可以自动运行 Adobe Flash 插件。 

  - 选择 "BlockPlugins" 以阻止所有站点上的 Adobe Flash
  - 选择 "ClickToPlay" 可让 Adobe Flash 运行，但要求用户单击占位符以启动它。
  
   在任何情况下，"PluginsAllowedForUrls" 和 "PluginsBlockedForUrls" 策略优先于 "DefaultPluginsSetting"。 仅允许在 "PluginsAllowedForUrls" 策略中显式列出的域自动播放。 
   如果要为所有站点启用自动播放，请考虑将 http://* 和 https://* 添加到此列表。 
   
   - 如果将此策略设置为 "*未配置*"，则用户可以手动更改此设置。 * 2 = 阻止 Adobe Flash 插件 * 3 = 单击以播放前面的 "1" 选项集 "全部允许"，但此功能现在仅通过 "PluginsAllowedForUrls" 策略进行处理。 使用 "1" 的现有策略将在 "即用即用" 模式下运行。  
 
  - **默认 Adobe Flash 设置**  
    **默认**：阻止 Adobe Flash 插件

- **为每个站点启用站点隔离**  
  **默认值**：已启用  

  "SitePerProcess" 策略可用于防止用户选择不使用隔离所有站点的默认行为。 你还可以使用 IsolateOrigins 策略来隔离更细化的其他来源。

  - 如果此策略设置为 "*已启用*"，则用户不能选择退出默认行为，其中每个站点都在其自己的进程中运行。 
  - 如果使用 "*已禁用*" 或 "*未配置*"，则用户可以选择退出站点隔离。 （例如，通过使用 edge://flags 中的 "禁用网站隔离" 条目。）禁用策略或不配置策略不会关闭站点隔离。

- **支持的身份验证方案**  
  **默认值**：已启用  

  指定支持的 HTTP 身份验证方案。 可以使用以下值配置策略： "基本"、"digest"、"ntlm" 和 "协商"。 用逗号分隔多个值。 如果未配置此策略，则会使用所有这四个方案。
 
  - **支持的身份验证方案**  
    选择从以下选项： 
    - 基本
    - Digest
    - NTLM  （已默认选择）
    - 协商 *（默认情况下选中）*

- **允许将密码保存到密码管理器**  
  **默认值**：已禁用  
  Microsoft Edge CSP：[浏览器/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  允许 Microsoft Edge 保存用户密码。 
  - 如果启用此策略，用户可在 Microsoft Edge 中保存其密码。 下一次访问该站点时，Microsoft Edge 会自动输入该密码。 
  - 如果禁用此策略，用户将无法保存新密码，但仍可使用以前保存的密码。 
  
  将此策略设置为 "*已启用*" 或 "*已禁用*" 时，用户不能在 Microsoft Edge 中更改或覆盖此策略。 
  
  如果将此项设置为 "*未配置*"，则用户可以保存密码，并关闭此功能。

- **控制无法安装的扩展**  
  **默认值**：已启用  

  列出用户无法在 Microsoft Edge 中安装的特定扩展。 部署此策略时，将禁用此列表上以前安装的任何扩展，并且用户将无法启用它们。 如果从阻止的扩展列表中删除某个项目，则会在之前安装该扩展的任何位置自动重新启用该扩展。
  
  使用 **\*** 阻止允许列表中未显式列出的所有扩展。 如果此策略设置为 "*未配置*"，则用户可以在 Microsoft Edge 中安装任何扩展。 
  
  示例值： extension_id1 extension_id2。  
  <br>
  - **应阻止用户安装的扩展 Id （或 * 表示所有）**  
    选择 "**添加**" 并指定其他扩展。 **\*** 默认处于选中状态。

- **配置 Microsoft Defender SmartScreen**  
  **默认值**：已启用  
  Microsoft Edge CSP：[浏览器/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  此策略设置允许你配置是否启用 Microsoft Defender SmartScreen。 Microsoft Defender SmartScreen 提供警告消息，可帮助用户防范潜在的网页仿冒欺诈和恶意软件。 
  
  - 默认情况下，Microsoft Defender SmartScreen 处于开启状态。 如果启用此设置，则会打开 Microsoft Defender SmartScreen，用户无法将其关闭。
  - 如果禁用此设置，则会关闭 Microsoft Defender SmartScreen，用户无法将其打开。 
  - 当设置为 "*未配置*" 时，用户可以选择是否使用 Microsoft Defender SmartScreen。 
  
  此策略仅适用于加入 Microsoft Active Director 域的 Windows 实例，或已注册用于设备管理的 Windows 10 专业版或企业实例。

- **允许用户级本机消息传递主机（安装时不需要管理员权限）**  
  **默认值**：已禁用  

  启用本机消息传递主机的用户级别安装。 
  - 如果禁用此策略，Microsoft Edge 将仅使用系统级别上安装的本机消息传递主机。 默认情况下，如果未配置此策略，Microsoft Edge 将允许使用用户级本机消息传递主机。

## <a name="next-steps"></a>后续步骤

[在 Intune 中使用安全基线](security-baselines.md)
