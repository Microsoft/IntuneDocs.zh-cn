---
title: 使用 Microsoft Intune 自定义 iOS 设备上的锁屏 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解使用 iOS 的共享设备配置设置可在 iOS 设备锁屏上用于显示信息的 Microsoft Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203070"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>使用 Microsoft Intune 在 iOS 设备上向锁屏和登录窗口添加自定义消息

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍了可用于在 iOS 设备锁屏和登录窗口上显示信息的 Microsoft Intune 设置。 

使用这些设置在登录窗口和锁屏上显示自定义消息或文本。 例如，可输入“如果丢失，请送还至…”消息和资产标记信息。

这些设置支持运行 iOS 9.3 及更高版本的已监督设备。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入配置文件的“名称”和“描述”。
4. 在“平台”中，请选择“iOS”。 在“配置文件类型”中，请选择“设备功能”。
5. 在“设置”中，请选择“锁屏信息(仅受监督模式)”。 配置下列设置：

    - **资产标记信息：** 输入有关该设备资产标记的信息。 例如，输入 `123xyz`。

        输入的文本显示在设备的登录窗口和锁屏上。

    - **锁屏脚注：** 输入一个可帮助在设备丢失或被盗时将其找回的注释。 可以在字段中输入任何文本。 例如，输入类似于 `If found, call Contoso at ...` 的内容。

    设备令牌还可以用于向这些字段添加特定于设备的信息。 例如，若要显示序列号，请输入 `Serial Number: {{serialnumber}}`。 在锁屏上，文本显示类似于 `Serial Number 123456789ABC`。 输入变量时，请务必使用大括号 `{{ }}`。 [应用配置令牌](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可用变量的列表。 还可以使用 `deviceName` 或任何其他特定于设备的值。

6. 完成时，请依次选择“确定” > “确定” > “创建”。 配置文件显示在列表中。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
