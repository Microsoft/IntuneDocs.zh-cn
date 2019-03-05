---
title: 在 Microsoft Intune 中添加或配置教育设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中 Windows 10 及更高版本设备上的设备配置文件中使用“参加测验”应用。 使用教育设置创建配置文件，输入测验应用 URL，选择用户登录方式，在测验期间监视屏幕，以及在测验期间允许或阻止文本建议。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3c34935f161050bae51a2fbbee9b49f9fc1156f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228878"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>在 Microsoft Intune 中的 Windows 10 设备上使用“参加测验”应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 中的教育配置文件专为学生在设备上参加测验或考试而设计。 此功能包含“参加测验”应用，以及用于添加测验 URL、选择最终用户的测验登录方式等的设置。 此功能支持以下平台：

- Windows 10 及更高版本

在用户登录后，“参加测验”应用自动打开，并显示所输入的测验。 正在参加测验时，无法在设备上运行其他任何应用。 [Windows 10 中的“参加测验”](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)详细介绍了“参加测验”应用。

本文列出了在 Microsoft Intune 中创建设备配置文件的步骤。 其中还包括了解适用于 Windows 10 设备的教育设置所需的信息。

## <a name="create-a-device-profile"></a>创建设备配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”。
    - **配置文件**：选择“教育配置文件”。

4. 输入要配置的设置：

    - [Windows 10 及更高版本](education-settings-windows.md)

5. 选择“确定” > “创建”以保存所做的更改。

输入设置并创建配置文件后，配置文件将显示在配置文件列表中。 下一步，[将此配置文件分配给某些组](device-profile-assign.md)。

## <a name="next-steps"></a>后续步骤

查看 [Windows 10 教育设置](education-settings-windows.md)及其说明的列表。

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
