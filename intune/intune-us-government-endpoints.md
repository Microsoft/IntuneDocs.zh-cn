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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4712c2958e2beee8853ad0d2620414d823da327
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804492"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Microsoft Intune 的美国政府终结点

此页列出了 Intune 部署中代理设置所需的美国政府终结点。

若要管理防火墙和代理服务器后面的设备，必须启用 Intune 的通信。

- 由于 Intune 客户端使用 **HTTP (80)** 和 **HTTPS (443)** ，因此代理服务器必须支持这两种协议
- 对于某些任务（例如下载软件更新），Intune 需要对 manage.microsoft.com 的未经身份验证的代理服务器访问权限

可以修改单个客户端计算机上的代理服务器设置。 还可以使用“组策略”设置来更改位于指定代理服务器后面的所有客户端计算机的设置。

托管的设备需要允许“所有用户”  通过防火墙访问服务的配置。

下表列出了 Intune 客户端访问的端口和服务：

|终结点 |**IP 地址**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>美国政府客户指定的终结点：
- Azure 门户： https://portal.azure.us/ 
- Office 365： https://portal.office365.us/ 
- Intune 公司门户： https://portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Intune 依赖的合作伙伴服务终结点:
- AAD Sync 服务： https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS： https://login.microsoftonline.us
- Directory Proxy： https://directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph： https://directory.microsoftazure.us 和 https://graph.microsoftazure.us
- MS Graph： https://graph.microsoft.us
- ADRS： https://enterpriseregistration.microsoftonline.us
