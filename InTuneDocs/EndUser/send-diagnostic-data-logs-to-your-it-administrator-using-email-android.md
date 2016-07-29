---
title: "使用电子邮件将诊断数据日志发送给 IT 管理员 | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94
ROBOTS: noindex,nofollow
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 00e23b0094ee03c2a54bf6d12295e9f38781373f


---


# 使用电子邮件将诊断数据日志发送给 IT 管理员

如果在 Android 设备上使用学校或公司应用或在公司门户应用中操作时遇到错误，可以发送诊断数据日志来帮助 IT 管理员找出并修复该错误。 若要在日志中包含所有详细信息，以便让 IT 管理员更快找出问题，请打开“详细日志记录”。 可以在[详细日志记录](use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md)阅读有关此内容的更多信息。

启用详细日志记录：

1.  打开公司门户应用。

2.  点击**菜单** &gt; **设置**。

    > [!NOTE]
    > “菜单”可以是软件按钮，也可以是硬件按钮，具体取决于你拥有的 Android 设备类型。

3.  在“诊断数据”下，点击“发送数据”。

    > [!NOTE]
    > **如果你仅使用 Android 6.0 或更高版本的设备：**点击“发送数据”时，将显示消息“是否允许公司门户访问你设备上的照片、媒体和文件?”。

    此消息有误导性，因为**Microsoft 绝不会访问你设备上的照片、媒体或文件！** 消息文本由 Google 管控，Microsoft 无法更改。  允许访问就意味着允许你的设备将数据日志写入设备的 SD 卡中，这可使你通过使用 USB 电缆移动这些日志。

    如果拒绝访问，下次点击“发送数据”时将再次出现此消息，但是你可以点击“不再询问”复选框关闭以后接收此消息。  如果你稍后决定允许访问，请转到**设置** &gt; **应用** &gt; **公司门户** &gt; **权限** &gt; **存储**，然后开启权限。

4.  按照提示选择用于将日志发送给 IT 管理员的电子邮件应用。 该应用会创建预先填好地址的电子邮件，其中附加了所有日志。


### 另请参阅
[通过 Intune 使用 Android 设备](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


