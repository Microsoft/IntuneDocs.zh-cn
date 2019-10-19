---
title: Microsoft Intune 中适用于 Windows 10 的展台设置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 将 Windows 10（及更高版本）设备配置为单应用和多应用展台、自定义开始菜单、添加应用、显示任务栏，以及配置 Web 浏览器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17dce8f7c5aa55a2044e663f724a5784cee8b375
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506679"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>使用 Intune 将 Windows 10 及更高版本设备作为展台运行的设置

在 Windows 10 及更高版本设备上，可以将这些设备配置为，在单应用展台模式或多应用展台模式下运行。

本文列出并介绍了可以在 Windows 10 和更高版本设备上控制的不同设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置将 Windows 10 及更高版本设备配置为在展台模式下运行。

作为 Intune 管理员，可以创建这些设置，并将它们分配到设备。

若要详细了解 Intune 中的 Windows 展台功能，请参阅[配置展台设置](../kiosk-settings.md)。

## <a name="before-you-begin"></a>在开始之前

- [创建配置文件](kiosk-settings.md#create-the-profile)。

- 此展台配置文件与使用 [Microsoft Edge 展台设置](device-restrictions-windows-10.md#microsoft-edge-browser)创建的设备限制配置文件直接相关。 总结：

  1. 创建此展台配置文件以在展台模式下运行设备。
  2. 创建[设备限制配置文件](device-restrictions-windows-10.md#microsoft-edge-browser)，并配置可在 Microsoft Edge 中使用的特定功能和设置。

> [!IMPORTANT]
> 请务必将此展台配置文件和 [Microsoft Edge 配置文件](device-restrictions-windows-10.md#microsoft-edge-browser)分配给相同设备。

## <a name="single-full-screen-app-kiosks"></a>单个全屏应用展台

只能在设备上运行一个应用。

- 选择展台模式：选择单应用全屏展台   。

- 用户登录类型  ：添加的应用以你输入的用户帐户的身份运行。 选项包括：

  - **自动登录（Windows 10 版本 1803 和更高版本）** ：用于不需要用户登录的面向公众的环境中的展台，类似于来宾帐户。 此设置使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - 本地用户帐户  ：输入本地（对设备而言）用户帐户。 输入的帐户会在展台中登录。

- 应用程序类型：选择应用程序类型  。 选项包括：

  - **添加 Microsoft Edge 浏览器**：选择“Microsoft Edge 浏览器”，再选择“Edge 展台模式类型”   ：

    - **数字/互动标牌**：打开 URL 全屏，仅显示该网站上的内容。 [设置数字标牌](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供有关此功能的详细信息。
    - **公共浏览 (InPrivate)** ：运行 Microsoft Edge 的受限多标签页版本。 用户可公开浏览或结束正在浏览的会话。

    要详细了解这些选项，请参阅[部署 Microsoft Edge 展台模式](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

    > [!NOTE]
    > 此设置会在设备上启用 Microsoft Edge 浏览器。 要配置 Microsoft Edge 专属设置，请创建设备配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10”（针对平台），再选择“设备限制” >  “Microsoft Edge 浏览器”       ）。 [Microsoft Edge 浏览器](device-restrictions-windows-10.md#microsoft-edge-browser)列出并介绍了可用设置。

  - **添加展台浏览器**：选择“展台浏览器设置”  。 这些设置控制展台上的 Web 浏览器应用。 请确保从应用商店获取[展台浏览器应用](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)，并将其作为[客户端应用](../apps/apps-add.md)添加到 Intune。 然后，将应用分配到展台设备。

    输入以下设置：

    - 默认主页 URL  ：输入展台浏览器打开或重新启动时显示的默认 URL。 例如，输入 `http://bing.com` 或 `http://www.contoso.com`。

    - 主页按钮  ：显示  或隐藏  展台浏览器的主页按钮。 默认情况下，不会显示该按钮。

    - 导航按钮  ：显示  或隐藏  前进和后退按钮。 默认情况下，不会显示导航按钮。

    - 结束会话按钮  ：显示  或隐藏  结束会话按钮。 显示时，用户选择该按钮，应用会提示结束会话。 确认后，浏览器会清除所有浏览数据（Cookie、缓存等），然后打开默认 URL。 默认情况下，不会显示该按钮。

    - 空闲时间后刷新浏览器  ：输入展台浏览器以刷新状态重新启动之前的空闲时长（1-1440 分钟）。 空闲时间是自用户上次交互以来的分钟数。 默认情况下，该值为空，这意味着没有任何空闲超时。

    - 允许的网站  ：使用此设置允许特定网站打开。 换言之，使用此功能可在设备上限制或阻止网站。 例如，可以允许 `http://contoso.com*` 中的所有网站打开。 默认情况下，允许所有网站。

      要允许特定网站，请以单独的行上传包含允许的网站列表的文件。 如果未添加文件，则允许所有网站。 Intune 支持 `*`（星号）作为通配符。

      示例文件应类似于以下列表：

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`

    > [!NOTE]
    > 使用 Microsoft 展台浏览器启用了自动登录功能的 Windows 10 网亭必须使用来自 Microsoft Store for Business 的脱机许可证。 此要求是因为自动登录使用的本地用户帐户没有 Azure Active Directory （AD）凭据。 因此，无法评估联机许可证。 有关详细信息，请参阅[分发脱机应用](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)。

  - **添加商店应用**：选择“添加商店应用”，再从列表中选择应用  。

    未列出任何应用？ 使用[客户端应用](../apps/apps-add.md)中的步骤添加一些应用。
    
 - **指定应用重启的维护时段**：默认值为 "未配置"，请选择 "需要" 以检查是否有应用需要重新启动才能完成安装。
 
     如果使用展台浏览器或其他 Microsoft Store for business 应用，请决定检查应用更新是否需要重新启动才能完成应用程序安装的频率。 如果未配置此设置，则在安装应用更新后，业务应用 Microsoft Store 将在非计划的时间启动3天。
     
     - **维护时段开始时间**：选择开始检查客户端是否有任何需要重新启动的应用程序更新的日期和时间。 默认开始时间为午夜或零分钟。
     
     - **维护时段定期**：默认为每天。
         设置应用更新的维护时段发生的频率。 建议为每日建议，以避免不计划的应用重启。

  [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## <a name="multi-app-kiosks"></a>多应用展台

在此模式下，可从开始菜单使用应用。 其中仅包含用户可以打开的应用。 如果某应用在另一应用上有依赖项，则这两者都必须包含在“允许的应用”列表中。 例如，Internet Explorer 64 位在 Internet Explorer 32 位上有依赖项，因此必须同时允许“C:\Program Files\internet explorer\iexplore.exe”和“C:\Program Files (x86)\Internet Explorer\iexplore.exe”。 

- **选择展台模式**：选择“多应用展台”  。

- **在 S 模式设备中定位 Windows 10**：
  - **是**：展台配置文件中允许应用商店应用和 AUMID 应用（Win32 应用除外）。
  - **否**：展台配置文件中允许应用商店应用、Win32 应用和 AUMID 应用。 此展台配置文件不会部署到 S 模式下的设备。

- 用户登录类型  ：添加的应用以你输入的用户帐户的身份运行。 选项包括：

  - **自动登录（Windows 10 版本 1803 和更高版本）** ：用于不需要用户登录的面向公众的环境中的展台，类似于来宾帐户。 此设置使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - 本地用户帐户  ：添加  本地（对设备而言）用户帐户。 输入的帐户会在展台中登录。
  - **Azure AD 用户或组（Windows 10 版本 1803 和更高版本）** ：选择“添加”，然后从列表中选择 Azure AD 用户或组  。 你可以选择多个用户和组。 选取“选择”  ，保存所做的更改。
  - **HoloLens 访问者**：访问者帐户是来宾帐户，不需要任何用户凭据或身份验证，如[共享电脑模式概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)中所述。

- **浏览器和应用程序**：添加要在展台设备上运行的应用。 请记住，可以添加多个应用。

  - **浏览器**

    - **添加 Microsoft Edge**：Microsoft Edge 会添加到应用网格中，且所有应用程序均可在此展台上运行。 选择“Microsoft Edge 展台模式类型”  ：

      - **正常模式（Microsoft Edge 完整版）** ：运行带有全部浏览功能的完整版 Microsoft Edge。 会话期间会保存用户数据和状态。
      - **公共浏览 (InPrivate)** ：运行多标签页版本的 Microsoft Edge InPrivate，为全屏模式下运行的展台提供量身定制的体验。

      要详细了解这些选项，请参阅[部署 Microsoft Edge 展台模式](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

      > [!NOTE]
      > 此设置会在设备上启用 Microsoft Edge 浏览器。 要配置 Microsoft Edge 专属设置，请创建设备配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10”（针对平台），再选择“设备限制” >  “Microsoft Edge 浏览器”       ）。 [Microsoft Edge 浏览器](device-restrictions-windows-10.md#microsoft-edge-browser)列出并介绍了可用设置。

    - **添加展台浏览器**：这些设置控制展台上的 Web 浏览器应用。 请确保使用[客户端应用](../apps/apps-add.md)向展台设备部署 Web 浏览器应用。

      输入以下设置：

      - 默认主页 URL  ：输入展台浏览器打开或重新启动时显示的默认 URL。 例如，输入 `http://bing.com` 或 `http://www.contoso.com`。

      - 主页按钮  ：显示  或隐藏  展台浏览器的主页按钮。 默认情况下，不会显示该按钮。

      - 导航按钮  ：显示  或隐藏  前进和后退按钮。 默认情况下，不会显示导航按钮。

      - 结束会话按钮  ：显示  或隐藏  结束会话按钮。 显示时，用户选择该按钮，应用会提示结束会话。 确认后，浏览器会清除所有浏览数据（Cookie、缓存等），然后打开默认 URL。 默认情况下，不会显示该按钮。

      - 空闲时间后刷新浏览器  ：输入展台浏览器以刷新状态重新启动之前的空闲时长（1-1440 分钟）。 空闲时间是自用户上次交互以来的分钟数。 默认情况下，该值为空，这意味着没有任何空闲超时。

      - 允许的网站  ：使用此设置允许特定网站打开。 换言之，使用此功能可在设备上限制或阻止网站。 例如，可以允许 `contoso.com*` 中的所有网站打开。 默认情况下，允许所有网站。

        若要允许特定网站，请上传包含允许的网站列表的 .csv 文件。 如果未添加 .csv 文件，则允许所有网站。

      > [!NOTE]
      > 使用 Microsoft 展台浏览器启用了自动登录功能的 Windows 10 网亭必须使用来自 Microsoft Store for Business 的脱机许可证。 此要求是因为自动登录使用的本地用户帐户没有 Azure Active Directory （AD）凭据。 因此，无法评估联机许可证。 有关详细信息，请参阅[分发脱机应用](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)。

  - 应用程序 

    - 添加应用商店应用  ：从适用于企业的 Microsoft Store 中添加应用。 如果未列出任何应用，则可以获取应用，并[将其添加到 Intune](../apps/store-apps-windows.md)。 例如，可以添加展台浏览器、Excel、OneNote 等。

    - 添加 Win32 应用  ：Win32 应用是一个传统的桌面应用，如 Visual Studio Code 或 Google Chrome。 输入以下属性：

      - 应用程序名称  ：必填。 输入应用程序的名称。
      - 本地路径  ：必填。 输入可执行文件的路径，例如 `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 或 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`。
      - **应用程序用户模型 ID (AUMID)** ：输入 Win32 应用的应用程序用户模型 ID (AUMID)。 此设置确定桌面上磁贴的开始布局。 若要获取此 ID，请参阅 [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)。

    - 按 AUMID 添加  ：使用此选项可添加收件箱 Windows 应用，如记事本或计算器。 输入以下属性：

      - 应用程序名称  ：必填。 输入应用程序的名称。
      - 应用程序用户模型 ID (AUMID)  ：必填。 输入 Windows 应用的应用程序用户模型 ID (AUMID)。 若要获取此 ID，请参阅[查找已安装应用的应用程序用户模型 ID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)。

    - **自动启动**：可选。 选择在用户登录时要自动启动的应用程序。 仅自动启动一个应用。
    - 磁贴大小  ：必填。 选择“小”、“中”、“宽”或“大”的应用磁贴大小。

  > [!TIP]
  > 在添加所有应用后，可以通过在列表中单击并拖动应用更改显示顺序。  

- 使用替代“开始”布局  ：选择“是”  输入一个 XML 文件，用于描述应用在开始菜单上的显示方式，包括应用的顺序。 如果在开始菜单中需要更多自定义，请使用此选项。 相关指导和示例 XML，请参阅[自定义和导出“开始”布局](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)。

- Windows 任务栏  ：选择“显示”  或“隐藏”  任务栏。 默认情况下，不会显示任务栏。 可以看到图标（如 Wi-fi 图标），但最终用户无法更改这些设置。

- **允许访问 Downloads 文件夹**：选择“是”，让用户能够访问 Windows 资源管理器中的 Downloads 文件夹  。 默认禁用对 Downloads 文件夹的访问。 此功能通常由最终用户用来访问从浏览器下载的项目。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 和 [Windows Holographic for Business](kiosk-settings-holographic.md) 设备创建展台配置文件。
