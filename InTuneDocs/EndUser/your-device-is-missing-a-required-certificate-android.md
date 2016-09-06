---
title: "你的设备缺少必需的证书 | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3a2daebdb781ce99aa103e7717ffa1b0297cb3a
ms.openlocfilehash: e10de556babc49d4e2f1ebf6ba9c766291d58efd


---


# 你的设备缺少必需的证书


## 你的设备缺少通常安装在电话上的证书
如果你的 Android 设备未在 Intune 中注册，并且它缺少通常安装在电话上的证书，你将无法登录到 Android 公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

若要解决此问题并获取所需的证书：

1.  在浏览器中，导航到此 [Digicert 证书页](https://www.digicert.com/digicert-root-certificates.htm)。

2.  查找并下载 Baltimore CyberTrust 根证书 (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  从顶部向下拖动以打开你的通知，并在通知列表中点击 **BaltimoreCyberTrustRoot.crt**。

4.  在 **命名证书** 对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

6. 关闭 Web 浏览器和公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果需要帮助，请与你的 IT 管理员联系。

## 你的设备缺少 IT 管理员所需的证书
如果你的 Android 设备未在 Intune 中注册，并且它缺少 IT 管理员所需的特定证书，你将无法登录到 Android 公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

>[!NOTE]
> 如果你已经看到一条“缺少证书”的消息，请按照[你的设备缺少通常安装在电话上的证书](#your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone)的步骤执行操作即可。 它与此消息和证书不同，所以继续并按照本部分的步骤进行操作以获取缺少的证书。

若要解决此问题并获取所需的证书，需要执行两个主要步骤：

- 通过查看公司或学校的电脑来标识缺少的证书。
- 使用你的设备从 Internet 下载缺少的证书。

### 通过查看公司或学校的电脑来标识缺少的证书

1. 在电脑上，打开 Internet Explorer。 如果你没有用于此目的的电脑，请与你的 IT 管理员联系。 有关你的 IT 管理员的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

2. 转到[公司门户网站](http://portal.manage.microsoft.com)，并使用你的工作或学校凭据登录。

3. 在浏览器地址栏的最右侧，单击类似于挂锁的符号，如下所示。 如果你未看到挂锁符号，请停止操作并与你的 IT 管理员取得联系。 锁意味着你已安全登录，所以在没有看到该符号前请不要继续进行操作。

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

4. 单击“**查看证书**”。

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. 在“**证书**”对话框中，单击“**证书路径**”选项卡，然后标识你需要从 Internet 获取的证书。 你需要的证书的名称将显示在与上面的示例屏幕截图中突出显示的位置相同的位置上。

### 在你的 Android 移动设备上下载并安装缺少的证书。

1. 使用搜索引擎（如必应或 Google），搜索你在之前部分标识的所缺少证书的名称。 该证书可能以不同的扩展名结尾，如“.crt”或“.pem”等。

2. 从网站下载根证书。

3. 证书下载后，从你的设备顶部向下拖动以打开你的通知，然后在通知列表中点击证书的名称。

4. 在如下所示的“**命名证书**”对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 关闭公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果需要帮助，请与你的 IT 管理员联系。

如果你看到相同的“缺少证书”消息（如上所示），且你已经按照上面的步骤执行了操作，这可能意味着还有另一个证书需要你的 IT 管理员帮助你安装。 与你的 IT 管理员取得联系并向他提供该[链接](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含有助于解决此问题的步骤。

### 另请参阅
[通过 Intune 使用 Windows 设备](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO4-->


