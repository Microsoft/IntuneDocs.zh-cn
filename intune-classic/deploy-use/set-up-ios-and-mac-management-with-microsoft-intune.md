---
title: Set up iOS and Mac management
description: 使用 Microsoft Intune 为 iOS 设备（包括 iPad 和 iPhone）以及 Mac OS X 设备启用移动设备管理 (MDM)。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 280efe7e7a5a1616ebab9abce7b7a5d78e321e7c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-ios-and-mac-device-management"></a>设置 iOS 和 Mac 设备管理

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 启用了 iPad、iPhone 和 macOS 设备的移动设备管理 (MDM)，并允许用户访问公司电子邮件和应用。 必须拥有 Apple 推送通知服务 (APNs) 证书，才能使用 Intune 管理 iOS 和 Mac 设备。 在将证书添加到 Intune 后，用户就可以安装公司门户应用来注册其设备，或者管理员可以设置[企业自有的 iOS 设备管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

1.  **设置 Intune**<br>
    如果你尚未设置，请通过[将移动设备管理机构设置](prerequisites-for-enrollment.md#step-2-set-mdm-authority)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2.  **获取证书签名请求**<br>
    以管理用户身份，打开 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，转到“管理”&gt;“移动设备管理”&gt;“iOS 和 Mac OS X”&gt;“上传 APNs 证书”，然后选择“上传 APNs 证书请求”。 本地保存证书签名请求 (.csr) 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。

    ![上传 APNs 证书对话框](../media/Intune-iOS-enrollment-with-apns.png)

3.  **获取 Apple 推送通知服务证书**<br>
    转到 [Apple Push Certificates 门户](http://go.microsoft.com/fwlink/?LinkId=269844)，并使用公司 Apple ID 登录以使用 .csr 文件创建 APNs 证书。 在 Apple Push Certificates 门户上选择“上传”后，将收到不能用于 APNs 的 .json 文件。 完成下载后，返回到“第三方服务器的证书”的 Apple Push Certificates 门户，然后选择“下载”。

    下载 APNs (.pem) 证书并本地保存文件。

    > [!NOTE]
    > 每年都需要续订（不是替换）此 APNs 证书。 使用此相同的 Apple ID 登录到 Apple 推送证书门户来续订证书，然后按照本主题中相同的说明下载该证书，并将其上传到 Intune。

4.  **将 APNs 证书添加到 Intune**<br>
    在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，转到“管理”&gt;“移动设备管理”&gt;“iOS 和 Mac OS X”&gt;“上传 APNs 证书”，然后选择“上传 APNs 证书”。 转到证书 (.pem) 文件，选择“打开”，然后输入“Apple ID”。 使用 APN 证书，Intune 可通过将策略推送到注册的移动设备注册并管理 iOS 设备。

5.  **告诉用户如何注册其设备以获取对公司资源的访问权限。**

    有关最终用户注册说明，请参阅[在 Intune 中注册 iOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)和[在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)。 注册过程会告知用户将出现的情况，以及 IT 管理员在其设备上可以看到和不能看到的内容。

    有关其他最终用户任务的信息，请参阅以下文章：
    - [有关 Microsoft Intune 最终用户体验的资源](/intune/end-user-educate)
    - [适用于 iOS 和 Mac 设备的最终用户指南](https://docs.microsoft.com/intune-user-help/using-your-ios-or-macOS-device-with-intune)

如果公司或组织为用户购买了 iOS 设备，也可以将这些设备注册为[公司拥有的 iOS 设备](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)，以便进行管理。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册的先决条件](prerequisites-for-enrollment.md)
