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
ms.sourcegitcommit: 4ebd74c77145464574a1fed878ec4dbc2eb3c271
ms.openlocfilehash: 7bb8168c442a3340e8c185f1908acd9be15cab05
ms.lasthandoff: 04/05/2017

---

# <a name="add-corporate-identifiers"></a>添加企业标识符

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

作为一名 IT 管理员，你可以创建和导入用逗号分隔的值 (.csv) 文件，该文件列出了国际移动设备识别 (IMEI) 编号来识别公司所有的设备。 每个 IMEI 编号可以在列表中指定详细信息，以便用于管理。

为公司拥有的 iOS 设备上载序列号时，它们必须与公司注册配置文件成对使用。 然后，必须使用 Apple 的设备注册程序 (DEP) 或 Apple 配置器注册这些设备，以使其显示为公司所有。 

## <a name="create-a-csv-file"></a>创建 .csv 文件
若要创建列表，请创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加 IMEI 标识符，在右列添加详细信息。 详细信息最多允许 128 个字符。 当前限制为每个 .csv 文件 500 行。

**上传含序列号的 .csv 文件** - 创建两列不带标头的逗号分隔值 (.csv) 列表，并将列表限制为每个 .csv 文件 5,000 台设备或 5 MB。

|||
|-|-|
|&lt;IMEI #1&gt;|&lt;Device #1 Details&gt;|
|&lt;IMEI #2&gt;|&lt;Device #2 Details&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**添加企业标识符 .csv 列表**

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“企业设备标识符”。

3. 若要导入包含新详细信息（将覆盖现有信息）的文件，请选择“覆盖现有标识符详细信息”以将现有详细信息替换为新的详细信息。

4. 导航到 IMEI CSV 文件，然后选择“添加”。

> [!IMPORTANT]
> 某些 Android 设备具有多个 IMEI 号码。 Intune 为每台设备列出一个 IMEI 号码。 如果导入一个 IMEI 号码，但它与 Intune 列出的 IMEI 不符，就会将设备归类为个人设备，而非公司拥有的设备。 如果为设备导入多个 IMEI 号码，未列出号码的注册状态将显示为“未知”。

导出后，这些设备可能已/未注册，其状态可能为“已注册”或“未连接”。 “未连接”表示该设备没有与 Intune 服务通信。

## <a name="delete-a-csv-list"></a>删除 .csv 列表

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“企业设备标识符”。

3. 选择“删除”。

有关国际移动设备识别号的详细规范，请参阅 [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。

