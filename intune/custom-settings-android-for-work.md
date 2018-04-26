---
title: 适用于 Android for Work 的 Intune 自定义配置文件设置
titlesuffix: Microsoft Intune
description: 了解如何创建适用于 Android for Work 设备的 Microsoft Intune 自定义配置文件设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d7d1512514465b618435b8e699c581534384d2c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="create-intune-custom-profile-settings-for-android-for-work-devices"></a>创建适用于 Android for Work 设备的 Intune 自定义配置文件设置

使用 Intune 的 Android for Work 自定义配置策略来分配可用于控制 Android for Work 设备功能的 OMA-URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在使你能够分配不能使用 Intune 策略配置的 Android 设置。 Intune 目前支持有限数量的 Android 自定义策略。 请参阅本主题的示例，查找可配置的策略。

## <a name="create-a-custom-profile"></a>创建自定义配置文件

1. 按照[如何配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“自定义 OMA-URI 设置”边栏选项卡上，选择“添加”可添加新设置。
3. 在“添加行”边栏选项卡上，配置以下内容：
    - **名称** - 输入 Android for Work 自定义设置的唯一名称，这有助于在 Azure 门户中识别它。
    - **说明** - 提供对 Android 自定义策略的概述以及可帮助你查找它的其他相关信息。
    - **OMA-URI** - 输入需为其提供设置的 OMA-URI。
    - **数据类型** - 选择将在其中指定此 OMA-URI 设置的数据类型。 从“字符串”、“字符串（XML 文件）”、“日期和时间”、“整数”、“浮点”**、**“布尔值”或“Base64（文件）”中进行选择。
    - **值** - 指定要与之前指定的 OMA-URI 关联的值。 根据所选的数据类型，用于提供此值的方法将有所不同。 例如，如果选择了**日期和时间**，则将从日期选取器中选择值。
4. 完成后，选择“确定”以返回“自定义 OMA-URI 设置”，然后添加更多设置，或选择“创建”以创建自定义配置文件。


## <a name="example"></a>示例

在此示例中，将创建一个自定义配置文件，可用于限制是否允许在托管的 Android for Work 设备上的工作和个人应用之间执行复制和粘贴操作。

1. 使用本主题中的过程创建使用以下值的 Android for Work 设备的自定义配置文件：
    - **名称** - 输入“阻止复制和粘贴”或你自己选择的文本。
    - **说明** - 输入“在工作和个人应用之间阻止复制/粘贴”或你自己选择的文本。
    - **OMA-URI** - 输入 **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**。
    - **数据类型** - 选择“布尔”以指示此 OMA-URI 的值为“True”或“False”。
    - **值** - 选择“True”。
2. 最后应得到类似于此图像的设置。
![阻止 Android for Work 的复制和粘贴。](./media/custom-policy-afw-copy-paste.png)
3. 现在，向你管理的 Android for Work 设备分配此自定义配置文件时，将阻止工作应用和个人配置文件之间的复制和粘贴操作。