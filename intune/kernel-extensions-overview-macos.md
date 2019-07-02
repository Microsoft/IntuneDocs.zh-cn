---
title: 使用 Microsoft Intune-Azure 中创建 macOS 内核扩展设备配置文件 |Microsoft Docs
titleSuffix: ''
description: 添加或创建 macOS 设备配置文件，以及如何配置内核扩展，若要允许用户重写时，请在 Microsoft Intune 中添加团队标识符和捆绑包和团队标识符。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403901"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>在 Intune 中添加 macOS 内核扩展

在 macOS 设备上可以在内核级别添加功能。 这些功能访问的普通程序无法访问 OS 的部分。 你的组织可能具有的具体需求或要求在应用程序、 设备功能等中不可用。 

若要添加始终允许在设备上加载的内核扩展，添加"内核 extensions"(KEXT) 在 Microsoft Intune 中，然后将这些扩展部署到你的设备。

例如，您有病毒扫描程序扫描设备的恶意内容。 您可以添加此病毒扫描程序的内核扩展为允许的内核扩展在 Intune 中。 然后，""将扩展分配给 macOS 设备。

使用此功能，管理员可以允许用户重写内核扩展，添加团队标识符，并在 Intune 中添加特定的内核扩展。

此功能适用于：

- macOS 10.13.2 及更高版本

若要使用此功能，设备必须：

- 使用 Apple 的设备注册计划 (DEP) 在 Intune 中注册。 [自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)提供了更多信息。

  要么

- 在 Intune 中注册进行"批准的用户注册"（Apple 的词）。 [准备向 macOS High Sierra 中的内核扩展更改](https://support.apple.com/en-us/HT208019)（打开 Apple 的网站） 提供了更多信息。

Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，就可以将配置文件推送或部署到组织的 macOS 设备上。

本文介绍如何创建设备配置文件在 Intune 中使用内核扩展。

> [!TIP]
> 有关内核扩展的详细信息，请参阅[内核扩展概述](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)（打开 Apple 的网站）。

## <a name="what-you-need-to-know"></a>须知内容

- 无符号的旧版内核扩展可添加。
- 请确保输入正确的团队标识符和捆绑 ID 的内核扩展。 Intune 不会验证输入的值。 如果输入了错误的信息，无法在设备上运行该扩展。

> [!NOTE]
> 有关签名和所有软件的公证 Apple 发布信息。 在 macOS 10.14.5 和更高版本，内核通过 Intune 部署的扩展插件不需要符合 Apple 的公证策略。
>
> 在此公证策略，以及任何更新或更改的信息，请参阅以下资源：
>
>  - [Notarizing 分发之前应用](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)（打开 Apple 的网站） 
>  - [准备向 macOS High Sierra 中的内核扩展更改](https://support.apple.com/en-us/HT208019)（打开 Apple 的网站）

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“macOS”
    - **配置文件类型**： 选择**扩展**。
    - **设置**：输入要配置的设置。 有关所有设置及其用途的列表，请参阅：

        - [macOS](kernel-extensions-settings-macos.md)

4. 完成后，选择“确定” > “创建”以保存所做的更改。

此时，配置文件创建完成，并出现在列表中。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
