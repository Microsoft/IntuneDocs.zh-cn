---
title: "使用 Intune 配置 Windows 10 版本升级"
titlesuffix: Azure portal
description: "了解如何使用 Intune 将所管 Windows 10 设备升级到其他版本。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8581aea9db4c04efda5fe9f3281be95330bcd2e2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Windows 10 版本升级
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本文将介绍如何配置 Windows 10 版本升级配置文件。 使用此配置文件，可以将运行 Windows 10 版本的设备自动升级到其他版本。 

## <a name="before-you-start"></a>开始之前
开始将设备升级至最新版本之前，需要以下内容之一：

- 在该策略针对的所有设备上安装 Windows 新版本使用的有效产品密钥（针对于 Windows 10 桌面版）。 可以使用多次激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥，或者使用包含在遵循策略的所有设备上安装新版 Windows 所需的许可信息的 Microsoft 许可证文件（用于 Windows 10 移动版和 Windows 10 全息版）。
- 为其分配策略的 Windows 10 设备必须在 Microsoft Intune 中进行注册。 无法将版本升级策略用于运行 Intune 电脑客户端软件的电脑。

## <a name="supported-upgrade-paths-for-the-windows-10-edition-upgrade-profile"></a>Windows 10 版本升级配置文件支持的升级路径
下面列出了 Windows 10 版本升级配置文件支持的升级路径。 要升级到的 Windows 10 版本以粗体显示，后面列出了可以从哪些受支持的版本升级到此版本：

**Windows 10 教育版**
- Windows 10 专业版
- Windows 10 专业教育版
- Windows 10 云端版
- Windows 10 企业版
- Windows 10 核心版
    
**Windows 10 教育版 N**    
- Windows 10 专业版 N
- Windows 10 专业教育版 N
- Windows 10 云端版 N
- Windows 10 企业版 N
- Windows 10 核心板 N
    
**Windows 10 企业版**
- Windows 10 专业版
- Windows 10 云端版
- Windows 10 核心版
    
**Windows 10 企业版 N**
- Windows 10 专业版 N
- Windows 10 云端版 N
- Windows 10 核心板 N
    
**Windows 10 专业版**
- Windows 10 云端版
    
**Windows 10 专业版 N**
- Windows 10 云端版 N
    
**Windows 10 专业教育版**
- Windows 10 专业版
- Windows 10 云端版
- Windows 10 核心版
    
**Windows 10 专业教育版 N**
- Windows 10 专业版 N
- Windows 10 云端版 N
- Windows 10 核心板 N

**Windows 10 Holographic for Business**
- Windows 10 全息版

**Windows 10 移动企业版**
- Windows 10 移动版

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件
1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入版本升级配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 从“配置文件类型”下拉列表中，选择“版本升级”。
7. 在“版本升级”边栏选项卡上，配置以下设置：
    - **将升级到的版本** - 从下拉列表中，选择你想将目标设备升级到的版本：Windows 10 桌面版、Windows 10 全息版或 Windows 10 移动版。
    - **产品密钥** - 指定从 Microsoft 获取并且可以用于升级所有目标 Windows 10 桌面版设备的产品密钥。<br>在创建包含产品密钥的策略后，将无法对产品密钥进行编辑。 这是因为出于安全考虑，密钥将被遮盖。 若要更改产品密钥，必须重新输入完整的密钥。
    - **许可证文件** - 选择“浏览”，选择从 Microsoft 获取的许可证文件，其中包含要将目标设备升级到的 Windows Holographic 或 Windows 10 移动版的许可证信息。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

系统将创建配置文件并在“配置文件列表”边栏选项卡上显示出来。

## <a name="next-steps"></a>后续步骤

如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

>[!NOTE]
>如果稍后删除分配的策略，设备上的 Windows 版本将不会还原，并继续正常运行。

