---
title: Microsoft Intune 中的 macOS 内核扩展设置-Azure |Microsoft Docs
titleSuffix: ''
description: 添加、配置或在 macOS 设备上创建设置以使用内核扩展。 此外，允许用户重写已批准的扩展，允许来自团队标识符的所有扩展，或者允许 Microsoft Intune 中的特定扩展或应用。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8632f5b8df0f483de3bb4d06a6823639ba52c604
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506694"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>在 Intune 中配置和使用内核扩展的 macOS 设备设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文列出并介绍了可以在 macOS 设备上控制的各种内核扩展设置。 作为移动设备管理（MDM）解决方案的一部分，请使用这些设置来添加和管理设备上的内核扩展。

若要详细了解 Intune 中的内核扩展和任何必备组件，请参阅[添加 macOS 内核扩展](../kernel-extensions-overview-macos.md)。

我们将这些设置添加到 Intune 中的设备配置配置文件中，然后分配或部署到 macOS 设备。

## <a name="before-you-begin"></a>开始之前

[创建设备内核扩展配置文件](../kernel-extensions-overview-macos.md)。

> [!NOTE]
> 这些设置适用于不同的注册类型。 有关不同注册类型的详细信息，请参阅[macOS 注册](../macos-enroll.md)。

## <a name="kernel-extensions"></a>内核扩展

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>设置适用于：用户已批准，自动设备注册

- **允许用户重写**：**允许**允许用户批准配置文件中未包含的内核扩展。 "**未配置**" （默认值）可防止用户允许未包含在配置文件中的扩展。 意思是，只允许配置文件中包含的扩展。

  有关此功能的详细信息，请参阅[用户批准的内核扩展加载](https://developer.apple.com/library/archive/technotes/tn2459/_index.html)（打开 Apple 的网站）。

- **允许的团队标识符**：使用此设置以允许一个或多个团队 id。 使用您输入的团队 Id 签署的任何内核扩展都允许和信任。 换句话说，使用此选项可以允许同一团队 ID 中的所有内核扩展，这可能是特定的开发人员或合作伙伴。

  **添加**要加载的有效和已签名内核扩展的团队标识符。 可以添加多个团队标识符。 团队标识符必须为字母数字（字母和数字）并且包含10个字符。 例如，输入 `ABCDE12345`。

  添加团队标识符后，还可以将其删除。

  [找到你的团队 ID](https://help.apple.com/developer-account/#/dev55c3c710c) （打开 Apple 网站）以了解详细信息。

- **允许的内核扩展**：使用此设置可允许特定内核扩展。 仅允许或信任输入的内核扩展。 

  **添加**要加载的内核扩展的捆绑标识符和团队标识符。 对于未签名的旧版内核扩展，请使用空的团队标识符。 可以添加多个内核扩展。 团队标识符必须为字母数字（字母和数字）并且包含10个字符。 例如，为 "**捆绑 ID**" 和 "**团队标识符**" `ABCDE12345` 输入 `com.contoso.appname.macos`。

  > [!TIP]
  > 若要在 macOS 设备上获取内核扩展（Kext）的捆绑 ID，可以执行以下操作：
  >
  > 1. 在终端中，运行 `kextstat | grep -v com.apple`，并记下输出。 安装所需的软件或 Kext。 再次运行 `kextstat | grep -v com.apple`，并查找更改。
  >
  >    在终端中，`kextstat` 列出操作系统上的所有内核扩展。 
  >
  > 2. 在设备上，打开 Kext 的信息属性列表文件（info.plist）。 将显示捆绑 ID。 每个 Kext 都有一个存储在中的 info.plist 文件。 

> [!NOTE]
> 无需添加团队标识符和内核扩展。 您可以配置一个或另一个。

## <a name="next-steps"></a>后续步骤

[分配配置文件](../device-profile-assign.md)并[监视其状态](../device-profile-monitor.md)。
