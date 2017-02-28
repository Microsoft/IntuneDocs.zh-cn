---
title: "使用 Intune 配置 Windows 10 版本升级 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何使用 Intune 升级你管理的 Windows 10 设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 49da713cfe61ce21501e0a8e0f6e0c225b2bc291
ms.lasthandoff: 02/16/2017


---

# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Windows 10 版本升级

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用本主题中的信息了解如何配置 Windows 10 版本升级配置文件。 此配置文件可以将运行以下任一 Windows 10 版本的设备自动升级至较新的版本：

- Windows 10 桌面版
- Windows 10 全息版
- Windows 10 移动版

支持下列升级路径：

- 从 Windows 10 专业版到 Windows 10 企业版
- 从 Windows 10 家庭版到 Windows 10 教育版
- 从 Windows 10 移动版到 Windows 10 移动企业版
- Windows 10 全息专业版到Windows 10 全息企业版

## <a name="before-you-start"></a>开始之前
在开始将设备升级至最新版本之前，你将需要以下内容之一：

- 在该策略针对的所有设备上安装 Windows 新版本使用的有效产品密钥（针对于 Windows 10 桌面版）。 你可以使用多激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥。 或者包含在遵循策略的所有设备上安装 Windows 新版本许可信息的 Microsoft 许可证文件（用于 Windows 10 移动版和 Windows 10 全息版）。
- 作为目标的 Windows 10 设备必须在 Microsoft Intune 中进行注册。 无法将版本升级策略用于运行 Intune 电脑客户端软件的电脑。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入版本升级配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 从“配置文件类型”下拉列表中，选择“版本升级”。
7. 在“版本升级”边栏选项卡上，配置以下各项：
    - **要升级的版本** - 从下拉列表中选择想要在设备上升级的 Windows 10 版本。
    - **将升级到的版本** - 从下拉列表中，选择你想将目标设备升级到的版本：Windows 10 桌面版、Windows 10 全息版或 Windows 10 移动版。
    - **产品密钥** - 指定从 Microsoft 获取并且可以用于升级所有目标 Windows 10 桌面版设备的产品密钥。<br>在创建包含产品密钥的策略后，将无法对产品密钥进行编辑。 这是因为出于安全考虑，密钥将被遮盖。 若要更改产品密钥，必须重新输入完整的密钥。
    - **许可证文件** - 选择“浏览”以选择从 Microsoft 获取的许可证文件，该文件包含要将目标设备升级到的 Windows 全息版或 Windows 10 移动版的许可证信息。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。


