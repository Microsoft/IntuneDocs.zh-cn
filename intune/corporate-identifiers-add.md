---
title: "将企业标识符添加到 Intune"
titleSuffix: Intune on Azure
description: "了解如何将企业标识符（注册方法、IMEI 和序列号）添加到 Microsoft Intune。 \""
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 03a278762401ee9697909cf45b3fe86212393e66
ms.sourcegitcommit: 0b164f806165d312acfc88815a60e325e3d02672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2017
---
# <a name="add-corporate-identifiers"></a>添加企业标识符

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 管理员可以通过多种方式将设备标识为公司拥有。 Intune 可以从公司拥有的设备收集其他信息。 还可设置设备限制，防止对非公司拥有的设备进行注册。

满足以下任意条件时，设备将被标识为公司拥有的设备：

- 使用[设备注册管理员](device-enrollment-manager-enroll.md)帐户进行注册（所有平台）
- 通过 Apple [设备注册计划](device-enrollment-program-enroll-ios.md)、[Apple School Manager](apple-school-manager-set-up-ios.md) 或 [Apple 配置器](apple-configurator-enroll-ios.md)进行注册（仅限 iOS）
- 使用国际移动设备标识符 (IMEI) 号码（具有 IMEI 号码的所有平台）或序列号（iOS 和 Android）进行预声明
- 在 Azure Active Directory 或企业移动性套件中注册为 Windows 10 企业版设备（仅限 Windows 10）
- 在设备“属性”中指定为“企业”

在 Intune 中，对于企业拥有的设备，设备记录的“所有权”列显示为“企业”。 可转到“设备” > “所有设备”进行查看。

## <a name="predeclare-a-device-with-imei-or-serial-number"></a>使用 IMEI 或序列号预声明设备

Intune 管理员可以创建和导入列有 IMEI 编号或序列号的逗号分隔值 (.csv) 文件。 Intune 将使用这些标示符来指定设备的所有权为公司。 可以声明所有支持平台的 IMEI 编号。 可以仅声明 iOS 和 Android 设备的序列号。 每个 IMEI 或序列号可以在列表中指定详细信息，以便用于管理。

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[了解如何查找 Apple 设备序列号](https://support.apple.com/HT204308)。<br>
[了解如何查找 Android 设备序列号](https://support.google.com/store/answer/3333000)。

## <a name="add-corporate-identifiers"></a>添加企业标识符
若要创建列表，请创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加 IMEI 或序列号，在右列添加详细信息。 仅可在单个 .csv 文件中导入一种类型的 ID、IMEI 或序列号。 详细信息限制为 128 个字符，且仅用于管理。 在设备上不显示详细信息。 当前限制为每个 .csv 文件 500 行。

**上传含序列号的 .csv 文件** - 创建两列不带标头的逗号分隔值 (.csv) 列表，并将列表限制为每个 .csv 文件 5,000 台设备或 5 MB。

|||
|-|-|
|&lt;ID #1&gt;|&lt;Device #1 Details&gt;|
|&lt;ID #2&gt;|&lt;Device #2 Details&gt;|

在文本编辑器中查看该 .csv 文件时，该文件显示为：

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> 某些 Android 设备具有多个 IMEI 号码。 对于每个已注册的设备，Intune 仅读取一个 IMEI 号码。 如果导入一个 IMEI 号码，但它与 Intune 列出的 IMEI 不符的情况下，就会将设备归类为个人设备，而非公司拥有的设备。 如果为设备导入多个 IMEI 号码，则未列出号码的注册状态将显示为“未知”。<br>
>另请注意：Android 序列号不确保存在或是唯一的。 请与你的设备提供商核实，以明确序列号是否是可信的设备 ID。
>设备向 Intune 报告的序列号可能与设备的“Android 设置/关于”菜单中显示的 ID 不一致。 请验证设备制造商报告的序列号的类型。

### <a name="add-a-csv-list-of-corporate-identifiers"></a>添加企业标识符 .csv 列表

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “公司设备标识符”，然后单击“添加”。

 ![企业设备标识符工作区的屏幕截图，其中突出显示了“添加”按钮。](./media/add-corp-id.png)

2. 在“添加标识符”边栏选项卡中，指定标识符类型：IMEI 或“序列号”。 你可以指定先前导入的号码是否应“覆盖现有标识符的详细信息”。

3. 单击文件夹图标并指定要导入的列表的路径。 导航到 .csv 文件，然后选择“添加”。 可单击“刷新”，查看新的设备标识符。

导入设备不一定必须进行注册。 设备状态可以是“已注册”或“未连接”。 “未连接”表示该设备没有与 Intune 服务通信。

## <a name="delete-corporate-identifiers"></a>删除企业标识符

1. 在 Azure 门户中的 Intune 中，选择“设备注册” > “公司设备标识符”。
2. 选择要删除的设备标识符，然后选择“删除”。
3. 确认删除。

删除已注册设备的企业标识符不会更改设备的所有权。 若要更改设备的所有权，请转到“设备” > “所有设备”，选择设备，选择“属性”，然后更改“设备所有权”。

## <a name="imei-specifications"></a>IMEI 规格
有关国际移动设备识别号的详细规范，请参阅 [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。
