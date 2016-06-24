---
# required metadata

title: 使用 Microsoft Intune 续订 Symantec 企业代码签名证书 |Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 续订用于 Windows 设备的 Symantec 企业代码签名证书

用于管理某些 Windows 和 Windows Phone 移动设备的 Symantec 证书必须定期续订。 对于 Windows Phone 8.0 设备，设备注册需要已签名公司门户应用和代码签名证书。 更高版本的 Windows Phone 设备可以使用从应用商店下载的公司门户应用。 部署业务线应用也需要代码签名证书。

## 如何续订 Symantec 企业代码签名证书

1.  大约在证书到期前 14 天查找发自 Symantec 的续订电子邮件。 电子邮件包括 Symantec 有关续订你的企业证书的说明。

    有关 Symantec 证书的其他信息，请访问 [www.symantec.com](http://www.symantec.com) 或致电 1-877-438-8776 或 1-650-426-3400。

2.  转到网站（例如： [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)），并使用 Symantec 发布者 ID 和与证书关联的电子邮件地址登录。 记住，请使用你将用于下载证书的同一计算机开始续订。

3.  续订获批并支付后，下载该证书。

## 如何为 Windows Phone 8.0 安装更新的证书

1.  在此处下载最新的 Windows Phone 公司门户，并对其进行签名：[http://www.microsoft.com/zh-cn/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)

2.  打开你的 Intune 管理控制台 ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) 并转到“管理”、“移动设备管理” &gt; “Windows Phone”，然后单击“上载已签名的应用”

3.  上载已签名的新公司门户。 你将需要新签名的 SSP.xap 文件和你从 Symantec 收到的新 .PFX 文件，或使用此新 .PFX 文件创建的应用程序注册令牌。

4.  上载完成时，在 Intune 管理控制台中的 **“软件”** 工作区中删除旧版本的公司门户。

5.  再次使用相同证书对企业的所有业务线应用签名，并上传和替换现有应用程序。

提供签名的 SSP.xap 文件是当前提供更新的代码签名证书的唯一方法。 要支持签名的业务线应用，你必须对公司门户应用签名，并将其上载，即使你的用户将从应用商店安装公司门户应用。

## 如何为 Windows Phone 8.1 和更高版本设备安装更新的证书

1.  从下载中心下载最新的 Windows Phone 公司门户，并对其进行签名：[http://www.microsoft.com/zh-cn/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)

2.  打开你的 [Intune 管理控制台](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) 并转到“管理” &gt; “移动设备管理” &gt; “Windows Phone”，然后单击“上载已签名的应用”

3.  上载已签名的新公司门户。 你将需要新签名的 SSP.xap 文件和你从 Symantec 收到的新 .PFX 文件，或使用此新 .PFX 文件创建的应用程序注册令牌。

4.  上载完成时，在 **“软件”**  工作区中删除旧版本的公司门户。

5.  使用新证书对所有新的和任何更新的企业业务线应用签名。 现有应用程序不需要重新签名和重新部署。


### 另请参阅
设置 Windows Phone 8.0 管理


<!--HONumber=May16_HO2-->


