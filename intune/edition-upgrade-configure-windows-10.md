---
title: 使用 Microsoft Intune 升级 Windows 10 设备 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建设备配置文件以将 Windows 10 设备升级到较新版本。 另请参阅 Windows 10 专业版、N 版、教育版、云、企业版、核心版、全息版和移动版支持的升级路径。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 994ab8e7d955d18b293e4d9e9661e0c44baaaa1f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="configure-windows-10-edition-upgrade-profile-in-intune"></a>在 Intune 中配置 Windows 10 版本升级配置文件
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Intune 中配置升级配置文件以自动将运行 Windows 10 版的设备升级到其他版本。 另请参阅支持的升级路径。

## <a name="before-you-begin"></a>开始之前
将设备升级至最新版本之前，需要以下内容之一：

- 用于在该策略针对的所有设备上安装已更新 Windows 版本的有效产品密钥（适用于 Windows 10 桌面版）。 可以使用多次激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥，或者使用包含在遵循策略的所有设备上安装已更新 Windows 版本所需的许可信息的 Microsoft 许可证文件（适用于 Windows 10 移动版和 Windows 10 全息版）。
- 分配策略的 Windows 10 设备将在 Microsoft Intune 中注册。 无法将版本升级策略用于运行 Intune 电脑客户端软件的电脑。

## <a name="supported-upgrade-paths"></a>支持的升级路径
下表列出了 Windows 10 版本升级配置文件支持的升级路径。

| 从 | 升级到 |
|---|---|
| Windows 10 专业版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业教育版 |
| Windows 10 专业版 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 专业教育版 | Windows 10 教育版 | 
| Windows 10 专业教育版 N | Windows 10 教育版 N |
| Windows 10 云端版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业版 <br/>Windows 10 专业教育版 | 
| Windows 10 云端版 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 企业版 | Windows 10 教育版 | 
| Windows 10 企业版 N | Windows 10 教育版 N | 
| Windows 10 核心版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业教育版 | 
| Windows 10 核心板 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 全息版 | Windows 10 Holographic for Business |
| Windows 10 移动版 | Windows 10 移动企业版 |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备配置”、“配置文件”和“创建配置文件”。
4. 输入版本升级配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 从“配置文件类型”下拉列表中，选择“版本升级”。
7. 在“版本升级”属性中，输入以下设置：
   - **将升级到的版本** - 从下拉列表中，选择要将目标设备升级到的版本：Windows 10 桌面版、Windows 10 全息版或 Windows 10 移动版。
   - **产品密钥** - 输入从 Microsoft 接收并且可以用于升级所有目标 Windows 10 桌面版设备的产品密钥。 
    创建包含产品密钥的策略后，无法更新该密钥，并出于安全原因隐藏该密钥。 要更改产品密钥，请再次输入完整密钥。
   - “许可证文件”- 选择“浏览”以选择从 Microsoft 收到的许可证文件。 此许可证文件包含要将目标设备升级到的 Windows 全息版或 Windows 10 移动版的许可证信息。
8. 完成后，选择“创建”以保存更改。

配置文件随即创建并在配置文件中列出。

## <a name="next-steps"></a>后续步骤

要向组分配此配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。

>[!NOTE]
>如果稍后删除分配的策略，设备上的 Windows 版本将不会还原，并继续正常运行。