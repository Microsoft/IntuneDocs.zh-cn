---
# required metadata

title: 设置 iOS 和 Mac 管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 设置 iOS 和 Mac 设备管理
利用 Microsoft Intune，可以为 iOS 和 Mac OS X 设备注册启用 BYOD（“自带设备办公”），以允许 iPhone、iPad 和 Mac 用户访问公司电子邮件和应用。 启用后，用户可以安装 Intune 公司门户应用并可以使用 Intune 管理控制台向其设备应用策略。

在可以使用 Intune 管理 iOS 设备之前，设备必须能够与 Intune 通信。 Apple 要求通过导入 Apple Push Notification 服务 (APNs) 证书与 Intune 建立信任关系。

1.  **设置 Intune**<br>
    如果你尚未设置，请通过[将移动设备管理机构设置](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2.  **获取证书签名请求**<br>
    以管理用户身份，打开 [Microsoft Intune 管理控制台](http://manage.microsoft.com)，转到**管理**&gt;**移动设备管理**&gt;**iOS 和 Mac OS X**&gt;**上载 APNs 证书**，并单击**下载 APNs证书请求**。 本地保存证书签名请求 (.csr) 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。

    ![上传 APNs 证书对话框](../media/Intune-iOS-enrollment-with-apns.png)

3.  **获取 Apple Push Notification 服务证书**<br>
    转到 [Apple 推送证书门户](http://go.microsoft.com/fwlink/?LinkId=269844) ，并使用你的公司 Apple ID 通过 .csr 文件创建 APN 证书。 单击 Apple 推送证书门户上的“上传”后，你将收到不能用于 APNs 的 .json 文件。 完成下载并返回到**第三方服务器的证书**的 Apple 推送证书门户上，然后单击**下载**。

    下载 APN (.pem)证书并在本地保存文件。 若要续订 APN 证书，必须在将来使用此 Apple ID。

4.  **将 APNs 证书添加到 Intune**<br>
    在 [Microsoft Intune 管理控制台](http://manage.microsoft.com)中，转到**管理**&gt;**移动设备管理**&gt;**iOS 和 Mac OS X**&gt;**上载 APNs 证书**，并单击**上载 APNs 证书**。 **“浏览”** 到证书(.pem)文件，单击 **“打开”** ，然后输入你的 **“Apple ID”**。 使用 APN 证书，Intune 可通过将策略推送到注册的移动设备注册并管理 iOS 设备。

5.  **告知用户如何通过公司门户访问公司资源**<br>
    你的用户将需要了解注册其设备的方式以及他们纳入管理之后会出现的情况。 [最终用户需要了解的有关 Microsoft Intune 使用的内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)

如果公司或组织为用户购买了 iOS 设备，可以将这些设备注册为[公司拥有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)，以便进行管理。

### 另请参阅
[为在 Microsoft Intune 中注册设备做好准备](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO4-->


