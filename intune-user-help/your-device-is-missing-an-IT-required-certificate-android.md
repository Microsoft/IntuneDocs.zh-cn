---
title: 设备缺少证书 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25ec84946aec9562aedce12b4199269f8de06f76
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72500015"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>安装组织所需证书丢失  

如果设备未在 Intune 中注册，并且缺少所需的证书，你将无法登录到公司门户应用。 在尝试登录时，你将看到以下消息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

可以通过两种方法来下载所需的证书并注册设备。 

- 在公司门户应用中启用浏览器访问。
- 在公司或学校的电脑上标识缺少的证书。 然后搜索 internet 下载缺少的证书。 

完成启用浏览器访问的步骤。 此后，如果仍无法注册设备，请按照步骤在 internet 上查找证书。 

## <a name="enable-browser-access"></a>启用浏览器访问
完成以下步骤以启用浏览器访问。 启用访问权限后，公司门户将安装相应的证书并继续注册。    

1. 在公司门户应用中，将鼠标移到右侧角并选择菜单。  
2. 选择“设置”  。  
3. 在 "**启用浏览器访问**" 旁边，选择 "**启用**"。  
4. 在 "设备管理员" 屏幕上，选择 "**激活**"。 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>通过 web 搜索标识并下载缺少的证书
完成这些步骤以在你的设备上手动标识并安装证书。  

1. 在电脑上，打开 Internet Explorer。 如果没有用于此目的的电脑，请与公司支持人员联系。 若要查找公司支持人员的联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。

2. 转到[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)，并使用你的工作或学校凭据登录。

3. 在浏览器地址栏的最右侧，选择类似于挂锁的符号，如下面的屏幕截图所示。

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    如果未看到挂锁符号，请停止操作并与公司支持人员联系。 锁意味着你已安全登录，所以在没有看到该符号前请不要继续进行操作。

4. 选择“查看证书”  。

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. 选择“证书路径”选项卡，然后标识需要从 Internet 获取的证书  。 所需证书的名称将显示在与上一示例屏幕截图中突出显示的位置相同的位置上。

6. 使用搜索引擎（如必应或 Google），搜索你在之前部分标识的所缺少证书的名称。 该证书可能以不同的扩展名结尾，如“.crt”或“.pem”等。

7. 从网站下载根证书。

8. 证书下载后，从你的设备顶部向下拖动以打开你的通知，然后在通知列表中点击证书的名称。

4. 在如下面的屏幕截图中所示的“命名证书”  对话框中，接受默认的证书名称。

5. 确保**凭据使用**设置为**用于 VPN 和应用**，然后点击**确定**。

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 关闭公司门户应用。

7. 重新打开公司门户应用。 现在应能够登录到公司门户应用。 如需帮助，请与公司支持人员联系。

如果看到相同的“缺少证书”消息（如之前所示），且已经按照步骤执行了操作，说明可能存在另一个需要公司支持人员帮助你安装的证书。 请使用[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)上提供的联系信息，联系公司支持人员获取帮助。

## <a name="next-steps"></a>后续步骤  

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
