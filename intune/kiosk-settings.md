---
title: Microsoft Intune 中适用于 Windows 10 的展台设置 - Azure | Microsoft Docs
description: 将 Windows 10（及更高版本）设备配置为单应用和多应用展台，包括自定义开始菜单，添加应用、任务栏和配置 Web 浏览器。 并在 Microsoft Intune 中将 Windows Holographic for Business 设备配置为多应用展台。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3de4d79e6121505718a75ffe64102bb1bc18347
ms.sourcegitcommit: 244456907e3ab4a4389d32d06060606a9591cfba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2018
ms.locfileid: "50751637"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune 中适用于 Windows 10 （及更高版本）的展台设置

在 Windows 10 设备上，可以使用 Intune 将这些设备作为展台运行。 展台可以运行一个应用，也可以运行多个应用。 还可以显示和自定义开始菜单、添加不同的应用（包括 Win32 应用）、向 Web 浏览器添加特定主页等。 

使用本文中的此步骤在 Intune 中创建单应用展台或多应用展台。

Intune 支持每台设备一个展台配置文件。 如果在单台设备上需要多个展台配置文件，可以使用[自定义 OMA-URI](custom-settings-windows-10.md)。

## <a name="kiosk-settings"></a>展台设置

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - 平台：选择“Windows 10 及更高版本”
   - 配置文件类型：选择“展台(预览)”

4. 选择“展台模式”。 “展台模式”标识策略支持的展台模式类型。 选项包括：

    - **未配置**（默认设置）：策略不启用展台模式。
    - 单个应用、全屏展台：设备以单个用户帐户的身份运行，并锁定到单个应用商店应用。 所以，用户登录时，将启动一个特定应用。 此模式还会限制用户打开新应用或更改正在运行的应用。
    - 多应用展台：设备通过使用应用程序用户模型 ID (AUMID) 运行多个应用商店应用、Win32 应用或收件箱 Windows 应用。 设备上仅可使用你添加的应用。

        多应用展台或固定目标设备的优势在于，让用户仅访问其所需应用，提供易于理解的体验。 同时从其视图中删除他们不需要的应用。

## <a name="single-full-screen-app-kiosks"></a>单个全屏应用展台
当选择单应用展台模式时，请输入以下设置：

- 用户登录类型：添加的应用以你输入的用户帐户的身份运行。 选项包括：

  - 自动登录（Windows 10 版本 1803 和更高版本）：对于不需要用户登录的面向公众的环境中的展台，类似于来宾帐户。 此设置使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - 本地用户帐户：输入本地（对设备而言）用户帐户。 输入的帐户用于登录到展台。

- 应用程序类型：选择“应用商店应用”。

- 要在展台模式下运行的应用：选择“添加应用商店应用”，并从列表中选择应用。

    未列出任何应用？ 使用[客户端应用](apps-add.md)中的步骤添加一些应用。

    选择“确定”，保存所做更改。

- 展台浏览器设置：这些设置控制展台上的 Web 浏览器应用。 确保从应用商店获取[展台浏览器应用](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)，将其作为[客户端应用](apps-add.md)添加到 Intune，然后将应用分配给展台设备。

  输入以下设置：

  - 默认主页 URL：输入展台浏览器打开或重新启动时显示的默认 URL。 例如，输入 `http://bing.com` 或 `http://www.contoso.com`。

  - 主页按钮：显示或隐藏展台浏览器的主页按钮。 默认情况下，不会显示该按钮。

  - 导航按钮：显示或隐藏前进和后退按钮。 默认情况下，不会显示导航按钮。

  - 结束会话按钮：显示或隐藏结束会话按钮。 显示时，用户选择该按钮，应用会提示结束会话。 确认后，浏览器会清除所有浏览数据（Cookie、缓存等），然后打开默认 URL。 默认情况下，不会显示该按钮。

  - 空闲时间后刷新浏览器：输入展台浏览器以刷新状态重新启动之前的空闲时长（1-1440 分钟）。 空闲时间是自用户上次交互以来的分钟数。 默认情况下，该值为空，这意味着没有任何空闲超时。

  - 允许的网站：使用此设置允许特定网站打开。 换言之，使用此功能可在设备上限制或阻止网站。 例如，可以允许 `http://contoso.com*` 中的所有网站打开。 默认情况下，允许所有网站。

    若要允许特定网站，请上传包含允许的网站列表的 .csv 文件。 如果未添加 .csv 文件，则允许所有网站。 Intune 支持 *（星号）作为通配符。

  选择“确定”，保存所做更改。

