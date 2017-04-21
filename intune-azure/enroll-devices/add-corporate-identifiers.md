---
title: "将 IMEI 标识符添加到 Intune"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何将企业标识符（IMEI 号码）添加到 Microsoft Intune。 "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 15415f9f31d520d66257df3a7e134e4b1de8467c
ms.openlocfilehash: 8c9e6b39ee01697d993e5738ec35e8a64fc8e236
ms.lasthandoff: 04/07/2017

---

# <a name="add-corporate-identifiers"></a>添加企业标识符

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

作为一名 IT 管理员，你可以创建和导入用逗号分隔的值 (.csv) 文件，该文件列出了国际移动设备识别 (IMEI) 编号来识别公司所有的设备。 每个 IMEI 编号可以在列表中指定详细信息，以便用于管理。

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>添加企业标识符
若要创建列表，请创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加 IMEI 标识符，在右列添加详细信息。 详细信息限制为 128 个字符，且仅用于管理。 在设备上不显示详细信息。 当前限制为每个 .csv 文件 500 行。

**上传含序列号的 .csv 文件** - 创建两列不带标头的逗号分隔值 (.csv) 列表，并将列表限制为每个 .csv 文件 5,000 台设备或 5 MB。

|||
|-|-|
|&lt;IMEI #1&gt;|&lt;Device #1 Details&gt;|
|&lt;IMEI #2&gt;|&lt;Device #2 Details&gt;|

在文本编辑器中查看该 .csv 文件时，该文件显示为：

```
01 234567 890123,device details
02 234567 890123,device details
```


> [!IMPORTANT]
> 某些 Android 设备具有多个 IMEI 号码。 Intune 为每台设备列出一个 IMEI 号码。 如果导入一个 IMEI 号码，但它与 Intune 列出的 IMEI 不符，就会将设备归类为个人设备，而非公司拥有的设备。 如果为设备导入多个 IMEI 号码，未列出号码的注册状态将显示为“未知”。

**添加企业标识符 .csv 列表**

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，依次选择“设备注册” > “注册限制”、“公司设备标识符”，然后单击“添加”。

3. 在“添加标识符”边栏选项卡中，指定标识符类型 **IMEI**。 你可以指定先前导入的号码是否应“覆盖现有标识符的详细信息”。  

4. 单击文件夹图标并指定要导入的列表的路径。 导航到 IMEI CSV 文件，然后选择“添加”。

导出后，这些设备可能已/未注册，其状态可能为“已注册”或“未连接”。 “未连接”表示该设备没有与 Intune 服务通信。

## <a name="delete--corporate-identifiers"></a>删除企业标识符

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，依次选择“设备注册” > “注册限制”、“公司设备标识符”，然后选择“删除”。

3. 在“删除标识符”边栏选项卡中，浏览到要删除的设备 ID 的 .csv 文件，然后单击“删除”。

## <a name="imei-specifications"></a>IMEI 规格
有关国际移动设备识别号的详细规范，请参阅 [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。

