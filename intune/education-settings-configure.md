---
title: "配置适用于 Windows 10 的 Intune 教育设置"
titleSuffix: Azure portal
description: "了解如何使用 Intune 配置所管设备上 Windows 10 的教育设置。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 12e36761320557f6af9554d3b671fc133253c13c
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Windows 10 教育设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可以使用教育配置文件指定配置 Windows Take a Test 应用的详细信息，其中包括帐户详细信息和测试 URL。 对此进行配置时，Take a Test 应用随指定的测试打开，直到测试完成才可以在设备上运行其他应用程序。

有关 Take a Test 应用的详细信息，请参阅[在 Windows 10 中参加测验](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)。

## <a name="create-a-device-profile-containing-education-profile-settings"></a>创建包含教育配置文件设置的设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备限制配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 在“配置文件类型”类型下拉列表中，选择“教育配置文件”。 
7. 选择“设置”>“配置”，然后，在“Take a Test”边栏选项卡上配置以下各项：
    - **帐户用户名** - 输入用于 Take a Test 的帐户用户名。 可以是域帐户、Azure Active Directory (AAD) 帐户或本地计算机帐户。
    - **评估 URL** -提供你想让用户执行的测试的 URL。 有关详细信息，请参阅 Take a Test 文档。
    - **屏幕监控** - 指定用户在执行测试时，你是否能够监视屏幕活动。
    - **文本建议** - 在用户执行测试时允许或阻止文本建议。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

此时，配置文件会进行创建，并显示在配置文件列表边栏选项卡上。

## <a name="next-steps"></a>后续步骤

如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。