## <a name="multi-app-kiosks"></a>多应用展台

在此模式下，可从开始菜单使用应用。 其中仅包含用户可以打开的应用。

当选择多应用展台模式时，请输入以下设置：

- 在 S 模式设备中定位 Windows 10：选择“是”以在展台配置文件中允许应用商店应用和 AUMID 应用（不包括 Win32 应用）。 选择“否”以在展台配置文件中允许应用商店应用、Win32 应用和 AUMID 应用。 选择“否”时，此展台配置文件不会部署到 S 模式设备。

- 用户登录类型：添加的应用以你输入的用户帐户的身份运行。 选项包括：

  - 自动登录（Windows 10 版本 1803 和更高版本）：对于不需要用户登录的面向公众的环境中的展台，类似于来宾帐户。 此设置使用 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。
  - 本地用户帐户：添加本地（对设备而言）用户帐户。 输入的帐户用于登录到展台。
  - Azure AD 用户或组（Windows 10 版本 1803 和更高版本）：选择“添加”以从列表中选择 Azure AD 用户或组。 你可以选择多个用户和组。 选取“选择”，保存所做的更改。
  - **HoloLens 访问者**：访问者帐户是来宾帐户，不需要任何用户凭据或身份验证，如[共享电脑模式概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)中所述。

- 应用程序：添加要在展台设备上运行的应用。 请记住，可以添加多个应用。

  - 添加应用商店应用：从适用于企业的 Microsoft Store 中添加应用。 如果未列出任何应用，则可以获取应用，并[将其添加到 Intune](store-apps-windows.md)。 例如，可以添加展台浏览器、Excel、OneNote 等。

  - 添加 Win32 应用：Win32 应用是一个传统的桌面应用，如 Visual Studio Code 或 Google Chrome。 输入以下属性：

    - 应用程序名称：必填。 输入应用程序的名称。
    - 本地路径：必填。 输入可执行文件的路径，例如 `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 或 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`。
    - **应用程序用户模型 ID (AUMID)**：输入 Win32 应用的应用程序用户模型 ID (AUMID)。 此设置确定桌面上磁贴的开始布局。 若要获取此 ID，请参阅[查找已安装应用的应用程序用户模型 ID](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)。
    - 磁贴大小：必填。 选择“小”、“中”、“宽”或“大”的应用磁贴大小。
  
  - 按 AUMID 添加：使用此选项可添加收件箱 Windows 应用，如记事本或计算器。 输入以下属性： 

    - 应用程序名称：必填。 输入应用程序的名称。
    - 应用程序用户模型 ID (AUMID)：必填。 输入 Windows 应用的应用程序用户模型 ID (AUMID)。 若要获取此 ID，请参阅[查找已安装应用的应用程序用户模型 ID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)。
    - 磁贴大小：必填。 选择“小”、“中”、“宽”或“大”的应用磁贴大小。

  > [!TIP]
  > 在添加所有应用后，可以通过在列表中单击并拖动应用更改显示顺序。  

  选择“确定”，保存所做更改。

- 展台浏览器设置：这些设置控制展台上的 Web 浏览器应用。 请确保使用[客户端应用](apps-add.md)向展台设备部署 Web 浏览器应用。

  输入以下设置：

  - 默认主页 URL：输入展台浏览器打开或重新启动时显示的默认 URL。 例如，输入 `http://bing.com` 或 `http://www.contoso.com`。

  - 主页按钮：显示或隐藏展台浏览器的主页按钮。 默认情况下，不会显示该按钮。

  - 导航按钮：显示或隐藏前进和后退按钮。 默认情况下，不会显示导航按钮。

  - 结束会话按钮：显示或隐藏结束会话按钮。 显示时，用户选择该按钮，应用会提示结束会话。 确认后，浏览器会清除所有浏览数据（Cookie、缓存等），然后打开默认 URL。 默认情况下，不会显示该按钮。

  - 空闲时间后刷新浏览器：输入展台浏览器以刷新状态重新启动之前的空闲时长（1-1440 分钟）。 空闲时间是自用户上次交互以来的分钟数。 默认情况下，该值为空，这意味着没有任何空闲超时。

  - 允许的网站：使用此设置允许特定网站打开。 换言之，使用此功能可在设备上限制或阻止网站。 例如，可以允许 `contoso.com*` 中的所有网站打开。 默认情况下，允许所有网站。

    若要允许特定网站，请上传包含允许的网站列表的 .csv 文件。 如果未添加 .csv 文件，则允许所有网站。

  选择“确定”，保存所做更改。

