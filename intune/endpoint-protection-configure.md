---
title: 在 Microsoft Intune 中配置终结点保护设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建 macOS 或 Windows 10 设备配置文件时，创建终结点保护设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 033021010698d46f7ecb33546164ee16ad7192c0
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182918"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>在 Intune 中添加终结点保护设置

终结点保护可用于控制设备上的各种安全功能，包括防火墙、bitlocker、允许和阻止应用、Windows Defender 和加密等。 可在 Microsoft Intune 中使用设备配置文件配置这些设置。

例如，可以创建一个终结点保护配置文件，仅允许 macOS 用户安装来自 Mac App Store 的应用。 或者在 Windows 10 设备上运行应用时启用 Windows SmartScreen。

本文介绍如何创建配置文件。 然后选择设备平台，获取有关可用设置的详细信息。

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>创建包含终结点保护设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入终结点保护配置文件的“名称”和“描述”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：
   - **macOS**
   - **Windows 10 及更高版本**
6. 在“配置文件类型”下拉列表中，选择“Endpoint Protection”。 
7. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下主题之一：
   - [macOS 设置](endpoint-protection-macos.md)
   - [Windows 10 设置](endpoint-protection-windows-10.md)
8. 完成后，返回“创建配置文件”页，然后单击“创建”。

配置文件随即创建并显示在“配置文件列表”页中。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。

## <a name="next-steps"></a>后续步骤
要向组分配配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。
