---
title: "设备缺少证书 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 52070573560b798044c929b0fa9476cf1f7bbf89
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2017
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>你的 Android 设备缺少通常随附安装在电话上的证书

如果设备未在 Intune 中注册，并且它缺少通常随附安装在电话上的证书，则无法登录到公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

可通过从 [Digicert 的证书页](https://www.digicert.com/digicert-root-certificates.htm)获取所需的证书来修复此问题。

1. 查找并下载 __Baltimore CyberTrust Root__ 证书。 也可以直接从[此处](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)下载。

2. 从顶部屏幕向下拖动以显示最近通知列表，并点击 **BaltimoreCyberTrustRoot.crt**。

3. 设备将要求你**命名证书**。 请勿更改显示的默认证书名称。

4. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. 关闭浏览器和公司门户应用。

6. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果仍然无法使用公司门户应用，请使用[公司门户网站](https://portal.manage.microsoft.com)上提供的信息，联系公司支持人员并获取进一步指示。

>[!NOTE]
> 如果安装此证书未解决问题，并且看到另一条“缺少证书”消息，则需要采取额外步骤来[安装缺少的证书](your-device-is-missing-an-IT-required-certificate-android.md)。

仍需要帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com)。