- 使用替代“开始”布局：选择“是”输入一个 XML 文件，用于描述应用在开始菜单上的显示方式，包括应用的顺序。 如果在开始菜单中需要更多自定义，请使用此选项。 相关指导和示例 XML，请参阅[自定义和导出“开始”布局](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)。

- Windows 任务栏：选择“显示”或“隐藏”任务栏。 默认情况下，不会显示任务栏。

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

在 Windows Holographic for Business 设备上，可将这些设备配置为以单应用展台模式或多应用展台模式运行。 在 Windows Holographic for Business 上不支持某些功能。

#### <a name="single-full-screen-app-kiosks"></a>单个全屏应用展台
当选择单应用展台模式时，请输入以下设置：

- 用户登录类型：选择“本地用户帐户”，以输入与展台应用相关联的本地（对设备而言）用户帐户或 Microsoft Account (MSA) 帐户。 Windows Holographic for Business 不支持“自动登录”用户帐户类型。

- 应用程序类型：选择“应用商店应用”。

- 要在展台模式下运行的应用：选择“添加应用商店应用”，并从列表中选择应用。

    未列出任何应用？ 使用[客户端应用](apps-add.md)中的步骤添加一些应用。

    选择“确定”，保存所做更改。

#### <a name="multi-app-kiosks"></a>多应用展台
在此模式下，可从开始菜单使用应用。 其中仅包含用户可以打开的应用。 当选择多应用展台模式时，请输入以下设置：

- 在 S 模式设备中定位 Windows 10：选择“否”。 在 Windows Holographic for Business 上不支持 S 模式。

- 用户登录类型：添加一个或多个可以使用你添加的应用的用户帐户。 选项包括： 

  - 自动登录：在 Windows Holographic for Business 上不支持。
  - 本地用户帐户：添加本地（对设备而言）用户帐户。 输入的帐户用于登录到展台。
  - Azure AD 用户或组（Windows 10 版本 1803 和更高版本）：需要用户凭据以登录到设备。 选择“添加”以从列表中选择 Azure AD 用户或组。 你可以选择多个用户和组。 选取“选择”，保存所做的更改。
  - **HoloLens 访问者**：访问者帐户是来宾帐户，不需要任何用户凭据或身份验证，如[共享电脑模式概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)中所述。

- 应用程序：添加要在展台设备上运行的应用。 请记住，可以添加多个应用。

  - 添加应用商店应用：选择使用[客户端应用](apps-add.md)添加的现有应用。 如果未列出任何应用，则可以获取应用，并[将其添加到 Intune](store-apps-windows.md)。
  - 添加 Win32 应用：在 Windows Holographic for Business 上不支持。
  - 按 AUMID 添加：使用此选项可添加收件箱 Windows 应用。 输入以下属性： 

    - 应用程序名称：必填。 输入应用程序的名称。
    - 应用程序用户模型 ID (AUMID)：必填。 输入 Windows 应用的应用程序用户模型 ID (AUMID)。 若要获取此 ID，请参阅[查找已安装应用的应用程序用户模型 ID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)。
    - 磁贴大小：必填。 选择“小”、“中”、“宽”或“大”的应用磁贴大小。

- 展台浏览器设置：在 Windows Holographic for Business 上不支持。

- 使用替代“开始”布局：选择“是”输入一个 XML 文件，用于描述应用在开始菜单上的显示方式，包括应用的顺序。 如果在开始菜单中需要更多自定义，请使用此选项。 [自定义和导出开始布局](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)提供了一些指导，并包含适用于 Windows Holographic for Business 设备的特定 XML 文件。

- Windows 任务栏：在 Windows Holographic for Business 上不支持。



## <a name="next-steps"></a>后续步骤
[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
