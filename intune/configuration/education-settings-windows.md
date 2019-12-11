---
title: Microsoft Intune 中的 Windows 10 教育设置 - Azure | Microsoft Docs
description: 查看所有适用于 Windows 10 设备的教育设置的列表。 在设备配置文件中结合使用这些设置和“参加测验”应用，在 Intune 中选择用户或学生登录方式、在测验期间监视屏幕等。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d89f512c06dcfbf6f6ddaba5e17ac9ca6f0becf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506810"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>使用 Intune 在 Windows 10 设备上配置“参加测验”应用

使用 "执行测试" 应用可以在教室的 Windows 10 设备上安全管理联机测试。 若要设置 Take a Test 应用，需要在 Intune 中创建设备配置文件，并配置安全评估设置。 本文介绍了 "执行测试" 应用所需的设置。 

配置了配置文件后，请将其分配给学生，并将其部署到你的学生。 

[Intune 中的“参加测验”应用](education-settings-configure.md)提供了此功能的详细信息。

## <a name="before-you-begin"></a>开始之前

[创建设备配置文件](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>“参加测验”设置
创建设备配置文件后，请参阅 "**配置文件类型**"，并选择 "**安全评估（教育）** "。 你将看到以下 "采用测试应用程序" 设置。 


- **帐户类型**：选择用户登录测验的方式。 选项包括：
  - Azure AD 帐户
  - 域帐户
  - 本地帐户
  - 本地来宾帐户：仅在运行 Windows 10 版本1903及更高版本的设备上可用。    
- **帐户用户名**：输入用于参加测验的帐户用户名。 可以按如下格式输入帐户：
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **帐户名称**：若要设置本地来宾帐户类型，请输入用于 "执行测试" 应用的帐户的名称。 帐户名称将在登录屏幕上显示为磁贴。 学生单击磁贴以启动测试。  
- **评估 URL**：输入你想让用户执行测试的 URL。 若要详细了解如何获取 URL，请参阅[“参加测验”文档](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)。
- **打印机连接**：选择 "仅**需要**允许访问" "从连接到打印机的设备获取测试应用"。 此设置还使应用的 "打印" 按钮可用于参与者。 "**未配置**" 允许学生从不连接到打印机的设备访问应用。  
- **屏幕监视**：选择“允许”可在用户参加测验时监视屏幕活动  。 如果选择“未配置”  ，便无法在测验期间监视屏幕。
- **文本建议**：选择“允许”可向测验者显示文本建议  。 如果选择“未配置”  ，便无法向正在参加测验的用户显示文本建议。

## <a name="next-steps"></a>后续步骤

请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。
