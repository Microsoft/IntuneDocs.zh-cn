---
title: "Windows 版本升级策略设置 | Microsoft Docs"
description: "了解如何使用 Intune 将 Windows 10 设备自动升级至其他版本。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 66be6716df38d868e8247131b49ffb50fc48e60b
ms.openlocfilehash: 81061f032ef2079695f45e54e99cbb6479252bed
ms.contentlocale: zh-cn
ms.lasthandoff: 04/15/2017


---

# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 版本升级策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune“版本升级策略”可以将运行以下任一 Windows 10 版本的设备自动升级至其他版本：
* Windows 10 桌面版
* Windows 10 全息版
* Windows 10 移动版

支持下列升级路径：
- 从 Windows 10 专业版到 Windows 10 企业版
- 从 Windows 10 家庭版到 Windows 10 教育版
- 从 Windows 10 移动版到 Windows 10 移动企业版
- Windows 10 全息专业版到Windows 10 全息企业版

## <a name="before-you-start"></a>开始之前
在开始将设备升级至最新版本之前，你将需要以下内容之一：
* 在该策略针对的所有设备上安装 Windows 新版本使用的有效产品密钥（针对于 Windows 10 桌面版）。 你可以使用多激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥。
**或者**包含在遵循策略的所有设备上安装 Windows 新版本许可信息的 Microsoft 许可文件（用于 Windows 10 移动版和 Windows 10 全息版）。
* 作为目标的 Windows 10 设备必须在 Microsoft Intune 中进行注册。 无法将版本升级策略用于运行 Intune 电脑客户端软件的电脑。

## <a name="edition-upgrade-policy-settings"></a>版本升级策略设置

|设置名|详细信息|
|-|-|
|**Name**|输入版本升级策略的名称。|
|**描述**|（可选）输入有助于在 Intune 控制台中识别该策略的描述。
|**要升级到的版本**|从下拉列表中，选择你想将目标设备升级到的版本：Windows 10 桌面版、Windows 10 全息版或 Windows 10 移动版。
|**产品密钥**|指定从 Microsoft 获取并且可以用于升级所有目标 Windows 10 桌面版设备的产品密钥。<br>在创建包含产品密钥的策略后，将无法对产品密钥进行编辑。 这是因为出于安全考虑，密钥将被遮盖。 若要更改产品密钥，必须重新输入完整的密钥。
|**许可证文件**|选择“**浏览**”以选择从 Microsoft 获取的许可证文件，该文件包含要将目标设备升级到的 Windows 全息版或 Windows 10 移动版的许可证信息。

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

