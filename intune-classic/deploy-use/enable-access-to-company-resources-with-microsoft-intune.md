---
title: 启用对公司资源的访问
description: Wi-Fi、VPN 和电子邮件配置文件协同工作，以便帮助你的用户获得对所需文件和资源的访问权限。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5bfc02f5f10ce88b992d0ea250d7b36fdf3f66dc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31017302"
---
# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>使用 Microsoft Intune 启用对公司资源的访问

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune Wi-Fi、VPN 和电子邮件配置文件协同工作，以便帮助你的用户获得对完成其工作所需的文件和资源的访问权限，无论他们身在何处。 证书配置文件可帮助保护该访问。

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[Wi-Fi 配置文件](wi-fi-connections-in-microsoft-intune.md)和受支持的平台

将无线网络设置部署到你的用户。 这些设置便于你的用户连接到公司网络。
#### <a name="supported-platforms"></a>受支持的平台

|Windows 8.1 及更高版本|Windows Phone 8.1 及更高版本|iOS|Android|Samsung KNOX 标准版|
|---------------------|---------------------------|---|-------|------------|
|是（你可以导入 Windows Wi-Fi 配置文件。）|是（你可以配置 OMA-URI。） |是|是|是|

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[VPN 配置文件](vpn-connections-in-microsoft-intune.md)和受支持的平台
将虚拟专用网 (VPN) 设置部署到你的用户。 这些设置便于用户连接到公司网络上的资源。

|Windows 8.1 及更高版本|Windows Phone 8.1 及更高版本|iOS|Android|Samsung KNOX 标准版|
|---------------------|---------------------------|---|-------|------------|
|是|是|是|是|是|

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[电子邮件配置文件](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)和受支持的平台
创建、部署和监视你的组织中的设备上的本机电子邮件设置。


| Windows 8.1 及更高版本 | Windows Phone 8.1 及更高版本 | iOS | Android | Samsung KNOX 标准版 |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          否           |             是             | 是 |   否    |          是          |

> [!NOTE]
> [这篇 Intune 团队博客文章](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/)提供有关如何使用 OMA-URI 配置 Windows Phone 8.1 Wi-Fi 配置文件的信息。

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[证书配置文件](secure-resource-access-with-certificate-profiles.md)和受支持的平台
有助于安全访问公司资源（包括无线网络和 VPN 连接）。


| Windows 8.1 及更高版本 | Windows Phone 8.1 及更高版本 | iOS | Android | Samsung KNOX 标准版 |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          是          |             是             | 是 |   是   |          是          |

