---
title: Microsoft Intune 中的 Windows 10 教育设置 - Azure | Microsoft Docs
description: 查看所有适用于 Windows 10 设备的教育设置的列表。 在设备配置文件中结合使用这些设置和“参加测验”应用，在 Intune 中选择用户或学生登录方式、在测验期间监视屏幕等。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 206bc3276f3c175fe61852f235c722b835ad60b4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564850"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>使用 Intune 在 Windows 10 设备上配置“参加测验”应用

本文介绍了可以在运行 Windows 10 及更高版本的设备上配置的所有 Microsoft Intune 教育“参加测验”应用设置。 使用此应用，学生可以登录设备并参加测验。

将这些设置添加到设备配置文件，然后使用 Microsoft Intune 将其分配或部署到设备中。

[Intune 中的“参加测验”应用](education-settings-configure.md)提供了此功能的详细信息。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>“参加测验”设置

- **帐户类型**： 选择如何用户登录到测试。 选项包括：
  - Azure AD 帐户
  - 域帐户
  - 本地帐户
- **帐户用户名**：输入用于参加测验的帐户用户名。 可以按如下格式输入帐户：
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **评估 URL**：输入你想让用户执行测试的 URL。 若要详细了解如何获取 URL，请参阅[“参加测验”文档](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)。
- **屏幕监视**：选择“允许”可在用户参加测验时监视屏幕活动。 如果选择“未配置”，便无法在测验期间监视屏幕。
- **测试建议**：选择“允许”可向测验者显示文本建议。 如果选择“未配置”，便无法向正在参加测验的用户显示文本建议。

## <a name="next-steps"></a>后续步骤

此时，配置文件创建完成，但它可能尚未执行任何操作。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。
