---
title: 在 Microsoft Intune 中配置终结点保护设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建 macOS 或 Windows 10 设备配置文件时，创建终结点保护设置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 2bebdf712ccf325c6742e6bb326a8fb2768023b7
ms.sourcegitcommit: 14f4e97de5699394684939e6f681062b5d4c1671
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "67251169"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>在 Intune 中添加终结点保护设置

使用 Intune，可以使用设备配置文件来管理设备上的公共终结点保护安全功能，包括：
- 防火墙 
- BitLocker
- 允许和阻止应用  
- Windows Defender 和加密

例如，可以创建一个终结点保护配置文件，仅允许 macOS 用户安装来自 Mac App Store 的应用。 或者在 Windows 10 设备上运行应用时启用 Windows SmartScreen。

在创建配置文件之前，请查看详细介绍 Intune 可以针对每个支持平台管理的终结点保护设置的以下文章： 
   - [macOS 设置](endpoint-protection-macos.md)
   - [Windows 10 设置](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>创建包含终结点保护设置的设备配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择“设备配置” > “配置文件” > “创建配置文件”    。
4. 输入终结点保护配置文件的“名称”和“描述”   。
5. 从“平台”  下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：
   - **macOS**
   - **Windows 10 及更高版本**
6. 在“配置文件类型”  下拉列表中，选择“Endpoint Protection”  。 
7. 根据所选择的平台，可配置的设置有所不同。 请参阅：
   - [macOS 设置](endpoint-protection-macos.md)
   - [Windows 10 设置](endpoint-protection-windows-10.md)  

8. 配置适用的设置后，选择“创建配置文件”页上的“创建”   。

   配置文件随即创建并显示在“配置文件列表”页中。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。


## <a name="next-steps"></a>后续步骤  

要向组分配配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。
