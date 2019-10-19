---
title: 在 Microsoft Intune 中向 iOS 设备添加自定义设置 - Azure | Microsoft Docs
titleSuffix: ''
description: 从 Apple Configurator 或 Apple 配置文件管理器工具导出 iOS 设置，然后将这些设置导入 Microsoft Intune。 这些设置可以创建、使用和控制 iOS 设备上的自定义设置和功能。 之后，可以将此自定义配置文件分配或分发到组织中的 iOS 设备，以创建基线或标准。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfe795a812572fa92c51a23b9e15b7fe48254174
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495766"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用适用于 iOS 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 iOS 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

使用 iOS 设备时，可以通过两种方法将自定义设置引入 Intune：

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple 配置文件管理器](https://support.apple.com/profile-manager)

这些工具可用于将设置导出到配置文件。 在 Intune 中，导入此文件，然后将该配置文件分配给 iOS 用户和设备。 分配后，就会分配设置。 它们还为组织中的 iOS 创建基准或标准。

本文提供了有关使用 Apple 配置器和 Apple 配置文件管理器的一些指导，并介绍了可配置的属性。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](device-profile-create.md)。

## <a name="what-you-need-to-know"></a>须知内容

- 使用 Apple 配置器创建配置文件时，请确保导出的设置与设备上的 iOS 版本兼容  。 有关如何解决不兼容设置的信息，请在 [Apple 开发人员](https://developer.apple.com/)网站上搜索“配置文件参考”和“移动设备管理协议参考”   。

- 使用 Apple 配置文件管理器时，请务必  ：

  - 在配置文件管理器中启用[移动设备管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)。
  - 在配置文件管理器中添加 [iOS 设备](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)。
  - 在配置文件管理器中添加设备后，转到“在库之下” > “设备”>“选择设备”>“设置”    。 输入设备的常规设置。

    下载并保存此文件。 需在 Intune 配置文件中输入此文件。

  - 请确保从 Apple 配置文件管理器导出的设置与设备上的 iOS 版本兼容。 有关如何解决不兼容设置的信息，请在 [Apple 开发人员](https://developer.apple.com/)网站上搜索“配置文件参考”和“移动设备管理协议参考”   。

## <a name="custom-configuration-profile-settings"></a>自定义配置文件设置

- **自定义配置文件名称**：输入策略的名称。 此名称将在设备上和 Intune 状态中显示。
- **配置文件**：浏览到使用 Apple Configurator 或 Apple 配置文件管理器创建的配置文件。 已导入的文件显示在“文件内容”区域中  。

  你还可以将设备令牌添加到自定义配置文件。 设备令牌用于添加特定于设备的信息。 例如，若要显示序列号，请输入 `{{serialnumber}}`。 在设备上，显示的文本类似于每个设备的唯一 `123456789ABC`。 输入变量时，请务必使用大括号 `{{ }}`。 [应用配置令牌](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可用变量的列表。 还可以使用 `deviceid` 或任何其他特定于设备的值。

  > [!NOTE]
  > 变量不在 UI 中进行验证，且区分大小写。 因此，可能会看到使用不正确输入保存的配置文件。 例如，如果输入 `{{DeviceID}}` 而不是 `{{deviceid}}`，则显示文本字符串而不是设备的唯一 ID。 请确保输入正确的信息。

选择“确定”   > “创建”  以保存所做的更改。 此时，配置文件创建完成，并出现在配置文件列表中。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。

请参阅如何[在 macOS 设备上创建配置文件](custom-settings-macos.md)。 
