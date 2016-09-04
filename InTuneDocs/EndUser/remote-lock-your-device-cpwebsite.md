---
title: "从公司门户网站远程锁定设备 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3a2daebdb781ce99aa103e7717ffa1b0297cb3a
ms.openlocfilehash: 19369b8914eee60eececd3e749eae12891cd1a2e


---


# 从公司门户网站远程锁定设备

如果设备已丢失或被盗，则可以通过使用[公司门户网站](http://portal.manage.microsoft.com)上的“远程锁定”选项锁定该设备。 “远程锁定”适用于以下几种设备：

平台  |支持详细信息  
---------|---------
Android | 支持       
iOS | 支持
Windows 10 移动版 | 仅在手机设置了密码时支持     
Windows 10 桌面版 | 不支持  
Windows Phone 8.1 | 仅在手机设置了密码时支持
Windows Phone 8。0 | 不支持
电脑（Windows 8.0 及更早版本） | 不支持       
电脑 (Windows 8.1) | 不支持

</br>
使用“远程锁定”锁定你的设备：

1.  在[公司门户网站](http://portal.manage.microsoft.com)中，点击要锁定设备的名称。

2.  点击**远程锁定**。

    ![remote-lock-option-on-company-portal-website](./media/iwp-screen-with-all-options.png)

3.  阅读警告消息，指示将锁定你的设备，然后点击“**远程锁定**”使公司门户网站尝试锁定你的设备。

    一旦点击“远程锁定”，将出现“远程锁定挂起”状态。  “远程锁定”成功后，状态将更改为“远程锁定成功”。

    该“远程锁定”状态将在以下三个位置中显示：

    * 网站的通知区域。
    * 设备的“详细信息”页。
    * 该页上“我的设备”部分显示设备名称的磁贴。

    如果看到“远程锁定失败”的通知，请等待几分钟，然后再次尝试锁定设备。 一旦点击重试，状态将变回“远程锁定挂起”。

    如果重试不起作用，请联系你的 IT 管理员以获取帮助。 如果使用“远程锁定”后找到了设备并希望对其进行解锁，则只需输入你的密码。

仍需要帮助？ 请与你的 IT 管理员联系。 有关他们的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

### 另请参阅
[使用 Intune 公司门户网站](using-the-intune-company-portal-website.md)



<!--HONumber=Aug16_HO4-->


