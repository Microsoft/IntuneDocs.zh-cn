---
# required metadata

title: 根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 根据国际移动设备标识 (IMEI) 号码指定公司拥有的设备
Microsoft Intune 让管理员可以导入具有 IMEI 号码的移动设备平台的国际移动设备标识 (IMEI) 号码，以帮助指定公司拥有的移动设备。 在 Intune 中注册后，带有导入的 IMEI 号码的设备就会被标记为公司，这些设备的应用策略与个人拥有的设备的应用策略不同。

1. 在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到“组” &gt; “所有设备” &gt; “所有企业预注册设备” &gt; “按 IMEI (所有平台)”，然后单击“添加设备...”。 可以通过两种方式添加设备：

    -   “上传包含序列号的 CSV 文件” - 创建不带标头的两列的逗号分隔值 (.csv) 列表，每个 csv 文件限 5000 台设备或 5 MB。

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Device #1 Details&gt;|
        |&lt;IMEI #2&gt;|&lt;设备 #2 详细信息&gt;|
        在文本编辑器中查看该 .csv 文件时，该文件显示为：

        ```
        AA-BBBBBB-CCCCCC-D,PO 1234
        AA-BBBBBB-CCCCCC-E,PO 1234
        ```

    -   **手动添加设备详细信息** - 输入最多五台设备的 IMEI 号码和设备详细信息

   *详细信息*用于管理，可以识别与设备关联的 IMEI 号码。 此信息不会发送给设备，但会出现在 Intune 控制台中。

2.   单击“下一步”
3.  在“查看设备”窗格中，可以确认导入哪些设备 IMEI 号码。 对于重新导入的 IMEI 号码，还可以决定是否要覆盖“详细信息”。 可以取消选中“覆盖”复选框以保留当前详细信息。 单击“完成”以导入 IMEI 号码。
4.  添加的 IMEI 号码和说明会添加到“按 IMEI（所有平台）”列表。

带有该 IMEI 号码的设备注册后，通常当用户安装公司门户应用并完成注册过程时，设备会被标记为公司拥有，并在“IMEI 设备”组中显示为已注册。


<!--HONumber=May16_HO2-->


