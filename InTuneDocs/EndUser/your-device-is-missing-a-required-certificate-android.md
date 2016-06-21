---
# required metadata

title: 你的设备缺少必需的证书 | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/05/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 你的设备缺少必需的证书
如果你的 Android 设备未在 Intune 中注册，并且它缺少通常安装在电话上的证书，你将无法登录到 Android 公司门户应用。 在尝试登录时，你将看到以下消息：

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

若要解决此问题并获取所需的证书：

1.  在浏览器中，导航到此 [Digicert 证书页](https://www.digicert.com/digicert-root-certificates.htm)。

2.  查找并下载 Baltimore CyberTrust 根证书 (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  从顶部向下拖动以打开你的通知，并在通知列表中点击 **BaltimoreCyberTrustRoot.crt**。

4.  在 **命名证书** 对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. 关闭 Web 浏览器和公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果需要帮助，请与你的 IT 管理员联系。

如需帮助，并且找不到 IT 管理员的联系信息，请查看在[公司门户网站](http://portal.manage.microsoft.com)中是否已经列出。

<!--HONumber=Jun16_HO1-->


