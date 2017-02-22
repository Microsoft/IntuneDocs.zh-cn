---
title: "将 IMEI 标识符添加到 Intune | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何将企业标识符（IMEI 号码）添加到 Microsoft Intune。 "
keywords: 
author: staciebarker
ms.author: stabark
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: e134a6e3ff143dacce1d70ef0ab44ade0722ed57

---

# <a name="add-corporate-identifiers"></a>添加企业标识符

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可以创建国际移动设备标识 (IMEI) 号码列表来标识你的公司设备。 这些设备可能已/未注册，其状态为“已注册”或“未连接”。 “未连接”表示该设备不会签入 Intune 服务。

若要创建列表，请创建没有标题的两列逗号分隔值 (.csv) 列表。 在左列添加 IMEI 标识符，在右列添加详细信息。 目前，该列表的最大长度为 500 行。

在文本编辑器中，该 .csv 列表可能如下所示：

01 234567 890123, 设备详细信息</br>
02 234567 890123, 设备详细信息

**添加企业标识符 .csv 列表**

1. 在 Azure 门户中，选择“更多服务”，在文本框中输入“Intune”，然后选择“其他” > “Intune”。

2. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“企业设备标识符”。

3. 若要导入包含新详细信息（将覆盖现有信息）的文件，请选择“覆盖现有标识符详细信息”以将现有详细信息替换为新的详细信息。

4. 导航到 IMEI CSV 文件，然后选择“添加”。

**删除企业标识符 .csv 列表**

1. 在 Intune 边栏选项卡上，选择“注册设备”，然后选择“企业设备标识符”。

2. 选择“删除”。



<!--HONumber=Feb17_HO1-->


