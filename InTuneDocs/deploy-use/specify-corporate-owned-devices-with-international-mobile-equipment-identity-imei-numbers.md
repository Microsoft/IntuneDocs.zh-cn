---
title: "指定 IMEI 号码 | Microsoft Docs"
description: "Microsoft Intune 使管理员可以为移动设备平台导入 IMEI 号码，以帮助识别公司拥有的移动设备"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: fbc9e94d3fc5dc7e69f5d59ca1d52493b2beefc3
ms.openlocfilehash: 5fa3c62553403dfafd182a691f611ba12a2d729c


---

# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 让管理员可以使用 IMEI 号码导入移动设备平台的国际移动设备标识 (IMEI) 号码，以帮助识别公司拥有的移动设备。 在 Intune 中注册设备后，可以在“组” > “概述” > “所有设备”下看到已导入 IMEI 号码的设备。 “设备组”在“所有权”列中将已导入 IMEI 号码的设备列为“公司”。

1. 在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，选择“组”&gt;“所有设备”&gt;“所有企业预注册设备”&gt;“按 IMEI (所有平台)”，然后单击“添加设备...”。 可以通过两种方式添加设备：

    -   **上传含序列号的 .csv 文件** - 创建两列不带标头的逗号分隔值 (.csv) 列表，并将列表限制为每个 .csv 文件 5,000 台设备或 5 MB。

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Device #1 Details&gt;|
        |&lt;IMEI #2&gt;|&lt;Device #2 Details&gt;|
        在文本编辑器中查看该 .csv 文件时，该文件显示为：

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **手动添加设备详细信息** - 输入最多 15 台设备的 IMEI 号码和设备详细信息。

   “详细信息”字段供管理使用。 可指定详细信息以帮助识别按硬件 ID 列出的企业持有设备列表中的设备。 此信息不会发送到设备，但它会出现在 Intune 控制台中。

2.   选择**下一步**。
3.  在“查看设备”窗格中，可确认已导入的设备 IMEI 号码。 对于要再次导入的 IMEI 号码，还可以决定是否要覆盖“详细信息”。 可以取消选中“覆盖”复选框，以保留当前详细信息。 选择**完成**以导入 IMEI 号码。
4.  已导入的 IMEI 号码和说明会添加到“按 IMEI (所有平台)”列表中。

当具有 IMEI 号码的设备在 Intune 中注册后，通常当用户安装公司门户应用并完成注册过程时，设备会被标记为“公司拥有”，并在“IMEI 设备”组中显示为“已注册”。

>[!NOTE] 
> 组织随后迁移到新的 Azure 门户时，将看到此功能的更改。 在现有的 Intune 管理员控制台中，管理员可以从上传的 CSV 中获取相关详细信息，并覆盖各个硬件标识符的现有详细信息。 在新的 Azure 门户中，可以自动覆盖所有硬件标识符的详细信息，或忽略现有标识符的所有新详细信息。



<!--HONumber=Feb17_HO1-->


