---
title: 在 Microsoft Intune 中向 macOS 设备添加首选项文件设置 - Azure | Microsoft Docs
titleSuffix: ''
description: 添加 xml 或 info.plist 文件，其中包含有关应用的重要信息。 使用首选项文件设备配置配置文件更改属性列表文件中的密钥信息，并将其分配给 macOS 设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391493"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>使用 Microsoft Intune 向 macOS 设备添加属性列表文件

使用 Microsoft Intune，可以为 macOS 设备或 macOS 设备上的应用添加属性列表文件（. info.plist）。

此功能适用于：

- 运行10.7 和更高版本的 macOS 设备

属性列表文件通常包含有关 macOS 应用程序的信息。 有关详细信息，请参阅[关于信息属性列表文件](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)（Apple 网站）和[自定义负载设置](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1)。

本文列出并描述了可添加到 macOS 设备的不同属性列表文件设置。 作为移动设备管理（MDM）解决方案的一部分，请使用这些设置添加应用程序包 ID （`com.company.application`），并添加其 info.plist 文件。

我们将这些设置添加到 Intune 中的设备配置配置文件中，然后分配或部署到 macOS 设备。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>须知内容

- 不验证这些设置。 在将配置文件分配到设备之前，请务必测试你的更改。
- 如果不确定如何输入应用密钥，请在应用中更改设置。 然后，使用[Xcode](https://developer.apple.com/xcode/)查看应用的首选项文件以查看设置的配置方式。 Apple 建议在导入文件前使用 Xcode 删除不可管理的设置。
- 只有某些应用使用托管首选项，并且可能不允许管理所有设置。
- 请确保上传的属性列表文件针对的是设备通道设置，而不是用户频道设置。 属性列表文件以整个设备为目标。

## <a name="preference-file"></a>首选项文件

- **首选项域名**：属性列表文件通常用于 web 浏览器（microsoft Edge）、 [Microsoft Defender 高级威胁防护](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)和自定义应用。 创建首选项域时，还会创建一个捆绑 ID。 输入 "捆绑 ID"，例如 "`com.company.application`"。 例如，输入 `com.Contoso.applicationName`、`com.Microsoft.Edge` 或 `com.microsoft.wdav`。
- **属性列表文件**：选择与应用关联的属性列表文件。 请确保它是 `.plist` 或 `.xml` 文件。 例如，上传 `YourApp-Manifest.plist` 或 `YourApp-Manifest.xml` 文件。
- **文件内容**：显示属性列表文件中的关键信息。 如果需要更改密钥信息，请在另一个编辑器中打开列表文件，然后在 Intune 中重新上传文件。

选择“确定”   > “创建”  以保存所做的更改。 此时，配置文件创建完成，并出现在配置文件列表中。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
