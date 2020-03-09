---
title: 使用 Microsoft Intune 创建 macOS 内核扩展配置文件 - Azure | Microsoft Docs
titleSuffix: ''
description: 添加或创建 macOS 设备配置文件，然后配置内核扩展，使其允许用户替代和添加团队标识符以及 Microsoft Intune 中的捆绑包和团队标识符。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/25/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8a516ce9dda525d5c7a48fcbc2c799471489d0d
ms.sourcegitcommit: ff254acb94df88afc3e3e7b878084052adf40745
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600249"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>使用 Intune 添加 macOS 内核扩展

> [!NOTE]
> macOS 内核扩展正在替换为系统扩展。 有关详细信息，请参阅[支持提示：在 Intune 中为 macOS Catalina 10.15 使用系统扩展而不是内核扩展](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-using-system-extensions-instead-of-kernel-extensions/ba-p/1191413)。

在 macOS 设备上，可添加内核级功能。 这些功能可访问正常程序无法访问的 OS 部分。 组织可能具有应用、设备功能等无法满足的特定需求或要求。 

要添加始终允许在设备上加载的内核扩展，请使用 Microsoft Intune 添加“内核扩展”(KEXT)，然后将这些扩展部署到设备。

例如，你有一个病毒扫描程序，可扫描设备中是否存在恶意内容。 你可使用 Intune 将此病毒扫描程序的内核扩展添加为允许的内核扩展。 然后，向 macOS 设备分配该扩展。

利用此功能，管理员可以允许用户替代内核扩展，添加团队标识符，以及使用 Intune 添加特定内核扩展。

此功能适用于：

- macOS 10.13.2 及更高版本

要使用此功能，设备必须符合以下情况：

- 使用 Apple 设备注册计划 (DEP) 通过 Intune 进行注册。 如需了解详细信息，请参阅[自动注册 macOS 设备](../enrollment/device-enrollment-program-enroll-macos.md)。

  要么

- 使用 Intune 通过“已批准的用户注册”（Apple 的术语）进行注册 如需了解详细信息，请参阅[为 macOS High Sierra 中内核扩展的更改做好准备](https://support.apple.com/en-us/HT208019)（打开 Apple 网站）。

Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，就可以将配置文件推送或部署到组织的 macOS 设备上。

本文介绍如何通过 Intune 使用内核扩展创建设备配置文件。

> [!TIP]
> 有关内核扩展的详细信息，请参阅[内核扩展概述](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)（打开 Apple 网站）。

## <a name="what-you-need-to-know"></a>须知内容

- 可以添加未签名的旧版内核扩展。
- 请确保输入正确的团队标识符和内核扩展的捆绑包 ID。 Intune 不会验证输入的值。 如果输入的信息不正确，则该扩展将无法在设备上运行。 团队标识符长度正好为 10 个字母数字字符。 

> [!NOTE]
> Apple 发布了有关所有软件的签名和公证的信息。 在 macOS 10.14.5 和更新版本中，通过 Intune 部署的内核扩展不必满足 Apple 的公证策略。
>
> 有关此公证策略以及任何更新或更改的信息，请参阅以下资源：
>
> - [分发前对应用进行公证](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)（打开 Apple 网站） 
> - [为 macOS High Sierra 中内核扩展的更改做好准备](https://support.apple.com/en-us/HT208019)（打开 Apple 网站）

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“macOS” 
    - **配置文件类型**：选择“扩展”  。
    - **设置**：输入要配置的设置。 有关所有设置及其用途的列表，请参阅：

        - [macOS](kernel-extensions-settings-macos.md)

4. 完成后，选择“确定”   > “创建”  以保存所做的更改。

此时，配置文件创建完成，并出现在列表中。 请务必[分配配置文件](../device-profile-assign.md)，并[监视配置文件状态](../device-profile-monitor.md)。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](../device-profile-assign.md)并[监视其状态](../device-profile-monitor.md)。
