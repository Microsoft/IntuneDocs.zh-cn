---
title: "设置 iOS 和 Mac 管理 | Microsoft Intune"
description: "使用 Microsoft Intune 为 iOS 设备（包括 iPad 和 iPhone）以及 Mac OS X 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 263fb9add8d30c0f98af46e46b566f15513db109


---

# 设置 iOS 和 Mac 设备管理
若要设置你的 iOS 或 Mac 设备，可在[此处](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)找到帮助。

Intune 启用了 iPad、iPhone 和 Mac OS X 设备的移动设备管理并允许用户访问公司电子邮件和应用。 必须拥有 Apple 推送通知服务 (APNs) 证书，才能使用 Intune 管理 iOS 和 Mac 设备。 一旦证书添加到 Intune，用户就可以安装公司门户应用来注册其设备或管理员可以设置[企业自有的 iOS 设备管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

1.  **设置 Intune**<br>
    如果你尚未设置，请通过[将移动设备管理机构设置](prerequisites-for-enrollment.md#set-mobile-device-management-authority)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2.  **获取证书签名请求**<br>
    以管理用户身份，打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转到**管理**&gt;**移动设备管理**&gt;**iOS 和 Mac OS X**&gt;**上载 APNs 证书**，并单击**下载 APNs证书请求**。 本地保存证书签名请求 (.csr) 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。

    ![上传 APNs 证书对话框](../media/Intune-iOS-enrollment-with-apns.png)

3.  **获取 Apple Push Notification 服务证书**<br>
    转到 [Apple 推送证书门户](http://go.microsoft.com/fwlink/?LinkId=269844) ，并使用你的公司 Apple ID 通过 .csr 文件创建 APN 证书。 单击 Apple 推送证书门户上的“上传”后，你将收到不能用于 APNs 的 .json 文件。 完成下载并返回到**第三方服务器的证书**的 Apple 推送证书门户上，然后单击**下载**。

    下载 APN (.pem)证书并在本地保存文件。 若要续订 APN 证书，必须在将来使用此 Apple ID。

4.  **将 APNs 证书添加到 Intune**<br>
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到**管理**&gt;**移动设备管理**&gt;**iOS 和 Mac OS X**&gt;**上载 APNs 证书**，并单击**上载 APNs 证书**。 **“浏览”** 到证书(.pem)文件，单击 **“打开”** ，然后输入你的 **“Apple ID”**。 使用 APN 证书，Intune 可通过将策略推送到注册的移动设备注册并管理 iOS 设备。

5.  **告知用户如何通过公司门户访问公司资源**<br>
    你的用户将需要了解注册其设备的方式以及他们纳入管理之后会出现的情况。
    - [最终用户需要了解的有关 Microsoft Intune 使用的内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [适用于 iOS 和 Mac 设备的最终用户指南](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

如果公司或组织为用户购买了 iOS 设备，可以将这些设备注册为[公司拥有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)，以便进行管理。

### 另请参阅
[在 Microsoft Intune 中注册的先决条件](prerequisites-for-enrollment.md)



<!--HONumber=Sep16_HO4-->


