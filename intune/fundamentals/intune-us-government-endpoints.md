---
title: 用于美国政府部署的网络终结点 - Microsoft Intune
titleSuffix: ''
description: 查看 Intune 的美国政府终结点。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfa93bb758447c872d172ded7706fd7507a42f11
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966277"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune 的美国政府终结点

此页列出了 Intune 部署中代理设置所需的美国政府终结点。

若要管理防火墙和代理服务器后面的设备，必须启用 Intune 的通信。

- 由于 Intune 客户端使用 **HTTP (80)** 和 **HTTPS (443)** ，因此代理服务器必须支持这两种协议
- 对于某些任务（例如下载软件更新），Intune 需要对 manage.microsoft.com 的未经身份验证的代理服务器访问权限

可以修改单个客户端计算机上的代理服务器设置。 还可以使用“组策略”设置来更改位于指定代理服务器后面的所有客户端计算机的设置。

托管的设备需要允许“所有用户”  通过防火墙访问服务的配置。

有关适用于美国政府客户的 Windows 10 自动注册和设备注册的详细信息，请参阅[设置 Windows 设备注册](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration)。

下表列出了 Intune 客户端访问的端口和服务：

|终结点 |**IP 地址**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>美国政府客户指定的终结点：
- Azure 门户：https:\//portal.azure.us/ 
- Office 365：https:\//portal.office365.us/ 
- Intune 公司门户：https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune 依赖的合作伙伴服务终结点:
- AAD Sync 服务：https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS：https:\//login.microsoftonline.us
- 目录代理：https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph：https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph：https:\//graph.microsoft.us
- ADRS：https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Windows 推送通知服务
在使用移动设备管理 (MDM) 管理的 Intune 托管设备上，设备操作和其他即时活动需要使用 Windows 推送通知服务 (WNS)。 有关详细信息，请参阅[支持 WNS 流量的企业防火墙和代理配置](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## <a name="apple-device-network-information"></a>Apple 设备网络信息

|**用途**|**主机名（IP 地址/子网）**|**协议**|**端口**|
|------------|-----------|------------|-----------|
|检索并显示 Apple 服务器的内容|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|与 APNS 服务器通信|#-courier.push.apple.com<br>“#”是 0 到 50 范围内的一个随机数字。|TCP|5223 和 443|
|各种功能，包括访问 Internet、iTunes 商店、macOS 应用商店、iCloud、消息等。|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 或 443|

有关详情，请参阅：

- [Apple 软件产品使用的 TCP 和 UDP 端口](https://support.apple.com/HT202944)
- [关于 macOS、iOS 和 iTunes 服务器主机连接和 iTunes 后台进程](https://support.apple.com/HT201999)
- [如果您的 macOS 和 iOS 客户端没有收到 Apple 推送通知](https://support.apple.com/HT203609)

## <a name="next-steps"></a>后续步骤
[Microsoft Intune 的网络终结点](intune-endpoints.md)

