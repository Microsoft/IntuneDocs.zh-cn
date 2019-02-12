---
title: Microsoft Intune 中适用于 Windows Holographic for Business 的展台设置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 将 Windows Holographic for Business 设备配置为单应用和多应用展台、自定义开始菜单、添加应用、显示任务栏，以及配置 Web 浏览器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28ecba61514c9143c21cb77e724fdcddbef42a37
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845255"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>使用 Intune 将 Windows Holographic for Business 设备作为展台运行的设置

在 Windows Holographic for Business 设备上，可将这些设备配置为以单应用展台模式或多应用展台模式运行。 在 Windows Holographic for Business 上不支持某些功能。

本文列出并介绍了可以在 Windows Holographic for Business 设备上控制的各种设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置将 Windows Holographic for Business 设备配置为在展台模式下运行。

作为 Intune 管理员，可以创建这些设置，并将它们分配到设备。

若要详细了解 Intune 中的 Windows 展台功能，请参阅[配置展台设置](kiosk-settings.md)。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](kiosk-settings.md#create-the-profile)。

## <a name="single-full-screen-app-kiosks"></a>单个全屏应用展台

当选择单应用展台模式时，请输入以下设置：

- **用户登录类型**：选择“本地用户帐户”，输入与展台应用相关联的本地（对设备而言）用户帐户或 Microsoft Account (MSA) 帐户。 Windows Holographic for Business 不支持“自动登录”用户帐户类型。

- **应用程序类型**：选择“存储应用”。

- **要在展台模式下运行的应用**：选择“添加应用商店应用”，并从列表中选择应用。

    未列出任何应用？ 使用[客户端应用](apps-add.md)中的步骤添加一些应用。

    选择“确定”，保存所做更改。

## <a name="multi-app-kiosks"></a>多应用展台

在此模式下，可从开始菜单使用应用。 其中仅包含用户可以打开的应用。 当选择多应用展台模式时，请输入以下设置：

- **在 S 模式设备中定位 Windows 10**：选择“否”。 Windows Holographic for Business 上不支持 S 模式。

- **用户登录类型**：添加一个或多个可以使用所添加的应用的用户帐户。 选项包括： 

  - **自动登录**：在 Windows Holographic for Business 上不支持。
  - **本地用户帐户**：“添加”本地（对设备而言）用户帐户。 输入的帐户用于登录到展台。
  - **Azure AD 用户或组（Windows 10 版本 1803 及更高版本）**：需要用户凭据才能登录到设备。 选择“添加”以从列表中选择 Azure AD 用户或组。 你可以选择多个用户和组。 选取“选择”，保存所做的更改。
  - **HoloLens 访问者**：访问者帐户是来宾帐户，不需要任何用户凭据或身份验证，如[共享电脑模式概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)中所述。

- **应用程序**：添加要在展台设备上运行的应用。 请记住，可以添加多个应用。

  - **添加应用商店应用**：选择使用[客户端应用](apps-add.md)添加的现有应用。 如果未列出任何应用，则可以获取应用，并[将其添加到 Intune](store-apps-windows.md)。
  - **添加 Win32 应用**：在 Windows Holographic for Business 上不支持。
  - **按 AUMID 添加**：使用此选项可添加收件箱 Windows 应用。 输入以下属性： 

    - **应用程序名称**：必须的。 输入应用程序的名称。
    - **应用程序用户模型 ID (AUMID)**：必须的。 输入 Windows 应用的应用程序用户模型 ID (AUMID)。 若要获取此 ID，请参阅[查找已安装应用的应用程序用户模型 ID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)。
    - **磁贴大小**：必须的。 选择“小”、“中”、“宽”或“大”的应用磁贴大小。

- **展台浏览器设置**：在 Windows Holographic for Business 上不支持。

- **使用可选“开始”屏幕布局**：选择“是”，输入一个 XML 文件，用于描述应用在“开始”菜单上的显示方式，包括应用的顺序。 如果在开始菜单中需要更多自定义，请使用此选项。 [自定义和导出开始布局](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)提供了一些指导，并包含适用于 Windows Holographic for Business 设备的特定 XML 文件。

- **Windows 任务栏**：在 Windows Holographic for Business 上不支持。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) 和 [Windows 10 及更高版本](kiosk-settings-windows.md)设备创建展台配置文件。
