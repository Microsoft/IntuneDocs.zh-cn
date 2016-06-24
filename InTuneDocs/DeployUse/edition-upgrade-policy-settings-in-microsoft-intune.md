---
# required metadata

title: Windows 版本升级策略设置 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 Windows 版本升级策略设置
Microsoft Intune“版本升级策略”可以将运行以下任一 Windows 10 版本的设备自动升级至较新的版本：
* Windows 10 桌面版
* Windows 10 全息版

## 开始之前
在开始将设备升级至最新版本之前，你将需要以下内容之一：
* 在该策略针对的所有设备上安装 Windows 新版本使用的有效产品密钥（针对于 Windows 10 桌面版）。
* 在该策略针对的所有设备上安装 Windows 新版本使用的包含许可信息的 Microsoft 许可证文件（针对于 Windows 10 移动版和 Windows 10 全息版）。
* 作为目标的 Windows 10 设备必须在 Microsoft Intune 中进行注册。

## 版本升级策略设置

|设置名|详细信息|
|-|-|
|**Name**|输入版本升级策略的名称。|
|**说明**|（可选）输入有助于在 Intune 控制台中识别该策略的描述。
|**要升级到的版本**|从下拉列表中，选择你想将目标设备升级到的版本：Windows 10 桌面版、Windows 10 全息版或 Windows 10 移动版。
|**产品密钥**|指定从 Microsoft 获取并且可以用于升级所有目标 Windows 10 桌面版设备的产品密钥。<br>在创建包含产品密钥的策略后，将无法对产品密钥进行编辑。 这是因为出于安全考虑，密钥将被遮盖。 若要更改产品密钥，必须重新输入完整的密钥。
|**许可证文件**|单击**浏览**以选择从 Microsoft 获取的许可证文件，该文件包含要将目标设备升级到的 Windows 全息版或 Windows 10 移动版的许可证信息。

### 另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

<!--HONumber=May16_HO3-->


