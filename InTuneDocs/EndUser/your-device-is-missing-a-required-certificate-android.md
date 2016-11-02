---
title: "你的设备缺少必需的证书 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 016449720f6e77b8862fcaa232d252eefa8b20b3
ms.openlocfilehash: 27b3e3d4aefade368d900df95454c3d02e37bed4


---


# <a name="your-device-is-missing-a-required-certificate"></a>你的设备缺少必需的证书


## <a name="your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>你的设备缺少通常安装在电话上的证书
如果你的 Android 设备未在 Intune 中注册，并且它缺少通常安装在电话上的证书，你将无法登录到 Android 公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

解决此问题并获取所需证书：

1.  在浏览器中，转到此 [Digicert 证书页](https://www.digicert.com/digicert-root-certificates.htm)。

2.  查找并下载 Baltimore CyberTrust 根证书 (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  从顶部向下拖动以打开你的通知，并在通知列表中点击 **BaltimoreCyberTrustRoot.crt**。

4.  在“命名证书”对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

6. 关闭 Web 浏览器和公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果需要帮助，请与 IT 管理员联系。

## <a name="your-device-is-missing-a-certificate-required-by-your-it-admin"></a>设备缺少 IT 管理员所需的证书
如果 Android 设备未在 Intune 中注册，并且缺少 IT 管理员所需的特定证书，则无法登录到 Android 公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

>[!NOTE]
> 如果已经看到一条“缺少证书”的消息，请按照[设备缺少通常安装在手机上的证书](#your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone)中的步骤执行操作。 它与此消息和证书不同，所以继续并按照本部分的步骤进行操作以获取缺少的证书。

若要解决此问题并获取所需的证书，需要执行两个主要步骤：

- 通过查看公司或学校的电脑来标识缺少的证书。
- 使用你的设备从 Internet 下载缺少的证书。

### <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>通过查看公司或学校的电脑来标识缺少的证书

1. 在电脑上，打开 Internet Explorer。 如果没有用于此目的的电脑，请与 IT 管理员联系。 若要查找 IT 管理员的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

2. 转到[公司门户网站](http://portal.manage.microsoft.com)，并使用你的工作或学校凭据登录。

3. 在浏览器地址栏的最右侧，选择类似于挂锁的符号，如下面的屏幕截图所示。

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    如果未看到挂锁符号，请停止操作并与 IT 管理员联系。 锁意味着你已安全登录，所以在没有看到该符号前请不要继续进行操作。

4. 选择“查看证书”。

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. 在“证书”对话框中，选择“证书路径”选项卡，然后标识需要从 Internet 获取的证书。 所需证书的名称将显示在与上一示例屏幕截图中突出显示的位置相同的位置上。

### <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>在你的 Android 移动设备上下载并安装缺少的证书。

1. 使用搜索引擎（如必应或 Google），搜索你在之前部分标识的所缺少证书的名称。 该证书可能以不同的扩展名结尾，如“.crt”或“.pem”等。

2. 从网站下载根证书。

3. 证书下载后，从你的设备顶部向下拖动以打开你的通知，然后在通知列表中点击证书的名称。

4. 在如下面的屏幕截图中所示的“命名证书”对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 关闭公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如果需要帮助，请与 IT 管理员联系。

如果看到相同的“缺少证书”消息（如之前所示），且已经按照步骤执行了操作，说明可能存在另一个需要 IT 管理员帮助你安装的证书。 与 IT 管理员联系并向其发送此 [Android 证书问题](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)的链接，其中包含帮助解决此问题的步骤。



<!--HONumber=Oct16_HO2-->


