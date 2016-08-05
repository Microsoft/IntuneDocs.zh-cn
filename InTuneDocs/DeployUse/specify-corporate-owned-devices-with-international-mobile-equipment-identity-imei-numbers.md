---
title: "指定 IMEI 号码 | Microsoft Intune"
description: "Microsoft Intune 可让管理员为移动设备平台导入 IMEI 号码以帮助识别公司自有的移动设备"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 4e2092182dbda4523c19afeabc34aa0166962c40


---

# 根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备
Microsoft Intune 让管理员可以导入具有 IMEI 号码的移动设备平台的国际移动设备标识 (IMEI) 号码，以帮助指定公司拥有的移动设备。 在 Intune 中注册后，可以在“**组** > **概述** > **所有设备**”下查看导入了 IMEI 号码的设备。 “**设备组**”列表在“**所有权**”列中显示导入的 IMEI 号码为“**公司**”的设备。

1. 在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，选择**组**&gt;**所有设备**&gt;**所有企业预注册设备**&gt;**按 IMEI (所有平台)**，然后单击**添加设备...**。 可以通过两种方式添加设备：

    -   “上传包含序列号的 CSV 文件” - 创建不带标头的两列的逗号分隔值 (.csv) 列表，每个 csv 文件限 5000 台设备或 5 MB。

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Device #1 Details&gt;|
        |&lt;IMEI #2&gt;|&lt;设备 #2 详细信息&gt;|
        在文本编辑器中查看该 .csv 文件时，该文件显示为：

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **手动添加设备详细信息** - 输入最多五台设备的 IMEI 号码和设备详细信息

   *详细信息*用于管理，可以识别与设备关联的 IMEI 号码。 此信息不会发送给设备，但会出现在 Intune 控制台中。

2.   选择**下一步**。
3.  在“查看设备”窗格中，可以确认导入哪些设备 IMEI 号码。 对于重新导入的 IMEI 号码，还可以决定是否要覆盖“详细信息”。 可以取消选中“覆盖”复选框以保留当前详细信息。 选择**完成**以导入 IMEI 号码。
4.  添加的 IMEI 号码和说明会添加到“按 IMEI（所有平台）”列表。

带有该 IMEI 号码的设备注册后，通常当用户安装公司门户应用并完成注册过程时，设备会被标记为公司拥有，并在“IMEI 设备”组中显示为已注册。



<!--HONumber=Jul16_HO4-->


